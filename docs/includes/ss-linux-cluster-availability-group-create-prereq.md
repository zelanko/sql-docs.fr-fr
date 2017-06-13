## <a name="prerequisites"></a>Conditions préalables

Avant de créer le groupe de disponibilité, vous devez :

- Définir votre environnement de sorte que tous les serveurs qui hébergeront les réplicas de disponibilité peuvent communiquer.
- Installation de SQL Server

>[!NOTE]
>Sur Linux, vous devez créer un groupe de disponibilité avant de l’ajouter en tant que ressource de cluster pour être géré par le cluster. Ce document fournit un exemple qui crée le groupe de disponibilité. Pour la distribution des instructions spécifiques pour créer le cluster et ajoutez le groupe de disponibilité en tant que ressource de cluster, consultez les liens sous [étapes](#next-steps).

1. **Mettre à jour le nom d’ordinateur pour chaque ordinateur hôte**

   Chaque nom de SQL Server doit être :
   
   - 15 caractères ou moins
   - Unique au sein du réseau
   
   Pour définir le nom d’ordinateur, modifiez `/etc/hostname`. Le script suivant vous permet de modifier `/etc/hostname` avec `vi`.

   ```bash
   sudo vi /etc/hostname
   ```

1. **Configurer le fichier hosts**

>[!NOTE]
>Si les noms d’hôte sont enregistrés avec leur adresse IP dans le serveur DNS, il est inutile d’effectuer les étapes ci-dessous. Vérifiez que tous les nœuds devant faire partie de la configuration de groupe de disponibilité peuvent communiquer avec d’autres (commande ping le nom d’hôte doit répondre avec l’adresse IP correspondante). Assurez-vous également que ce fichier/etc/hosts ne contient pas un enregistrement qui mappe l’adresse IP d’hôte local 127.0.0.1 avec le nom d’hôte du nœud.


   Le fichier hosts sur chaque serveur contient les adresses IP et les noms de tous les serveurs qui seront incluses dans le groupe de disponibilité. 

   La commande suivante renvoie l’adresse IP du serveur actuel :

   ```bash
   sudo ip addr show
   ```

   Mise à jour `/etc/hosts`. Le script suivant vous permet de modifier `/etc/hosts` avec `vi`.

   ```bash
   sudo vi /etc/hosts
   ```

   L’exemple suivant `/etc/hosts` sur **node1** au gré des ajouts pour **node1** et **node2**. Dans ce document **node1** fait référence au réplica principal de SQL Server. **Node2** fait référence au serveur SQL secondaire. ;


   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 node1
   10.128.16.77 node2
   ```

### <a name="install-sql-server"></a>Installation de SQL Server

Installez SQL Server. Les liens suivants pointent vers les instructions d’installation de SQL Server pour différentes distributions. 

- [Red Hat Enterprise Linux](..\linux\sql-server-linux-setup-red-hat.md)

- [SUSE Linux Enterprise Server](..\linux\sql-server-linux-setup-suse-linux-enterprise-server.md)

- [Ubuntu](..\linux\sql-server-linux-setup-ubuntu.md)

## <a name="enable-always-on-availability-groups-and-restart-sqlserver"></a>Activez les groupes de disponibilité Always On et redémarrez SQL Server

Activer les groupes de disponibilité Always On sur chaque nœud hébergeant le service SQL Server, puis redémarrez `mssql-server`.  Exécutez le script suivant :

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##    <a name="enable-alwaysonhealth-event-session"></a>Activer la session d’événements AlwaysOn_health 

Vous pouvez l’activer optionaly groupes de disponibilité AlwaysOn spécifique des événements étendus pour aider les causes diagnostic lors de la résolution d’un groupe de disponibilité.

```Transact-SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Pour plus d’informations sur cette session XE, consultez [toujours sur les événements étendus](http://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-db-mirroring-endpoint-user"></a>Créer la base de données utilisateur de point de terminaison de mise en miroir

Le script Transact-SQL suivant crée une connexion nommée `dbm_login`et un utilisateur nommé `dbm_user`. Mettre à jour le script avec un mot de passe fort. Exécutez la commande suivante sur tous les serveurs SQL Server pour créer la base de données utilisateur de point de terminaison de mise en miroir.

```Transact-SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>Créer un certificat

Service SQL Server sur Linux utilise des certificats pour authentifier les communications entre les points de terminaison de mise en miroir. 

Le script Transact-SQL suivant crée une clé principale et le certificat. Il sauvegarde le certificat et sécurise le fichier avec une clé privée. Mettre à jour le script avec les mots de passe forts. Se connecter au serveur SQL principal et exécuter Transact-SQL suivant pour créer le certificat :

```Transact-SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = '/var/opt/mssql/data/dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

À ce stade votre réplica principal de SQL Server possède un certificat à `/var/opt/mssql/data/dbm_certificate.cer` et un at de clé privée `var/opt/mssql/data/dbm_certificate.pvk`. Copiez ces deux fichiers dans le même emplacement sur tous les serveurs qui hébergeront les réplicas de disponibilité. Utilisez l’utilisateur mssql ou accorder l’autorisation à l’utilisateur de mssql pour accéder à ces fichiers. 

Par exemple sur le serveur source, la commande suivante copie les fichiers sur l’ordinateur cible. Remplacez le  **<node2>**  valeurs avec les noms des instances de SQL Server qui hébergeront les réplicas. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

Sur le serveur cible, accorder l’autorisation à l’utilisateur mssql d’accéder au certificat.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Créer le certificat sur les serveurs secondaires

Le script Transact-SQL suivant crée une clé principale et le certificat à partir de la sauvegarde que vous avez créé sur le réplica principal de SQL Server. La commande autorise également l’utilisateur d’accéder au certificat. Mettre à jour le script avec les mots de passe forts. Le mot de passe de déchiffrement est le même mot de passe que vous avez utilisé pour créer le fichier .pvk à l’étape précédente. Exécutez le script suivant sur tous les serveurs secondaires pour créer le certificat.

```Transact-SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate   
    AUTHORIZATION dbm_user
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>Créer la base de données mise en miroir des points de terminaison sur tous les réplicas

Les points de terminaison de mise en miroir de bases de données utilisent le protocole TCP (Transmission Control Protocol) pour l'envoi et la réception de messages entre les instances de serveur participant à des sessions de mise en miroir de bases de donnée ou hébergeant des réplicas de disponibilité. Le point de terminaison de mise en miroir de bases de données écoute sur un numéro de port TCP unique. 

L’instruction Transact-SQL suivant crée un point de terminaison écoute nommé `Hadr_endpoint` pour le groupe de disponibilité. Il démarre le point de terminaison, et donne l’autorisation de connexion à l’utilisateur que vous avez créé. Avant d’exécuter le script, remplacez les valeurs comprises entre `**< ... >**`.


>[!NOTE]
>Pour cette version, n’utilisez pas une adresse IP différente pour l’adresse IP d’écouteur. Nous travaillons sur un correctif pour résoudre ce problème, mais la seule valeur acceptable pour le moment est « 0.0.0.0 ».

Mise à jour de l’instruction Transact-SQL suivant pour votre environnement sur toutes les instances de SQL Server : 

```Transact-SQL
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

>[!IMPORTANT]
>Le port TCP sur le pare-feu doit être ouvert pour le port d’écoute.

Pour plus d’informations, consultez [la base de données mise en miroir de point de terminaison (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).
