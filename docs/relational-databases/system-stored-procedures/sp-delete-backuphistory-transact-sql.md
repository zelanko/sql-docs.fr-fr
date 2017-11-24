---
title: sp_delete_backuphistory (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_backuphistory
- sp_delete_backuphistory_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_delete_backuphistory
ms.assetid: bdb56834-616e-47e4-b942-e895d2325e97
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 700c5a3849aea0fe2d1db07cc0cce96bdc8d7e7b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spdeletebackuphistory-transact-sql"></a>sp_delete_backuphistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Réduit la taille des tables d'historique de sauvegarde et de restauration en supprimant les entrées correspondant aux jeux de sauvegarde antérieurs à la date spécifiée. Des lignes supplémentaires sont ajoutées à la sauvegarde et restauration des tables d’historique après chaque sauvegarde ou une opération de restauration est effectuée ; Par conséquent, nous vous recommandons d’exécuter régulièrement **sp_delete_backuphistory**.  
  
> [!NOTE]  
>  Les tables d’historique de sauvegarde et de restauration résident dans le **msdb** base de données.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_backuphistory [ @oldest_date = ] 'oldest_date'   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@oldest_date=** ] **'***oldest_date***'**  
 Date la plus ancienne conservée dans les tables d'historique de sauvegarde et de restauration. *l’argument oldest_date* est **datetime**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="remarks"></a>Notes  
 **sp_delete_backuphistory** doit être exécuté à partir de la **msdb** de base de données et affecte les tables suivantes :  
  
-   [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
  
-   [backupmediafamily](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
  
-   [backupmediaset](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
  
-   [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [restorefile](../../relational-databases/system-tables/restorefile-transact-sql.md)  
  
-   [restorefilegroup](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
  
-   [restorehistory](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
  
 Les fichiers de sauvegarde physiques sont conservés, même si tout l'historique est supprimé.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **sysadmin** rôle serveur fixe, mais les autorisations peuvent être accordées à d’autres utilisateurs.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime toutes les entrées créées avant le 14 janvier 2010, 12h00, dans les tables d'historique de sauvegarde et de restauration.  
  
```  
USE msdb;  
GO  
EXEC sp_delete_backuphistory @oldest_date = '01/14/2010';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_delete_database_backuphistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql.md)   
 [Historique de sauvegarde et informations d’en-tête &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
