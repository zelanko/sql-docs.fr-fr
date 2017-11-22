---
title: sp_syscollector_delete_collection_set (Transact-SQL) | Documents Microsoft
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
- sp_syscollector_delete_collection_set_TSQL
- sp_syscollector_delete_collection_set
dev_langs: TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_delete_collecton_set
ms.assetid: 29c63a74-4db4-4068-bd57-9fb519b0c598
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2f7eeff5b125469add891c39b83151c755b20b5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spsyscollectordeletecollectionset-transact-sql"></a>sp_syscollector_delete_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un jeu d'éléments de collecte définis par l'utilisateur et tous ses éléments de collecte.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syscollector_delete_collection_set [[ @collection_set_id = ] collection_set_id OUTPUT ]  
    , [[ @name = ] 'name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @collection_set_id =] *collection_set_id*  
 Identificateur unique pour le jeu d'éléments de collecte. *collection_set_id* est **int** et doit avoir une valeur si *nom* est NULL.  
  
 [ @name =] '*nom*'  
 Est le nom de l’ensemble de la collection. *nom* est **sysname** et doit avoir une valeur si *collection_set_id* a la valeur NULL.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 sp_syscollector_delete_collection_set doit être exécuté dans le contexte de la base de données système msdb.  
  
 Soit *collection_set_id* ou *nom* doit avoir une valeur, les deux ne peut pas être NULL. Pour obtenir ces valeurs, interrogez la vue système syscollector_collection_set.  
  
 Les jeux d'éléments de collecte définis par le système ne peuvent pas être supprimés.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'appartenance au rôle de base de données fixe dc_admin (avec autorisation EXECUTE) pour exécuter cette procédure.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant supprime une collection définie par l’utilisateur, la valeur spécifiant le *collection_set_id*.  
  
```  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_delete_collection_set  
    @collection_set_id = 4;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  
