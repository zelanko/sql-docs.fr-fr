---
title: sys.server_role_members (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_role_members
- sys.server_role_members_TSQL
- server_role_members_TSQL
- sys.server_role_members
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_role_members catalog view
ms.assetid: efa20414-2c6b-45a2-a7a9-60110a24da18
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4107e6c1f675f7fae78ca384c082ef12c2fa309b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743941"
---
# <a name="sysserverrolemembers-transact-sql"></a>sys.server_role_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Renvoie une ligne pour chaque membre de chaque rôle serveur fixe et défini par l'utilisateur.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**Int**|ID du principal de serveur du rôle.|  
|**member_principal_id**|**Int**|ID du principal de serveur du membre.|  
  
 Pour ajouter ou supprimer l’appartenance au rôle de serveur, utilisez le [ALTER SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md)instruction.  
  
## <a name="permissions"></a>Autorisations  
 Connexions peuvent afficher leur propre appartenance au rôle de serveur et les principal_id des membres de rôles serveur fixes. Pour afficher tous les appartenance au rôle de serveur nécessite le **VIEW DEFINITION ON SERVER ROLE** autorisation ou l’appartenance dans le **securityadmin** rôle serveur fixe.  
  
 Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les noms et ID des rôles et de leurs membres.  
  
```  
SELECT sys.server_role_members.role_principal_id, role.name AS RoleName,   
    sys.server_role_members.member_principal_id, member.name AS MemberName  
FROM sys.server_role_members  
JOIN sys.server_principals AS role  
    ON sys.server_role_members.role_principal_id = role.principal_id  
JOIN sys.server_principals AS member  
    ON sys.server_role_members.member_principal_id = member.principal_id;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
