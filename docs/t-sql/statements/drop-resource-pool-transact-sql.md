---
title: SUPPRIMER le POOL de ressources (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP RESOURCE POOL
- DROP_RESOURCE_POOL_TSQL
dev_langs: TSQL
helpviewer_keywords: DROP RESOURCE POOL
ms.assetid: 18cd6dd9-7a6d-4a08-b9d5-649af23583d5
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 77a09f66029777a761aec853916c59f2c8e0695e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="drop-resource-pool-transact-sql"></a>DROP RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un pool de ressources du gouverneur de ressources défini par l'utilisateur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP RESOURCE POOL pool_name  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *nom du pool*  
 Nom d'un pool de ressources défini par l'utilisateur existant.  
  
## <a name="remarks"></a>Notes  
 Vous ne pouvez pas supprimer un pool de ressources qui contient des groupes de charges de travail.  
  
 Vous ne pouvez pas supprimer les pools par défaut ou interne du gouverneur de ressources.  
  
 Lorsque vous exécutez des instructions DDL, nous vous recommandons de connaître les états du gouverneur de ressources. Pour plus d’informations, consultez [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md).  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le pool de ressources nommé `big_pool`.  
  
```  
DROP RESOURCE POOL big_pool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
