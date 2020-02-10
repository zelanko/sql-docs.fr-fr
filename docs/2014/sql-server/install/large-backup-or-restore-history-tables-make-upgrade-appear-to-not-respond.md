---
title: Les tables d’historique de sauvegarde ou de restauration volumineuses semblent ne pas répondre à la mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e4d994eb6d345ab98e6cd51a44c7c90a74bafd3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70874600"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a>Les tables d'historique de sauvegarde ou de restauration importantes donnent l'impression que la mise à niveau ne répond pas
  Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], de nouvelles colonnes ont été ajoutées dans certaines tables d'historique de sauvegarde et de restauration. La mise à niveau de ces tables implique de les modifier pour ajouter les nouvelles colonnes. Si une ou plusieurs de ces tables contiennent un grand nombre de lignes, la mise à niveau semblera bloquée pendant une durée substantielle sur l'instruction ALTER TABLE qui ajoute des colonnes à ces tables.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 La mise à niveau peut sembler ne plus répondre si l’une des tables d’historique de sauvegarde ou de restauration suivantes contient un grand nombre de lignes :  
  
-   **backupfile**  
  
-   **backupmediafamily**  
  
-   **backupmediaset**  
  
-   **backupset**  
  
-   **restorefile**  
  
-   **restorefilegroup**  
  
-   **restorehistory**  
  
 Si l'une de ces tables possède 10 000 lignes ou plus, le Conseiller de mise à niveau signale un échec de non-conformité. Il ne signale pas la table dont le nombre de lignes dépasse le nombre autorisé. La première table qui possède plus de 10 000 lignes provoque l'échec.  
  
## <a name="corrective-action"></a>Action corrective  
 Avant la mise à niveau d'une base de données, si l'une de ces tables possède plus de 10 000 lignes, nous vous recommandons de réduire ce nombre à moins de 10 000. Pour réduire les lignes de toutes ces tables, vous pouvez exécuter la procédure stockée **sp_delete_backuphistory** . Cette procédure supprime les entrées dans toutes les tables d'historique de sauvegarde et de restauration correspondant aux jeux de sauvegarde antérieurs à la date spécifiée. Pour plus d’informations, consultez [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).  
  
> [!NOTE]  
>  Vous pouvez mettre à niveau une base de données dont les tables d'historique de sauvegarde et de restauration possèdent plus de 10 000 lignes. Toutefois, la mise à niveau peut paraître bloquée pendant que les tables de grande taille sont modifiées. Plus les tables sont grandes, plus l'exécution du programme d'installation dure.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
