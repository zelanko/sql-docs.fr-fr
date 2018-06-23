---
title: Redémarrer une opération de restauration interrompue (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 65eb8e196b016bf3ae0595d7d0de87d67f67ace6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052409"
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
  
  
