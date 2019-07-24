---
ms.openlocfilehash: bf755ccfe5a1a6816129173dcb6ad5050ea5e114
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68213320"
---

## <a name="add-a-database-to-the-availability-group"></a>Ajouter une base de données au groupe de disponibilité

Vérifiez que la base de données que vous ajoutez au groupe de disponibilité est en mode de récupération complète et a une sauvegarde de fichier journal valide. S’il s’agit d’une base de données de test ou d’une base de données nouvellement créée, faites-en une sauvegarde. Pour créer et sauvegarder une base de données nommée `db1`, exécutez le script Transact-SQL suivant sur le serveur SQL Server principal :

```sql
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1]
   TO DISK = N'c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Backup\db1.bak';
```

Pour ajouter une base de données nommée `db1` à un groupe de disponibilité nommé `ag1`, exécutez le script Transact-SQL suivant sur le réplica SQL Server principal :

```sql
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Vérifier que la base de données est créée sur les serveurs secondaires

Pour déterminer si la base de données `db1` a été créée et si elle est synchronisée, exécutez la requête suivante sur chaque réplica SQL Server secondaire :

```sql
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
