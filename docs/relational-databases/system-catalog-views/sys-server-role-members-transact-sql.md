---
title: Sys.server_role_members (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- server_role_members
- sys.server_role_members_TSQL
- server_role_members_TSQL
- sys.server_role_members
dev_langs: TSQL
helpviewer_keywords: sys.server_role_members catalog view
ms.assetid: efa20414-2c6b-45a2-a7a9-60110a24da18
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dd26b9ea6419e17df0e318fbffeaeee958c0c501
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysserverrolemembers-transact-sql"></a>sys.server_role_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Renvoie une ligne pour chaque membre de chaque rôle serveur fixe et défini par l'utilisateur.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|ID du principal de serveur du rôle.|  
|**member_principal_id**|**int**|ID du principal de serveur du membre.|  
  
 Pour ajouter ou supprimer l’appartenance au rôle de serveur, utilisez le [ALTER SERVER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-server-role-transact-sql.md)instruction.  
  
## <a name="permissions"></a>Permissions  
 Les connexions peuvent afficher leur propre appartenance au rôle de serveur et les principal_id des membres des rôles serveur fixes. Pour afficher tous les rôles de serveur nécessite le **VIEW DEFINITION ON SERVER ROLE** autorisation ou l’appartenance dans le **securityadmin** rôle serveur fixe.  
  
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
  
  
