---
title: sp_syscollector_start_collection_set (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2016
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
- sp_syscollector_start_collection_set_TSQL
- sp_syscollector_start_collection_set
dev_langs: TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_start_collection_set
ms.assetid: d8357180-f51e-4681-99f9-0596fe2d2b53
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 32ab8a570febc69a91346e39c8f200a36a263aa8
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spsyscollectorstartcollectionset-transact-sql"></a>sp_syscollector_start_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Démarre un jeu d'éléments de collecte si le collecteur est déjà activé et que le jeu d'éléments de collecte n'est pas en cours d'exécution. Si le collecteur n’est pas activé, activez-le en exécutant [sp_syscollector_enable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql.md) , puis utilisez cette procédure stockée pour démarrer un jeu de collections.  

  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syscollector_start_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@collection_set_id =** ] *collection_set_id*  
 Identificateur local unique pour le jeu d'éléments de collecte. *collection_set_id* est **int** avec une valeur par défaut NULL. *collection_set_id* doit avoir une valeur si *nom* est NULL.  
  
 [  **@name =** ] '*nom*'  
 Est le nom de l’ensemble de la collection. *nom* est **sysname** avec une valeur par défaut NULL. *nom* doit avoir une valeur si *collection_set_id* a la valeur NULL.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 sp_syscollector_create_collection_set doit être exécuté dans le contexte de la base de données système msdb et l'Agent SQL Server doit être activé.  
  
 Cette procédure échoue si elle est exécutée sur un jeu d'éléments de collecte sans planification. Si l’ensemble de la collection n’a pas une planification (car son mode de collecte est défini à non mis en cache, par exemple), utilisez la [sp_syscollector_run_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql.md) une procédure stockée à démarrer l’ensemble de la collection.  
  
 Cette procédure active les travaux de collecte et de téléchargement pour le jeu d'éléments de collecte spécifié, et démarre immédiatement le travail de l'agent de collecte si le mode de collecte a la valeur 0 (mis en cache). Pour plus d’informations, consultez [sp_syscollector_create_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 Si le jeu d'éléments de collecte ne contient aucun élément de collecte, cette opération est sans effet. L'erreur 14685 est retournée en tant qu'avertissement.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle de base de données fixe dc_operator pour exécuter cette procédure. Si le jeu d'éléments de collecte n'a pas de compte proxy, l'appartenance au rôle serveur fixe sysadmin est requis.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant démarre un jeu d'éléments de collecte à l'aide de son identificateur.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  
