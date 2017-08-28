
## <a name="add-a-database-to-the-availability-group"></a>Ajouter une base de données au groupe de disponibilité

Vérifiez que la base de données que vous ajoutez au groupe de disponibilité est en mode de récupération complète et a une sauvegarde de fichier journal valide. S’il s’agit d’une base de données de test ou d’une base de données nouvellement créée, faites une sauvegarde de base de données. Sur le serveur SQL Server principal, exécutez la commande Transact-SQL suivante pour créer et sauvegarder une base de données nommée `db1`.

```Transact-SQL
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

Sur le réplica SQL Server principal, exécutez la commande Transact-SQL suivante pour ajouter une base de données nommée `db1` à un groupe de disponibilité nommé `ag1`.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Vérifier que la base de données est créée sur les serveurs secondaires

Sur chaque réplica SQL Server secondaire, exécutez la requête suivante pour déterminer si la base de données `db1` a été créée et si elle est synchronisée.

```Transact-SQL
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
