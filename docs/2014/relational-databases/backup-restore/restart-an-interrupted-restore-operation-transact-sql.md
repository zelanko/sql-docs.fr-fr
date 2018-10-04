---
title: Redémarrer une opération de restauration interrompue (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 22f5b597f7482c5a417633322f13776578e595e2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48143469"
---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a>Redémarrer une opération de restauration interrompue (Transact-SQL)
  Cette rubrique explique comment redémarrer une opération de restauration interrompue.  
  
### <a name="to-restart-an-interrupted-restore-operation"></a>Pour redémarrer une opération de restauration interrompue  
  
1.  Relancez l'exécution de l'instruction RESTORE interrompue, en spécifiant :  
  
    -   les mêmes clauses que celles utilisées dans l'instruction RESTORE d'origine ;  
  
    -   la clause RESTART.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant redémarre une opération de restauration interrompue.  
  
```tsql  
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
  
## <a name="see-also"></a>Voir aussi  
 [Restaurations complètes de bases de données &#40;mode de récupération complète&#41;](complete-database-restores-full-recovery-model.md)   
 [Restaurations complètes de bases de données &#40;mode de récupération simple&#41;](complete-database-restores-simple-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
