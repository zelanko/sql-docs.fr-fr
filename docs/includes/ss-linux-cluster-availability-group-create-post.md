
## <a name="add-a-database-to-the-availability-group"></a>Ajouter une base de données au groupe de disponibilité

Assurez-vous que la base de données que vous ajoutez au groupe de disponibilité est en mode de récupération complète et une sauvegarde de journal valide. S’il s’agit d’une base de données de test ou d’une base de données nouvellement créé, effectuez une sauvegarde de base de données. Sur le serveur SQL principal, exécutez le script Transact-SQL suivant pour créer, sauvegarder une base de données appelée `db1`:

```Transact-SQL
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

Sur le réplica principal de SQL Server, exécutez le script Transact-SQL suivant pour ajouter une base de données appelée `db1` à un groupe de disponibilité nommé `ag1`:

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Vérifier que la base de données est créée sur les serveurs secondaires

Sur chaque réplica secondaire de SQL Server, exécutez la requête suivante pour voir si le `db1` base de données a été créé et qu’il est synchronisé :

```Transact-SQL
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
