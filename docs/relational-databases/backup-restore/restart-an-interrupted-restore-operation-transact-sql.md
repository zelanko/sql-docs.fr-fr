---
title: "Redémarrer une opération de restauration interrompue (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea2993557756fc3808000064e5a6088ce27c32a4
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a>Redémarrer une opération de restauration interrompue (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique explique comment redémarrer une opération de restauration interrompue.  
  
### <a name="to-restart-an-interrupted-restore-operation"></a>Pour redémarrer une opération de restauration interrompue  
  
1.  Relancez l'exécution de l'instruction RESTORE interrompue, en spécifiant :  
  
    -   les mêmes clauses que celles utilisées dans l'instruction RESTORE d'origine ;  
  
    -   la clause RESTART.  
  
## <a name="example"></a> Exemple  
 L'exemple suivant redémarre une opération de restauration interrompue.  
  
```sql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Restaurations complètes de bases de données &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Restaurations complètes de bases de données &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
