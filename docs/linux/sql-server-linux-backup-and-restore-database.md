---
title: "Sauvegarde et restauration des bases de données SQL Server sur Linux | Documents Microsoft"
description: "Découvrez comment sauvegarder et restaurer des bases de données SQL Server sur Linux."
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: d30090fb-889f-466e-b793-5f284fccc4e6
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: a34954f14ad4c40fdc7376f3f35c6a3def6e2ec7
ms.contentlocale: fr-fr
ms.lasthandoff: 10/02/2017

---
# <a name="backup-and-restore-sql-server-databases-on-linux"></a>Sauvegarde et restauration de bases de données SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Pour effectuer des sauvegardes de bases de données à partir de 2017 du serveur SQL sur Linux avec les mêmes outils que les autres plates-formes. Sur un serveur Linux, vous pouvez utiliser `sqlcmd` pour vous connecter à SQL Server et effectuer des sauvegardes. À partir de Windows, vous pouvez vous connecter à SQL Server sur Linux et effectuer des sauvegardes avec l’interface utilisateur. La fonctionnalité de sauvegarde est le même sur plusieurs plateformes. Par exemple, vous pouvez sauvegarder les bases de données localement, aux lecteurs à distance ou aux [service de stockage d’objets Blob Microsoft Azure](http://msdn.microsoft.com/library/dn435916.aspx). 

## <a name="backup-with-sqlcmd"></a>Sauvegarde avec sqlcmd

Dans l’exemple suivant `sqlcmd` se connecte à l’instance locale de SQL Server et prend un complet sauvegarde de base de données utilisateur appelée `demodb`.

```bash
sqlcmd -H localhost -U SA -Q "BACKUP DATABASE [demodb] TO DISK = N'var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

Lorsque vous exécutez la commande, SQL Server demande un mot de passe. Une fois que vous entrez le mot de passe, l’interpréteur de commandes retournera les résultats de la sauvegarde en cours. Exemple :

```
Password:
10 percent processed.
21 percent processed.
32 percent processed.
40 percent processed.
51 percent processed.
61 percent processed.
72 percent processed.
80 percent processed.
91 percent processed.
Processed 296 pages for database 'demodb', file 'demodb' on file 1.
100 percent processed.
Processed 2 pages for database 'demodb', file 'demodb_log' on file 1.
BACKUP DATABASE successfully processed 298 pages in 0.064 seconds (36.376 MB/sec).
```

### <a name="backup-log-with-sqlcmd"></a>Journal de sauvegarde avec sqlcmd

Dans l’exemple suivant, `sqlcmd` se connecte à l’instance locale de SQL Server et prend la sauvegarde de fin du journal. Une fois l’opération de sauvegarde terminée, la base de données sera dans un état de restauration. 

```bash
sqlcmd -H localhost -U SA -Q "BACKUP LOG [demodb] TO  DISK = N'var/opt/mssql/data/demodb_LogBackup_2016-11-14_18-09-53.bak' WITH NOFORMAT, NOINIT,  NAME = N'demodb_LogBackup_2016-11-14_18-09-53', NOSKIP, NOREWIND, NOUNLOAD,  NORECOVERY ,  STATS = 5"
```


## <a name="restore-with-sqlcmd"></a>Restauration avec sqlcmd

Dans l’exemple suivant `sqlcmd` se connecte à l’instance locale de SQL Server et restaure une base de données.

```bash
sqlcmd -H localhost -U SA -Q "RESTORE DATABASE [demodb] FROM  DISK = N'var/opt/mssql/data/demodb.bak' WITH  FILE = 1,  NOUNLOAD,  REPLACE,  STATS = 5"
```

## <a name="backup-and-restore-with-sql-server-management-studio-ssms"></a>Sauvegarde et restauration avec SQL Server Management Studio (SSMS)

Vous pouvez utiliser SSMS à partir d’un ordinateur Windows pour vous connecter à une base de données de Linux et effectuez une sauvegarde via l’interface utilisateur. 

>[!NOTE] 
> Utiliser la dernière version de SSMS pour vous connecter à SQL Server. Pour télécharger et installer la version la plus récente, consultez [télécharger SSMS](http://msdn.microsoft.com/library/mt238290.aspx). 

Les étapes suivantes en effectuant une sauvegarde avec SSMS. 

1. Démarrez SSMS et connectez-vous à votre serveur dans 2017 du serveur SQL sur Linux.

1. Dans l’Explorateur d’objets, cliquez sur votre base de données, cliquez sur **tâches**, puis cliquez sur **sauvegarder...** .

1. Dans le **sauvegarde la base de données** boîte de dialogue, vérifiez les paramètres et options, puis cliquez sur **OK**.
 
SQL Server termine la sauvegarde de base de données.

Pour plus d’informations, consultez [SSMS d’utilisation pour gérer SQL Server sur Linux](sql-server-linux-manage-ssms.md).

### <a name="restore-with-sql-server-management-studio-ssms"></a>Restauration avec SQL Server Management Studio (SSMS) 

Les étapes suivantes vous guident tout au long de la restauration d’une base de données avec SSMS.

1. Dans SSMS droit **bases de données** et cliquez sur **restaurer les bases de données...** . 

1. Sous **Source** cliquez sur **périphérique :** puis cliquez sur le bouton de sélection (...).

1. Recherchez votre fichier de sauvegarde de base de données et cliquez sur **OK**. 

1. Sous **du plan de restauration**, vérifiez le fichier de sauvegarde et les paramètres. Cliquez sur **OK**. 

1. SQL Server restaure la base de données. 

## <a name="see-also"></a>Voir aussi

* [Créer une sauvegarde complète de la base de données (SQL Server)](http://msdn.microsoft.com/library/ms187510.aspx)
* [Sauvegarder un journal des transactions (SQL Server)](http://msdn.microsoft.com/library/ms179478.aspx)
* [BACKUP (Transact-SQL)](http://msdn.microsoft.com/library/ms186865.aspx)
* [Sauvegarde SQL Server vers une URL](http://msdn.microsoft.com/library/dn435916.aspx)

