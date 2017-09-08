---
title: "Le rôle ALTER (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_ROLE_TSQL
- ALTER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- modifying database roles
- ALTER ROLE statement
- renaming database roles
- database roles [SQL Server], modifying
- names [SQL Server], database roles
ms.assetid: e1e83caa-17cc-4871-b2db-2711339fb64f
caps.latest.revision: 64
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3eaee2d346eda964545caa60cd7168b531f47ad9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-role-transact-sql"></a>ALTER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ajoute ou supprime des membres vers ou à partir d’un rôle de base de données ou modifie le nom d’un rôle de base de données défini par l’utilisateur.  
  
> [!NOTE]  
>  Pour modifier les rôles dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez [sp_addrolemember &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) et [sp_droprolemember &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server (starting with 2012) and Azure SQL Database  
  
ALTER ROLE  role_name  
{  
       ADD MEMBER database_principal  
    |  DROP MEMBER database_principal  
    |  WITH NAME = new_name  
}  
[;]  
```  
  
 
```  
-- Syntax for SQL Server 2008 only  
  
-- Change the name of a user-defined database role  
ALTER ROLE role_name   
    WITH NAME = new_name  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *nom_rôle*  
 **S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (à partir de 2008),  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Spécifie le rôle de base de données à modifier.  
  
 Ajouter un membre *principal_base_de_données*l  
 **S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (à partir de 2012),  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Spécifie d’ajouter le principal de base de données à l’appartenance à un rôle de base de données.  
  
-   *principal_base_de_données* est un utilisateur de base de données ou un rôle de base de données défini par l’utilisateur.  
  
-   *principal_base_de_données* ne peut pas être un rôle de base de données fixe ou un principal de serveur.  
  
DROP MEMBER *principal_base_de_données*  
 **S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (à partir de 2012),  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Spécifie la suppression d’un principal de base de données à partir de l’appartenance à un rôle de base de données.  
  
-   *principal_base_de_données* est un utilisateur de base de données ou un rôle de base de données défini par l’utilisateur.  
  
-   *principal_base_de_données* ne peut pas être un rôle de base de données fixe ou un principal de serveur.  
  
AVEC NAME = *nouveau_nom*  
 **S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (à partir de 2008),  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Spécifie pour modifier le nom d’un rôle de base de données défini par l’utilisateur. Le nouveau nom ne doit pas déjà exister dans la base de données.  
  
 La modification du nom d'un rôle de base de données ne modifie pas le numéro d'identification, le propriétaire ou les autorisations du rôle.  
  
## <a name="permissions"></a>Permissions  
 Pour exécuter cette commande vous avez besoin d’un ou plusieurs de ces autorisations ou les appartenances :  
  
-   **ALTER** autorisation sur le rôle  
-   **ALTER ANY ROLE** autorisation sur la base de données  
-   L’appartenance à la **db_securityadmin** rôle de base de données fixe  
  
En outre, pour modifier l’appartenance à un rôle de base de données fixe, vous devez :  
  
-   L’appartenance à la **db_owner** rôle de base de données fixe  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Vous ne pouvez pas modifier le nom d’un rôle de base de données fixe.  
  
## <a name="metadata"></a>Métadonnées  
 Ces vues système contiennent des informations sur les rôles de base de données et des entités de base de données.  
  
-   [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)  
  
-   [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-change-the-name-of-a-database-role"></a>A. Modifier le nom d’un rôle de base de données  
 **S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (à partir de 2008),  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 L'exemple suivant remplace le nom du rôle `buyers` par `purchasing`. [!INCLUDE[AdWorks-example](../../includes/adworks-example-md.md)]  
  
```tsql  
ALTER ROLE buyers WITH NAME = purchasing;  
```  
  
### <a name="b-add-or-remove-role-members"></a>B. Ajouter ou supprimer des membres du rôle  
 **S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (à partir de 2012),  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 Cet exemple crée un rôle de base de données nommé `Sales`. Il ajoute un utilisateur de base de données nommé Barry à l’appartenance et montre ensuite comment supprimer le membre Barry. [!INCLUDE[AdWorks-example](../../includes/adworks-example-md.md)]  
  
```tsql  
CREATE ROLE Sales;  
ALTER ROLE Sales ADD MEMBER Barry;  
ALTER ROLE Sales DROP MEMBER Barry;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER un rôle &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [DROP ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  

