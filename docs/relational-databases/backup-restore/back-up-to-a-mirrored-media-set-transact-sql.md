---
title: Sauvegarder sur un support de sauvegarde miroir (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 747f918931944a99d737b21b8a200426f3cf1464
ms.sourcegitcommit: 721ad1cbc10e8147c087ae36b36296d72cbb0de8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2017
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>Sauvegarder sur un support de sauvegarde miroir (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique décrit comment utiliser l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](../../t-sql/statements/backup-transact-sql.md) pour spécifier un support de sauvegarde miroir lors de la sauvegarde d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans l'instruction BACKUP, spécifiez le premier miroir dans la clause TO. Spécifiez ensuite chaque miroir dans sa propre clause MIRROR TO. Les clauses TO et MIRROR TO doivent spécifier le même nombre et type d'unités de sauvegarde.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée le support de sauvegarde mis en miroir illustré dans la figure précédente et sauvegarde la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sur les deux miroirs.  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a>Tâches associées  
 **Pour restaurer une sauvegarde miroir**  
  
-   [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Jeux de supports de sauvegarde en miroir &#40;SQL Server&#41;](../../relational-databases/backup-restore/mirrored-backup-media-sets-sql-server.md)  
  
  
