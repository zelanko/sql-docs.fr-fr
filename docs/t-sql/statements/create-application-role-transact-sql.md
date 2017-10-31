---
title: "CRÉER le rôle d’APPLICATION (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- APPLICATION_ROLE_TSQL
- CREATE APPLICATION ROLE
- sql13.swb.applicationrole.permissions.f1
- APPLICATION
- APPLICATION ROLE
- CREATE_APPLICATION_ROLE_TSQL
- APPLICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE APPLICATION ROLE statement
- application roles [SQL Server], creating
ms.assetid: 647386da-ee80-41cf-86c9-dd590f9d66b6
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 68f185c59672e4414192fc75dbb7bb137800d69f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-application-role-transact-sql"></a>CREATE APPLICATION ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ajoute un rôle d'application à la base de données active.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE APPLICATION ROLE application_role_name   
    WITH PASSWORD = 'password' [ , DEFAULT_SCHEMA = schema_name ]  
```  
  
## <a name="arguments"></a>Arguments  
 *application_role_name*  
 Indique le nom du rôle d'application. Ce nom ne doit pas être déjà utilisé pour référencer un principal dans la base de données.  
  
 Mot de passe **='***mot de passe***'**  
 Spécifie le mot de passe que les utilisateurs de base de données doivent utiliser pour activer le rôle d'application. Vous devez toujours utiliser des mots de passe forts. *mot de passe* doit remplir les conditions de stratégie de mot de passe Windows de l’ordinateur qui exécute l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 DEFAULT_SCHEMA  **=**  *schema_name*  
 Indique le premier schéma dans lequel le serveur doit effectuer des recherches lorsqu'il résout les noms des objets pour ce rôle. Si DEFAULT_SCHEMA n'est pas défini, le rôle d'application utilise DBO comme schéma par défaut. *schema_name* peut être un schéma qui n’existe pas dans la base de données.  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]  
>  La complexité des mots de passe est vérifiée lors de la définition des mots de passe des rôles d'application. Les applications qui appellent des rôles d'application doivent stocker leurs mots de passe. Les mots de passe des rôles d'application doivent toujours être stockés sous forme chiffrée.  
  
 Rôles d’application sont visibles dans le [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) affichage catalogue.  
  
 Pour plus d’informations sur l’utilisation des rôles d’application, consultez [les rôles d’Application](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER ANY APPLICATION ROLE sur la base de données.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous, un rôle d'application nommé `weekly_receipts` est créé, doté du mot de passe `987Gbv876sPYY5m23` et du schéma `Sales` par défaut.  
  
```  
CREATE APPLICATION ROLE weekly_receipts   
    WITH PASSWORD = '987G^bv876sPY)Y5m23'   
    , DEFAULT_SCHEMA = Sales;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles d’application](../../relational-databases/security/authentication-access/application-roles.md)   
 [sp_setapprole &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [ALTER APPLICATION ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [Stratégie de mot de passe](../../relational-databases/security/password-policy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

