---
title: sp_syscollector_run_collection_set (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_run_collection_set_TSQL
- sp_syscollector_run_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_run_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 7bbaee48-dfc7-45c0-b11f-c636b6a7e720
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e2ad81b1d92bb45d9ab15ca11897804cc0d333a9
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531401"
---
# <a name="spsyscollectorruncollectionset-transact-sql"></a>sp_syscollector_run_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Démarre un jeu d'éléments de collecte si le collecteur est déjà activé et si le jeu d'éléments de collecte est configuré en mode de collecte sans mise en cache.  
  
> [!NOTE]  
>  Cette procédure échouera si elle est exécutée sur un jeu d'éléments de collecte configuré en mode de collecte mise en cache.  
  
 sp_syscollector_run_collection_set permet à un utilisateur de prendre des instantanés de données à la demande.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syscollector_run_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @collection_set_id = ] collection_set_id` Est l’identificateur local unique pour l’ensemble de la collection. *collection_set_id* est **int** et doit avoir une valeur si *nom* est NULL.  
  
`[ @name = ] 'name'` Est le nom de l’ensemble de la collection. *nom* est **sysname** et doit avoir une valeur si *collection_set_id* a la valeur NULL.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Soit *collection_set_id* ou *nom* doit avoir une valeur, les deux ne peut pas être NULL.  
  
 Cette procédure démarre la collection et télécharger des travaux pour ensemble de la collection spécifiée et démarre immédiatement le travail d’agent de collecte si le jeu de collection a son **@collection_mode** non mis en cache (1) la valeur. Pour plus d’informations, consultez [sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 sp_sycollector_run_collection_set peut également être utilisé pour exécuter un jeu d'éléments de collection sans planification.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **dc_operator** (avec autorisation EXECUTE) rôle fixe de base de données pour exécuter cette procédure.  
  
## <a name="example"></a>Exemple  
 Démarrez un jeu d'éléments de collecte à l'aide de son identificateur.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_run_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  
