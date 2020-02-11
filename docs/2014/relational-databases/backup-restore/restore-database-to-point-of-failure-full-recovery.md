---
title: Restaurer une base de données jusqu’au point de défaillance en mode de récupération complète (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- point of failure [SQL Server]
- restoring databases [SQL Server], point of failure
- database restores [SQL Server], point of failure
ms.assetid: 04106e18-bbf7-4a5e-a2e1-3d65319814d5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 83319e8eb1fe692bc55b764445ac155d9e1ad38d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62920993"
---
# <a name="restore-a-database-to-the-point-of-failure-under-the-full-recovery-model-transact-sql"></a>Restaurer une base de données jusqu'au point d'échec en mode de récupération complète (Transact-SQL)
  Cette rubrique explique comment restaurer jusqu'au point d'échec. Cette rubrique s'applique uniquement aux bases de données employant les modes de restauration complète ou de récupération utilisant les journaux de transactions.  
  
### <a name="to-restore-to-the-point-of-failure"></a>Pour restaurer jusqu'au point d'échec  
  
1.  Sauvegardez la fin du journal en exécutant l’instruction [BACKUP](/sql/t-sql/statements/backup-transact-sql) de base suivante :  
  
    ```  
    BACKUP LOG <database_name> TO <backup_device>   
       WITH NORECOVERY, NO_TRUNCATE;  
    ```  
  
2.  Restaurez une sauvegarde de base de données complète en exécutant l’instruction [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) de base suivante :  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
3.  Restaurez, éventuellement, une sauvegarde de base de données différentielle en exécutant l'instruction de base suivante RESTORE DATABASE :  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
4.  Appliquez chaque journal des transactions, y compris la sauvegarde de la fin du journal que vous avez créée à l'étape 1, en spécifiant WITH NORECOVERY dans l'instruction RESTORE LOG :  
  
    ```  
    RESTORE LOG <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
5.  Récupérez la base de données en exécutant l'instruction RESTORE DATABASE suivante :  
  
    ```  
    RESTORE DATABASE <database_name>   
       WITH RECOVERY;  
    ```  
  
## <a name="example"></a>Exemple  
 Avant de pouvoir exécuter cet exemple, vous devez terminer les préparations suivantes :  
  
1.  Le mode de récupération par défaut de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] est le mode de récupération simple. Étant donné que ce mode de récupération ne prend pas en charge la restauration jusqu’au point de défaillance, définissez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] pour utiliser le mode de restauration complète en exécutant l’instruction [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) suivante :  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
    ```  
  
2.  Créez une sauvegarde de base de données complète à l'aide de l'instruction suivante BACKUP :  
  
    ```  
    BACKUP DATABASE AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Data.bck';  
    ```  
  
3.  Créez une sauvegarde de routine des journaux :  
  
    ```  
    BACKUP LOG AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Log.bck';  
    ```  
  
 L'exemple suivant restaure les sauvegardes créées précédemment, après la création d'une sauvegarde de la fin du journal de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . (Cette étape suppose que le disque du journal est accessible).  
  
 Commencez par créer une sauvegarde de la fin du journal de la base de données qui capture le journal actif et laisse la base de données à l'état de restauration. Puis, l'exemple restaure la sauvegarde de base de données, applique la sauvegarde de routine des journaux créée précédemment et applique la sauvegarde de la fin du journal. Enfin, l'exemple récupère la base de données dans une étape séparée.  
  
> [!NOTE]  
>  Le comportement par défaut consiste à récupérer une base de données en même temps que l'instruction qui restaure la sauvegarde finale.  
  
```  
/* Example of restoring a to the point of failure */  
-- Step 1: Create a tail-log backup by using WITH NORECOVERY.  
BACKUP LOG AdventureWorks2012  
   TO DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 2: Restore the full database backup.  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Data.bck'  
   WITH NORECOVERY;  
GO  
-- Step 3: Restore the first transaction log backup.  
RESTORE LOG AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 4: Restore the tail-log backup.  
RESTORE LOG AdventureWorks2012  
   FROM  DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 5: Recover the database.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
