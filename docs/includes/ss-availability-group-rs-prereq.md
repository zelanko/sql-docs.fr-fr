## <a name="prerequisites"></a>Conditions préalables requises

Avant de créer le groupe de disponibilité, vous devez :

- Définir votre environnement de sorte que tous les serveurs qui hébergeront des réplicas de disponibilité puissent communiquer.
- Installez SQL Server. Pour plus d’informations, consultez [Installer SQL Server](../database-engine/install-windows/install-sql-server.md).

## <a name="enable-always-on-availability-groups-and-restart-mssql-server"></a>Activer les groupes de disponibilité AlwaysOn et redémarrer mssql-server

>[!NOTE]
>La commande suivante utilise des applets de commande du module sqlserver publié dans PowerShell Gallery. Vous pouvez installer ce module avec la commande Install-Module.

Activez les groupes de disponibilité AlwaysOn sur chaque réplica qui héberge une instance de SQL Server. Ensuite, redémarrez le service SQL Server. Exécutez la commande suivante pour activer et redémarrer les services SQL Server :

```powershell
Enable-SqlAlwaysOn -ServerInstance <server\instance> -Force
```

## <a name="enable-an-alwayson_health-event-session"></a>Activer une session d’événements AlwaysOn_health

 Pour faciliter le diagnostic de la cause principale quand vous résolvez les problèmes d’un groupe de disponibilité, vous pouvez activer une session d’événements étendus (XEvents) des groupes de disponibilité AlwaysOn. Pour cela, exécutez la commande suivante sur chaque instance de SQL Server :

```sql
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Pour plus d’informations sur cette session XEvents, consultez [Événements étendus des groupes de disponibilité AlwaysOn](../database-engine/availability-groups/windows/always-on-extended-events.md).

## <a name="database-mirroring-endpoint-authentication"></a>Authentification du point de terminaison de mise en miroir de bases de données

Pour que la synchronisation fonctionne correctement, les réplicas impliqués dans le groupe de disponibilité avec échelle lecture doivent s’authentifier sur le point de terminaison. Les deux scénarios principaux que vous pouvez utiliser pour ce type d’authentification sont traités dans les sections suivantes.

### <a name="service-account"></a>Compte de service

Dans un environnement Active Directory où tous les réplicas secondaires sont joints au même domaine, SQL Server peut utiliser le compte de service pour l’authentification. Vous devez créer explicitement une connexion pour le compte de service sur chaque instance de SQL Server :

```sql
CREATE LOGIN [<domain>\service account] FROM WINDOWS;
```

### <a name="sql-login-authentication"></a>Authentification de la connexion SQL

Dans les environnements où les réplicas secondaires ne sont peut-être pas joints à un domaine Active Directory, vous devez utiliser l’authentification SQL. Le script Transact-SQL suivant crée une connexion nommée `dbm_login` et un utilisateur nommé `dbm_user`. Mettez à jour le script avec un mot de passe fort. Pour créer l’utilisateur de point de terminaison de mise en miroir de bases de données, exécutez la commande suivante sur toutes les instances de SQL Server :

```sql
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

#### <a name="certificate-authentication"></a>Authentification par certificat

Si vous utilisez un réplica secondaire qui nécessite l’authentification SQL, utilisez un certificat pour l’authentification entre les points de terminaison de mise en miroir.

Le script Transact-SQL suivant crée une clé principale et un certificat. Il sauvegarde ensuite le certificat et sécurise le fichier avec une clé privée. Mettez à jour le script avec des mots de passe forts. Exécutez le script suivant sur l’instance principale de SQL Server pour créer le certificat :

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = 'c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

À ce stade, votre réplica SQL Server principal a un certificat à l’emplacement `c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer` et une clé privée à l’emplacement `c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk`. Copiez ces deux fichiers au même emplacement sur tous les serveurs qui hébergeront les réplicas de disponibilité.

Sur chaque réplica secondaire, vérifiez que le compte de service pour l’instance de SQL Server dispose des autorisations d’accès au certificat.

#### <a name="create-the-certificate-on-secondary-servers"></a>Créer le certificat sur les serveurs secondaires

Le script Transact-SQL suivant crée une clé principale et un certificat à partir de la sauvegarde que vous avez créée sur le réplica SQL Server principal. La commande autorise également les utilisateurs à accéder au certificat. Mettez à jour le script avec des mots de passe forts. Le mot de passe de déchiffrement est le même mot de passe que celui que vous avez utilisé pour créer le fichier *.pvk* à une étape précédente. Pour créer le certificat, exécutez le script suivant sur tous les réplicas secondaires :

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate
    AUTHORIZATION dbm_user
    FROM FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = 'c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-database-mirroring-endpoints-on-all-replicas"></a>Créer des points de terminaison de mise en miroir de bases de données sur tous les réplicas

Les points de terminaison de mise en miroir de bases de données utilisent le protocole TCP (Transmission Control Protocol) pour l’envoi et la réception de messages entre les instances de serveur participant à des sessions de mise en miroir de bases de données ou hébergeant des réplicas de disponibilité. Le point de terminaison de mise en miroir de bases de données écoute sur un seul numéro de port TCP.

Le script Transact-SQL suivant crée un point de terminaison d’écoute nommé `Hadr_endpoint` pour le groupe de disponibilité. Il démarre le point de terminaison et donne une autorisation de connexion au compte de service ou à la connexion SQL que vous avez créé au cours d’une étape précédente. Avant d’exécuter le script, remplacez les valeurs entre `**< ... >**`. Vous pouvez aussi inclure une adresse IP, `LISTENER_IP = (0.0.0.0)`. L’adresse IP de l’écouteur doit être une adresse IPv4. Vous pouvez également utiliser `0.0.0.0`.

Mettez à jour le script Transact-SQL suivant pour votre environnement sur toutes les instances de SQL Server :

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [<service account or user>];
```

Le port TCP sur le pare-feu doit être ouvert pour le port de l’écouteur.

Pour plus d’informations, consultez [Point de terminaison de mise en miroir de bases de données (SQL Server)](https://docs.microsoft.com/sql/database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server?view=sql-server-2017).
