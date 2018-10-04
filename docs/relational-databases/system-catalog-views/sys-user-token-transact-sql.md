---
title: Sys.user_token (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.user_token
- user_token
- sys.user_token_TSQL
- user_token_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], security tokens
- sys.user_token catalog view
- user tokens [SQL Server]
- tokens [SQL Server]
- user_token catalog view
ms.assetid: be018103-5e57-43a4-9160-9bf420892aa7
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 806675392484e7d9d23d9432b336f6367d04bd1c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47770137"
---
# <a name="sysusertoken-transact-sql"></a>sys.user_token (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie une ligne pour chaque principal de base de données faisant partie du jeton de l'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**principal_id**|**Int**|ID du principal. Sa valeur est unique dans une base de données.|  
|**sid**|**varbinary(85)**|Identificateur de sécurité du principal, si le principal est défini comme externe à la base de données. Par exemple, ce peut être une information de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Windows, Windows Group, ou une information de connexion mappée sur un certificat ; sinon, cette valeur est NULL.|  
|**nom**|**nvarchar (128)**|Nom du principal. Sa valeur est unique dans une base de données.|  
|**type**|**nvarchar (128)**|Description du type de principal. Tous les types sont mappés aux **sid**. Il peut s'agir de l'une des valeurs suivantes :<br /><br /> SQL USER<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> ROLE<br /><br /> APPLICATION ROLE<br /><br /> DATABASE ROLE<br /><br /> USER MAPPED TO CERTIFICATE<br /><br /> USER MAPPED TO ASYMMETRIC KEY<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**Utilisation**|**nvarchar (128)**|Indique que le principal prend part à l'évaluation des autorisations GRANT ou DENY, ou sert d'authentificateur.<br /><br /> Cette valeur peut être une des opérations suivantes :<br /><br /> GRANT OR DENY<br /><br /> DENY ONLY<br /><br /> AUTHENTICATOR|  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.login_token &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-login-token-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
