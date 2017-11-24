---
title: SUPPRIMER le POOL de ressources externes (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/17/2016
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
- DROP EXTERNAL RESOURCE POOL
- DROP_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs: TSQL
helpviewer_keywords: DROP EXTERNAL RESOURCE POOL statement
ms.assetid: e2fa01bd-96ff-4ea9-bb08-6cb6b6adf68c
caps.latest.revision: "6"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: edd6e956bc9453317c928a099469e65ddf5e0e0f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="drop-external-resource-pool-transact-sql"></a>SUPPRIMER le POOL de ressources externes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Supprime un pool de ressources externes du gouverneur de ressources permet de définir des ressources pour les processus externes. Pour R Services régit le pool externe `rterm.exe`, `BxlServer.exe`et les autres processus engendrés par ces derniers. Pools de ressources externes sont créés à l’aide de [CREATE EXTERNAL RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-resource-pool-transact-sql.md) et modifié à l’aide de [ALTER EXTERNAL RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-external-resource-pool-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DROP EXTERNAL RESOURCE POOL pool_name  
```  
  
## <a name="arguments"></a>Arguments  
 *nom du pool*  
 Le nom du pool de ressources externes à supprimer.  
  
## <a name="remarks"></a>Notes  
 Vous ne pouvez pas supprimer un pool de ressources externes s’il contient des groupes de charges de travail.  
  
 Vous ne pouvez pas supprimer les pools par défaut ou interne du gouverneur de ressources.  
  
 La reconfiguration est n  
  
 Lorsque vous exécutez des instructions DDL, nous vous recommandons de connaître les états du gouverneur de ressources. Pour plus d’informations, consultez [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation `CONTROL SERVER`.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant supprime le pool de ressources externe nommé `ex_pool`.  
  
```  
DROP EXTERNAL RESOURCE POOL ex_pool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Option de Configuration de serveur scripts externes activés](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Problèmes connus pour SQL Server R Services](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [MODIFIER le POOL de ressources externes &#40; Transact-SQL &#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)  
  
  
