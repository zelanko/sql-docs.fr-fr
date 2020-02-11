---
title: sys. login_token (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- login_token_TSQL
- sys.login_token_TSQL
- sys.login_token
- login_token
dev_langs:
- TSQL
helpviewer_keywords:
- sys.login_token catalog view
- logins [SQL Server], security tokens
- tokens [SQL Server]
ms.assetid: 86e06938-9d0a-44e5-99e2-55c8ef5f2f84
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: fb396d47da69724d16c0d72e1373527f9c5e700f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68102427"
---
# <a name="syslogin_token-transact-sql"></a>sys.login_token (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque principal de serveur appartenant au jeton de connexion.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**principal_id**|**int**|ID du principal. Cette valeur est unique dans le serveur.|  
|**sid**|**varbinary(85)**|Identificateur de sécurité du principal. S’il s’agit d’un principal Windows, **sid** = SID Windows. Si la connexion est mappée à un certificat, **sid** = GUID à partir du certificat.|  
|**nomme**|**nvarchar(128)**|Nom du principal. Cette valeur est unique dans le serveur.|  
|**entrer**|**nvarchar(128)**|Description du type de principal. Tous les types sont mappés à **sid**. Les valeurs possibles sont les suivantes :<br /><br /> SQL LOGIN<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> SERVER ROLE<br /><br /> LOGIN MAPPED TO CERTIFICATE<br /><br /> LOGIN MAPPED TO ASYMMETRIC KEY<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**syntaxe**|**nvarchar(128)**|Indique que le principal prend part à l'évaluation des autorisations GRANT ou DENY, ou sert d'authentificateur.<br /><br /> Cette valeur peut être l'une des suivantes :<br /><br /> GRANT OR DENY<br /><br /> DENY ONLY<br /><br /> AUTHENTICATOR|  
  
## <a name="see-also"></a>Voir aussi  
 [sys. user_token &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-user-token-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys. database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
