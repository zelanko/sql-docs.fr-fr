---
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
ms.openlocfilehash: 90b8f5c2886da151ae15e9dc1dbcaace9d5093a6
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896368"
---
# <a name="drop-endpoint-transact-sql"></a>DROP ENDPOINT (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Supprime un point de terminaison existant.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP ENDPOINT endPointName  
```  
  
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
  
  
