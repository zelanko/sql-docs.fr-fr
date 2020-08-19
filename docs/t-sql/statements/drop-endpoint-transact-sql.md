---
description: DROP ENDPOINT (Transact-SQL)
title: DROP ENDPOINT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_ENDPOINT_TSQL
- DROP ENDPOINT
dev_langs:
- TSQL
helpviewer_keywords:
- removing endpoints
- endpoints [SQL Server], removing
- deleting endpoints
- DROP ENDPOINT statement
- dropping endpoints
ms.assetid: 6aca7412-66a5-4fa4-86b2-061512ff2080
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c9aabafbad425cf9f570a466bdb01283a141082d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444681"
---
# <a name="drop-endpoint-transact-sql"></a>DROP ENDPOINT (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Supprime un point de terminaison existant.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP ENDPOINT endPointName  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 *endPointName*  
 Nom du point de terminaison à supprimer.  
  
## <a name="remarks"></a>Notes  
 Il n'est pas possible d'exécuter d'instructions ENDPOINT DDL à l'intérieur d'une transaction utilisateur.  
  
## <a name="permissions"></a>Autorisations  
 L’utilisateur doit être membre du rôle serveur fixe **sysadmin**, être propriétaire du point de terminaison ou bénéficier de l’autorisation CONTROL sur ce point de terminaison.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le point de terminaison `sql_endpoint`, créé auparavant.  
  
```  
DROP ENDPOINT sql_endpoint;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
