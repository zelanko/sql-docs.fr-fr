---
description: REVOKE - Révoquer des autorisations sur des informations d’identification délimitées à la base de données (Transact-SQL)
title: REVOKE - Révoquer des autorisations sur des informations d’identification délimitées à la base de données (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- REVOKE DATABASE SCOPED CREDENTIAL
- REVOKE_DATABASE_SCOPED_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statements, database scoped credentials
- revoking permissions [SQL Server], database scoped credentials
ms.assetid: b73233c5-9afa-48ca-ba34-a9f86b9b1d2e
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8bc8760b678391b2bee7cf96d6e1b0e1e0c317a6
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88496574"
---
# <a name="revoke-database-scoped-credential-transact-sql"></a>REVOKE - Révoquer des autorisations sur des informations d’identification délimitées à la base de données (Transact-SQL)
[!INCLUDE[sqlserver2017-asdb](../../includes/applies-to-version/sqlserver2017-asdb.md)]

  Permet de révoquer des autorisations sur des informations d’identification délimitées à la base de données.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
  
REVOKE [ GRANT OPTION FOR ] permission  [ ,...n ]   
    ON DATABASE SCOPED CREDENTIAL :: credential_name   
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 GRANT OPTION FOR  
 Indique que la possibilité d'accorder l'autorisation spécifiée sera révoquée. L'autorisation elle-même ne sera pas révoquée.  
  
> [!IMPORTANT]  
>  Si le principal possède l'autorisation spécifiée sans l'option GRANT, l'autorisation elle-même sera révoquée.  
  
 *permission*  
 Spécifie une autorisation qui peut être révoquée sur des informations d’identification délimitées à la base de données. Voir ci-dessous.  
  
 ON CERTIFICATE **::** _credential_name_  
 Spécifie les informations d’identification délimitées à la base de données sur lesquelles l’autorisation est révoquée. Le qualificateur d'étendue "::" est indispensable.  
  
 *database_principal*  
 Spécifie le principal pour lequel l'autorisation est révoquée. Celui-ci peut avoir l'une des valeurs suivantes :  
  
-   d'un utilisateur de base de données ;  
  
-   d'un rôle de base de données ;  
  
-   d'un rôle d'application ;  
  
-   d'un utilisateur de base de données mappé sur une connexion Windows ;  
  
-   d'un utilisateur de base de données mappé sur un groupe Windows ;  
  
-   d'un utilisateur de base de données mappé sur un certificat ;  
  
-   d'un utilisateur de base de données mappé à une clé asymétrique ;  
  
-   d'un utilisateur de base de données qui n'est pas mappé sur le principal d'un serveur.  
  
 CASCADE  
 Indique que l'autorisation en cours de révocation est également révoquée sur les principaux auxquels elle a été accordée par ce principal.  
  
> [!CAUTION]  
>  Une révocation en cascade d'une autorisation accordée avec l'option WITH GRANT OPTION entraîne la révocation des deux options GRANT et DENY de cette autorisation.  
  
 AS *revoking_principal*  
 Spécifie un principal dont le principal qui exécute cette requête dérive son droit de révoquer l'autorisation. Celui-ci peut avoir l'une des valeurs suivantes :  
  
-   d'un utilisateur de base de données ;  
  
-   d'un rôle de base de données ;  
  
-   d'un rôle d'application ;  
  
-   d'un utilisateur de base de données mappé sur une connexion Windows ;  
  
-   d'un utilisateur de base de données mappé sur un groupe Windows ;  
  
-   d'un utilisateur de base de données mappé sur un certificat ;  
  
-   d'un utilisateur de base de données mappé à une clé asymétrique ;  
  
-   d'un utilisateur de base de données qui n'est pas mappé sur le principal d'un serveur.  
  
## <a name="remarks"></a>Remarques  
 Les informations d’identification délimitées à la base de données sont des éléments sécurisables au niveau base de données inclus dans la base de données qui est son parent dans la hiérarchie des autorisations. Les autorisations les plus spécifiques et limitées qui peuvent être révoquées sur des informations d’identification délimitées à la base de données sont indiquées ci-dessous, avec les autorisations plus générales qui les incluent implicitement.  
  
|Autorisation sur des informations d’identification délimitées à la base de données|Implicite avec l’autorisation sur les informations d’identification délimitées à la base de données|Impliquée par une autorisation de base de données|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation CONTROL sur les informations d’identification délimitées à la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)      
 [GRANT - Accorder des autorisations sur les informations d’identification délimitées à la base de données (Transact-SQL)](../../t-sql/statements/grant-database-scoped-credential-transact-sql.md)   
 [DENY - Refuser des autorisations sur des informations d’identification délimitées à la base de données (Transact-SQL)](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
