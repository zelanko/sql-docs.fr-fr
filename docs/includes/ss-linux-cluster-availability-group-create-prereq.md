## <a name="prerequisites"></a>Conditions préalables

Avant de créer le groupe de disponibilité, vous devez :

- Définir votre environnement de sorte que tous les serveurs qui hébergeront des réplicas de disponibilité puissent communiquer.
- Installer SQL Server

>[!NOTE]
>Sur Linux, vous devez créer un groupe de disponibilité avant de l’ajouter en tant que ressource de cluster à gérer par le cluster. Ce document fournit un exemple qui crée le groupe de disponibilité. Pour des instructions spécifiques à la distribution pour créer le cluster et ajouter le groupe de disponibilité en tant que ressource de cluster, consultez les liens sous [Étapes suivantes](#next-steps).

1. **Mettre à jour le nom de l’ordinateur pour chaque hôte**

   Chaque nom de serveur SQL Server doit :
   
   - Comporter 15 caractères ou moins
   - Être unique dans le réseau
   
   Pour définir le nom de l’ordinateur, modifiez `/etc/hostname`. Le script suivant vous permet de modifier `/etc/hostname` avec `vi`.

   ```bash
   sudo vi /etc/hostname
   ```

1. **Configurer le fichier hosts**

>[!NOTE]
>Si les noms d’hôte sont inscrits avec leur adresse IP dans le serveur DNS, il n’est pas nécessaire d’effectuer les étapes ci-dessous. Vérifiez que tous les nœuds destinés à faire partie de la configuration du groupe de disponibilité peuvent communiquer les uns avec les autres (un test ping vers le nom d’hôte doit normalement répondre avec l’adresse IP correspondante). Vérifiez aussi que ce fichier/etc/hosts ne contient pas un enregistrement qui mappe l’adresse IP 127.0.0.1 de localhost au nom d’hôte du nœud.


   Le fichier hosts sur chaque serveur contient les adresses IP et les noms de tous les serveurs qui seront inclus dans le groupe de disponibilité. 

   La commande suivante retourne l’adresse IP du serveur actif :

   ```bash
   sudo ip addr show
   ```

   Mettez à jour `/etc/hosts`. Le script suivant vous permet de modifier `/etc/hosts` avec `vi`.

   ```bash
   sudo vi /etc/hosts
   ```

   L’exemple suivant montre `/etc/hosts` sur **node1** avec des ajouts pour **node1**, **node2** et **node3**. Dans ce document **node1** fait référence au serveur qui héberge le réplica principal. **node2** et **node3** font référence aux serveurs qui hébergent des réplicas secondaires.


   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.12 node1
   10.128.16.77 node2
   10.128.15.33 node3
   ```

### <a name="install-sql-server"></a>Installer SQL Server

Installez SQL Server. Les liens suivants pointent vers les instructions d’installation de SQL Server pour différentes distributions. 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)

- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)

- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-always-on-availability-groups-and-restart-sqlserver"></a>Activer les groupes de disponibilité AlwaysOn et redémarrer SQL Server

Activez les groupes de disponibilité AlwaysOn sur chaque nœud hébergeant une instance de SQL Server puis redémarrez `mssql-server`.  Exécutez le script suivant :

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-alwaysonhealth-event-session"></a>Activer la session d’événements AlwaysOn_health 

Vous pouvez éventuellement activer les événements étendus des groupes de disponibilité Always On pour mieux diagnostiquer la cause principale quand vous résolvez les problèmes d’un groupe de disponibilité. Exécutez la commande suivante sur chaque instance de SQL Server. 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Pour plus d’informations sur cette session XE, consultez [Événements étendus d’AlwaysOn](http://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-db-mirroring-endpoint-user"></a>Créer un utilisateur de point de terminaison de mise en miroir de bases de données

Le script Transact-SQL suivant crée une connexion nommée `dbm_login` et un utilisateur nommé `dbm_user`. Mettez à jour le script avec un mot de passe fort. Exécutez la commande suivante sur toutes les instances de SQL Server pour créer l’utilisateur de point de terminaison de mise en miroir de bases de données.

```SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>Créer un certificat

Le service SQL Server sur Linux utilise des certificats pour authentifier les communications entre les points de terminaison de mise en miroir. 

Le script Transact-SQL suivant crée une clé principale et un certificat principal. Il sauvegarde ensuite le certificat et sécurise le fichier avec une clé privée. Mettez à jour le script avec des mots de passe forts. Connectez-vous à l’instance principale de SQL Server et exécutez la commande Transact-SQL suivante pour créer le certificat :

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

À ce stade votre réplica SQL Server principal a un certificat dans `/var/opt/mssql/data/dbm_certificate.cer` et une clé privée dans `var/opt/mssql/data/dbm_certificate.pvk`. Copiez ces deux fichiers au même emplacement sur tous les serveurs qui hébergeront les réplicas de disponibilité. Utilisez l’utilisateur mssql ou accordez à l’utilisateur mssql l’autorisation d’accéder à ces fichiers. 

Par exemple, sur le serveur source, la commande suivante copie les fichiers sur la machine cible. Remplacez les valeurs de  **<node2>** par les noms des instances de SQL Server qui hébergeront les réplicas. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

Sur chaque serveur cible, accordez à l’utilisateur mssql l’autorisation d’accéder au certificat.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Créer le certificat sur les serveurs secondaires

Le script Transact-SQL suivant crée une clé principale et un certificat principal à partir de la sauvegarde que vous avez créée sur le réplica principal de SQL Server. La commande autorise également l’utilisateur à accéder au certificat. Mettez à jour le script avec des mots de passe forts. Le mot de passe de déchiffrement est le même mot de passe que celui que vous avez utilisé pour créer le fichier .pvk à une étape précédente. Exécutez le script suivant sur tous les serveurs secondaires pour créer le certificat.

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

Les points de terminaison de mise en miroir de bases de données utilisent le protocole TCP (Transmission Control Protocol) pour l'envoi et la réception de messages entre les instances de serveur participant à des sessions de mise en miroir de bases de donnée ou hébergeant des réplicas de disponibilité. Le point de terminaison de mise en miroir de bases de données écoute sur un numéro de port TCP unique. L’écouteur TCP requiert une adresse IP d’écouteur. L’adresse IP d’écouteur doit être une adresse IPv4. Vous pouvez également utiliser `0.0.0.0`. 

L’instruction Transact-SQL suivante crée un point de terminaison d’écoute nommé `Hadr_endpoint` pour le groupe de disponibilité. Il démarre le point de terminaison et donne l’autorisation de connexion à l’utilisateur que vous avez créé. Avant d’exécuter le script, remplacez les valeurs entre `**< ... >**`.

Mise à jour de l’instruction Transact-SQL suivant pour votre environnement sur toutes les instances de SQL Server : 

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
>Si vous utilisez SQL Server Express Edition sur un nœud pour héberger un seul réplica de configuration, la seule valeur valide pour le rôle est `WITNESS`. Exécutez le script suivant dans SQL Server Express Edition.
>```SQL
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

The TCP port on the firewall needs to be open for the listener port.



>[!IMPORTANT]
>For SQL Server 2017 release, the only authentication method supported for database mirroring endpoint is `CERTIFICATE`. `WINDOWS` option will be enabled in a future release.

For complete information, see [The Database Mirroring Endpoint (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).
