---
title: DROP ENDPOINT (Transact-SQL) | Documents Microsoft
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
- DROP_ENDPOINT_TSQL
- DROP ENDPOINT
dev_langs: TSQL
helpviewer_keywords:
- removing endpoints
- endpoints [SQL Server], removing
- deleting endpoints
- DROP ENDPOINT statement
- dropping endpoints
ms.assetid: 6aca7412-66a5-4fa4-86b2-061512ff2080
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a5f08fbbb767d5272d0cb5999c68359eaab7fb7b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="drop-endpoint-transact-sql"></a>DROP ENDPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un point de terminaison existant.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP ENDPOINT endPointName  
```  
  
## <a name="arguments"></a>Arguments  
 *endPointName*  
 Nom du point de terminaison à supprimer.  
  
## <a name="remarks"></a>Notes  
 Il n'est pas possible d'exécuter d'instructions ENDPOINT DDL à l'intérieur d'une transaction utilisateur.  
  
## <a name="permissions"></a>Permissions  
 Utilisateur doit être un membre de la **sysadmin** le propriétaire du point de terminaison, du rôle de serveur fixe ou avoir reçu l’autorisation CONTROL sur le point de terminaison.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le point de terminaison `sql_endpoint`, créé auparavant.  
  
```  
DROP ENDPOINT sql_endpoint;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
