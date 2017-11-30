## <a name="prerequisites"></a>Conditions préalables

Avant de créer le groupe de disponibilité, vous devez :

- Définissez votre environnement afin que tous les serveurs qui hébergeront les réplicas de disponibilité peuvent communiquer.
- Installez SQL Server.

>[!NOTE]
>Sur Linux, vous devez créer un groupe de disponibilité avant de vous ajoutez en tant que ressource de cluster pour être géré par le cluster. Ce document fournit un exemple qui crée le groupe de disponibilité. Pour obtenir des instructions spécifiques à la distribution créer le cluster et ajoutez le groupe de disponibilité en tant que ressource de cluster, consultez les liens sous « Étapes suivantes ».

1. Mettre à jour le nom d’ordinateur pour chaque hôte.

   Chaque nom de serveur SQL Server doit :
   
   - 15 caractères ou moins.
   - Unique au sein du réseau.
   
   Pour définir le nom de l’ordinateur, modifiez `/etc/hostname`. Le script suivant vous permet de modifier `/etc/hostname` avec `vi`:

   ```bash
   sudo vi /etc/hostname
   ```

2. Configurer le fichier hosts.

    >[!NOTE]
    >Si les noms d’hôte sont enregistrés avec leur adresse IP dans le serveur DNS, vous n’avez pas besoin de suivre les étapes ci-dessous. Vérifiez que tous les nœuds destinées à faire partie de la configuration de groupe de disponibilité peuvent communiquer avec eux. (Une commande ping sur le nom d’hôte doit répondre avec l’adresse IP correspondante.) En outre, assurez-vous que le fichier/etc/hosts ne contient pas un enregistrement qui mappe l’adresse IP de localhost 127.0.0.1 avec le nom d’hôte du nœud.
    >

   Le fichier hosts sur chaque serveur contient les adresses IP et les noms de tous les serveurs qui seront inclus dans le groupe de disponibilité. 

   La commande suivante retourne l’adresse IP du serveur actif :

   ```bash
   sudo ip addr show
   ```

   Mettez à jour `/etc/hosts`. Le script suivant vous permet de modifier `/etc/hosts` avec `vi`:

   ```bash
   sudo vi /etc/hosts
   ```

   L’exemple suivant montre `/etc/hosts` sur **node1** avec des ajouts pour **node1**, **node2** et **node3**. Dans ce document, **node1** fait référence au serveur qui héberge le réplica principal. Et **node2** et **node3** font référence à des serveurs qui hébergent les réplicas secondaires.

    ```
    127.0.0.1   localhost localhost4 localhost4.localdomain4
    ::1       localhost localhost6 localhost6.localdomain6
    10.128.18.12 node1
    10.128.16.77 node2
    10.128.15.33 node3
    ```

### <a name="install-sql-server"></a>Installer SQL Server

Installez SQL Server. Les liens suivants pointent vers les instructions d’installation de SQL Server pour différentes distributions : 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)
- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>Activer les groupes de disponibilité AlwaysOn et redémarrez mssql-serveur

Activer les groupes de disponibilité AlwaysOn sur chaque nœud qui héberge une instance de SQL Server. Puis redémarrez `mssql-server`. Exécutez le script suivant :

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-an-alwaysonhealth-event-session"></a>Activer une session d’événements AlwaysOn_health 

Vous pouvez éventuellement activer les événements étendus des groupes de disponibilité AlwaysOn aider les causes diagnostic lors de la résolution d’un groupe de disponibilité. Exécutez la commande suivante sur chaque instance de SQL Server : 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Pour plus d’informations sur cette session XE, consultez [AlwaysOn événements étendus](http://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-a-database-mirroring-endpoint-user"></a>Créer un utilisateur de point de terminaison de mise en miroir de base de données

Le script Transact-SQL suivant crée une connexion nommée `dbm_login` et un utilisateur nommé `dbm_user`. Mettez à jour le script avec un mot de passe fort. Pour créer la base de données utilisateur de point de terminaison de mise en miroir, exécutez la commande suivante sur toutes les instances de SQL Server :

```SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>Créer un certificat

Le service SQL Server sur Linux utilise des certificats pour authentifier les communications entre les points de terminaison de mise en miroir. 

Le script Transact-SQL suivant crée une clé principale et un certificat. Il sauvegarde le certificat et sécurise le fichier avec une clé privée. Mettez à jour le script avec des mots de passe forts. Se connecter à l’instance de SQL Server principal. Pour créer le certificat, exécutez le script Transact-SQL suivant :

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = '/var/opt/mssql/data/dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

À ce stade, votre réplica principal de SQL Server possède un certificat à `/var/opt/mssql/data/dbm_certificate.cer` et un at de clé privée `var/opt/mssql/data/dbm_certificate.pvk`. Copiez ces deux fichiers au même emplacement sur tous les serveurs qui hébergeront les réplicas de disponibilité. Utilisez l’utilisateur mssql ou accorder l’autorisation à l’utilisateur de mssql pour accéder à ces fichiers. 

Par exemple, sur le serveur source, la commande suivante copie les fichiers sur l’ordinateur cible. Remplacez le `**<node2>**` valeurs avec les noms des instances de SQL Server qui hébergeront les réplicas. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

Sur chaque serveur cible, accorder l’autorisation à l’utilisateur de mssql pour accéder au certificat.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Créer le certificat sur les serveurs secondaires

Le script Transact-SQL suivant crée une clé principale et un certificat à partir de la sauvegarde que vous avez créé sur le réplica principal de SQL Server. La commande autorise également l’utilisateur à accéder au certificat. Mettez à jour le script avec des mots de passe forts. Le mot de passe de déchiffrement est le même mot de passe que celui que vous avez utilisé pour créer le fichier .pvk à une étape précédente. Pour créer le certificat, exécutez le script suivant sur tous les serveurs secondaires :

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate   
    AUTHORIZATION dbm_user
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>Créer les points de terminaison de mise en miroir de bases de données sur tous les réplicas

Les points de terminaison de mise en miroir de base de données utilisent le protocole TCP (Transmission Control) pour envoyer et recevoir des messages entre les instances de serveur qui participent aux sessions de mise en miroir de base de données ou hébergeront des réplicas de disponibilité. Le point de terminaison de mise en miroir de bases de données écoute sur un numéro de port TCP unique. L’écouteur TCP requiert une adresse IP d’écouteur. L’adresse IP d’écouteur doit être une adresse IPv4. Vous pouvez également utiliser `0.0.0.0`. 

Le script Transact-SQL suivant crée un point de terminaison écoute nommé `Hadr_endpoint` pour le groupe de disponibilité. Il démarre le point de terminaison et autorise la connexion à l’utilisateur que vous avez créé. Avant d’exécuter le script, remplacez les valeurs entre `**< ... >**`.

Mettre à jour le script Transact-SQL suivant pour votre environnement sur toutes les instances de SQL Server : 

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

>[!NOTE]
>Si vous utilisez SQL Server Express Edition sur un nœud pour héberger un réplica de configuration uniquement, la seule valeur valide pour `ROLE` est `WITNESS`. Exécutez le script suivant dans SQL Server Express Edition :

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = WITNESS,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

Le port TCP sur le pare-feu doit être ouvert pour le port d’écoute.



>[!IMPORTANT]
>Pour la version de SQL Server 2017, est la seule méthode d’authentification pris en charge pour le point de terminaison de mise en miroir de base de données `CERTIFICATE`. Le `WINDOWS` option est activée dans une version ultérieure.

Pour plus d’informations, consultez [la base de données mise en miroir du point de terminaison (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).


