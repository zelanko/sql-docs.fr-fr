---
title: ALTER AUTHORIZATION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_AUTHORIZATION_TSQL
- ALTER AUTHORIZATION
dev_langs:
- TSQL
helpviewer_keywords:
- owners [SQL Server], transferring
- modifying entity ownership
- full-text search [SQL Server], permissions
- owners [SQL Server], entities
- ALTER AUTHORIZATION statement
- entity ownership [SQL Server]
- transferring ownership
- search property lists [SQL Server], permissions
- TAKE OWNERSHIP
ms.assetid: 8c805ae2-91ed-4133-96f6-9835c908f373
caps.latest.revision: 84
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 31738dcb4eaf4676b4c0a34b13ee400e89333428
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-authorization-transact-sql"></a>ALTER AUTHORIZATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Change la propriété d'un élément sécurisable.    
    
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Syntaxe    
    
```    
-- Syntax for SQL Server  
ALTER AUTHORIZATION    
   ON [ <class_type>:: ] entity_name    
   TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::=    
    {    
        OBJECT | ASSEMBLY | ASYMMETRIC KEY | AVAILABILITY GROUP | CERTIFICATE     
      | CONTRACT | TYPE | DATABASE | ENDPOINT | FULLTEXT CATALOG     
      | FULLTEXT STOPLIST | MESSAGE TYPE | REMOTE SERVICE BINDING    
      | ROLE | ROUTE | SCHEMA | SEARCH PROPERTY LIST | SERVER ROLE     
      | SERVICE | SYMMETRIC KEY | XML SCHEMA COLLECTION    
    }    
```    

```
-- Syntax for SQL Database  
  
ALTER AUTHORIZATION    
   ON [ <class_type>:: ] entity_name    
   TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::=    
    {    
      OBJECT | ASSEMBLY | ASYMMETRIC KEY | CERTIFICATE     
    | TYPE | DATABASE | FULLTEXT CATALOG     
    | FULLTEXT STOPLIST     
    | ROLE | SCHEMA | SEARCH PROPERTY LIST     
    | SYMMETRIC KEY | XML SCHEMA COLLECTION    
    }    
```    

    
```    
-- Syntax for Azure SQL Data Warehouse  
  
ALTER AUTHORIZATION ON    
    [ <class_type> :: ] <entity_name>     
    TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::= {    
      SCHEMA     
    | OBJECT     
}    
    
<entity_name> ::=    
{    
      schema_name    
    | [ schema_name. ] object_name    
}    
```    
    
```    
-- Syntax for Parallel Data Warehouse  
  
ALTER AUTHORIZATION ON    
    [ <class_type> :: ] <entity_name>     
    TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::= {    
      DATABASE     
    | SCHEMA     
    | OBJECT     
}    
    
<entity_name> ::=    
{    
      database_name 
    | schema_name    
    | [ schema_name. ] object_name    
}    
```    
    
## <a name="arguments"></a>Arguments    
\<class_type > est la classe sécurisable de l’entité pour laquelle le propriétaire est en cours de modification. OBJECT est la valeur par défaut.    
    
|||    
|-|-|    
|OBJECT|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], entrepôt de données SQL Azure, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|    
|ASSEMBLY|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|ASYMMETRIC KEY|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|AVAILABILITY GROUP |**S’applique à**: SQL Server 2012 via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|CERTIFICATE|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|CONTRACT|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|DATABASE|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Pour plus d’informations, consultez [ALTER AUTHORIZATION pour les bases de données](#AlterDB) section ci-dessous.|    
|ENDPOINT|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|FULLTEXT CATALOG|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|FULLTEXT STOPLIST|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|MESSAGE TYPE|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|REMOTE SERVICE BINDING|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|ROLE|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|ROUTE|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SCHEMA|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], entrepôt de données SQL Azure, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|    
|SEARCH PROPERTY LIST|**S’applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|SERVER ROLE|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SERVICE|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|    
|SYMMETRIC KEY|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|TYPE|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
|XML SCHEMA COLLECTION|**S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|    
    
 *nom_entité*    
 Nom de l'entité.    
    
 *principal_name* | PROPRIÉTAIRE DU SCHÉMA    
 Nom du principal de sécurité qui possède l'entité. Les objets de bases de données doivent appartenir à un principal de base de données, un utilisateur de base de données ou un rôle. Les objets serveur (par exemple les bases de données) doivent appartenir à un principal serveur (un identifiant de connexion). Spécifiez **propriétaire du schéma** comme le *principal_name* pour indiquer que l’objet doit être possédé par le principal qui possède le schéma de l’objet.    
    
## <a name="remarks"></a>Notes    
 ALTER AUTHORIZATION peut s'utiliser pour modifier la propriété d'une entité qui a un propriétaire. La propriété d'entités contenues dans une base de données peut être transférée à n'importe quel principal de niveau base de données. La propriété d'entités de niveau serveur peut être transférée à n'importe quel principal de niveau serveur.    
    
> [!IMPORTANT]    
>  À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], un utilisateur peut être propriétaire d'un OBJECT ou d'un TYPE contenu dans un schéma appartenant à un autre utilisateur de base de données. Il s'agit là d'une différence par rapport aux versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [OBJECTPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/objectproperty-transact-sql.md) et [TYPEPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/typeproperty-transact-sql.md).    
    
 La propriété des entités suivantes, contenues dans un schéma et de type « objet » peut être transférée : tables, vues, fonctions, procédures, files d'attente et synonymes.    
    
 La propriété des entités suivantes ne peut pas être transférée : serveurs liés, statistiques, contraintes, règles, valeurs par défaut, déclencheurs, files d'attente [!INCLUDE[ssSB](../../includes/sssb-md.md)], informations d'identification, fonctions de partition, schémas de partition, clés principales de base de données, clé principale de service et notifications d'événements.    
    
 La propriété des membres des classes sécurisables suivantes ne peut pas être transférée : serveur, connexion, utilisateur, rôle d'application et colonne.    
    
 L'option SCHEMA OWNER n'est valide que lorsque vous transférez la propriété d'une entité contenue dans un schéma. SCHEMA OWNER transférera la propriété de l'entité au propriétaire du schéma dans lequel elle réside. Seules les entités des classes OBJECT, TYPE ou XML SCHEMA COLLECTION sont contenues dans des schémas.    
    
 Si l'entité cible n'est pas une base de données et que l'entité est transférée à un nouveau propriétaire, toutes les autorisations de la cible seront supprimées.    
    
> [!CAUTION]    
>  Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], le comportement des schémas n'est pas le même que dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un code qui suppose que les schémas sont équivalents aux utilisateurs de base de données peut retourner des résultats incorrects. Anciens affichages catalogue, notamment sysobjects, ne doivent pas être utilisés dans une base de données où une des DDL suivantes instructions a été utilisée : CREATE SCHEMA, ALTER SCHEMA, DROP SCHEMA, CREATE USER, ALTER USER, DROP USER, CREATE ROLE, ALTER ROLE, DROP ROLE, CREATE APPROLE, ALTER APPROLE, DROP APPROLE, ALTER AUTHORIZATION. Dans une base de données où une de ces instructions a été utilisée, vous devez recourir aux nouveaux affichages catalogue. Les nouveaux affichages catalogue prennent en compte la séparation des principaux et des schémas introduite dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour plus d’informations sur les affichages catalogue, consultez [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).    
    
 En outre, notez les points suivants :    
    
> [!IMPORTANT]    
>  La seule méthode fiable pour rechercher le propriétaire d’un objet est de requête le **sys.objects** affichage catalogue. La seule méthode fiable pour rechercher le propriétaire d'un type est d'utiliser la fonction TYPEPROPERTY.    
    
## <a name="special-cases-and-conditions"></a>Cas particuliers et conditions    
 Le tableau suivant récapitule les cas particuliers, les exceptions et les conditions qui s'appliquent à l'autorisation de modification.    
    
|Classe|Condition|    
|-----------|---------------|    
|OBJECT|Impossible de modifier la propriété des déclencheurs, des contraintes, des règles, des valeurs par défaut, des statistiques, des objets système, des files d'attente, des vues indexées ou des tables avec des vues indexées.|    
|SCHEMA|Lors d'un transfert de propriété, les autorisations sur des objets contenus dans des schémas n'ayant pas de propriétaires explicites seront supprimées. Impossible de modifier le propriétaire de sys, dbo ou information_schema.|    
|TYPE|Impossible de modifier le propriétaire d'un TYPE qui appartient à sys ou information_schema.|    
|CONTRACT, MESSAGE TYPE ou SERVICE|Impossible de modifier la propriété des entités système.|    
|SYMMETRIC KEY|Impossible de modifier la propriété des clés temporaires globales.|    
|CERTIFICATE ou ASYMMETRIC KEY|Impossible de transférer la propriété de ces entités vers un rôle ou un groupe.|    
|ENDPOINT|Le principal doit être une connexion.|    
  
## <a name="AlterDB"></a>AUTORISATION de modifier des bases de données  
**S’APPLIQUE À**: [!INCLUDE[ssSQL15](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
### <a name="for-sql-server"></a>Pour SQL Server :  
**Configuration requise pour le nouveau propriétaire :**   
La nouvelle entité de sécurité propriétaire doit être une des opérations suivantes :  
-   Une connexion d’authentification SQL Server.  
-   Une connexion d’authentification Windows qui représente un utilisateur Windows (et non un groupe).  
-   Un utilisateur Windows qui s’authentifie via une connexion d’authentification Windows qui représente un groupe Windows.  
  
**Configuration requise pour la personne qui exécute l’instruction ALTER AUTHORIZATION :**  
Si vous n’êtes pas un membre de la **sysadmin** rôle serveur fixe, vous devez avoir au moins l’autorisation TAKE OWNERSHIP sur la base de données et doit avoir l’autorisation IMPERSONATE sur le nouveau compte de connexion du propriétaire.   

### <a name="for-azure-sql-database"></a>Pour la base de données SQL Azure :  
**Configuration requise pour le nouveau propriétaire :**   
La nouvelle entité de sécurité propriétaire doit être une des opérations suivantes :  
-   Une connexion d’authentification SQL Server.  
-   Un utilisateur fédéré (pas un groupe) présent dans Azure AD.  
-   Un utilisateur géré (pas un groupe) ou une application dans Azure AD.    

> [!NOTE]  
> Si le nouveau propriétaire est un utilisateur Azure Active Directory, il ne peut pas exister en tant qu’utilisateur dans la base de données dans lequel le nouveau propriétaire sera le nouveau propriétaire. Ces utilisateurs Azure AD doit tout d’abord supprimé à partir de la base de données avant d’exécuter l’instruction ALTER AUTHORIZATION la modification de la propriété de base de données au nouvel utilisateur. Pour plus d’informations sur la configuration d’un utilisateur Azure Active Directory avec la base de données SQL, consultez [la connexion à la base de données SQL ou SQL données entrepôt par à l’aide d’authentification Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).   
  
**Configuration requise pour la personne qui exécute l’instruction ALTER AUTHORIZATION :**  
Vous devez vous connecter à la base de données cible pour changer le propriétaire de cette base de données.  

Les types de comptes suivants peuvent changer le propriétaire d’une base de données. 
* La connexion du principal au niveau du service. (L’administrateur de SQL Azure configuré lorsque le serveur logique a été créé.)  
* L’administrateur Azure Active Directory pour le serveur SQL Azure.   
* Le propriétaire actuel de la base de données.   
 
  
Le tableau suivant résume les conditions requises :  
  
Exécuteur  |Cible  |Résultat    
---------|---------|---------  
Connexion de l’authentification SQL Server     |Connexion de l’authentification SQL Server         |Réussi  
Connexion de l’authentification SQL Server     |Utilisateur AD Azure         |Échec           
Utilisateur AD Azure     |Connexion de l’authentification SQL Server         |Réussi           
Utilisateur AD Azure     |Utilisateur AD Azure         |Réussi           
  
Pour vérifier un propriétaire d’Azure AD de la base de données exécuter la commande Transact-SQL suivante dans une base de données utilisateur (dans cet exemple `testdb`).  
    
```    
SELECT CAST(owner_sid as uniqueidentifier) AS Owner_SID   
FROM sys.databases   
WHERE name = 'testdb';  
```    
    
Le résultat sera un identificateur (par exemple, 6D8B81F6-7C79-444C-8858-4AF896C03C67) qui correspond à Azure AD ObjectID est assigné à`richel@cqclinic.onmicrosoft.com`  
Lorsqu’un utilisateur de connexion d’authentification SQL Server est propriétaire de base de données, exécutez l’instruction suivante dans la base de données master pour vérifier le propriétaire de la base de données :  
    
```    
SELECT d.name, d.owner_sid, sl.name   
FROM sys.databases AS d  
JOIN sys.sql_logins AS sl  
ON d.owner_sid = sl.sid;  
    
```    
  
### <a name="best-practice"></a>Meilleure pratique  
  
Au lieu d’utiliser les utilisateurs Azure AD en tant que propriétaires individuels de la base de données, utilisez un groupe Azure AD en tant que membre de la **db_owner** rôle de base de données fixe. Les étapes suivantes montrent comment configurer une connexion désactivée en tant que propriétaire de la base de données et de rendre un groupe Azure Active Directory (`mydbogroup`) un membre de la **db_owner** rôle. 
1.  Connexion à SQL Server en tant qu’administrateur d’Azure AD et de changer le propriétaire de la base de données pour une connexion d’authentification SQL Server désactivée. Par exemple, à partir de la base de données utilisateur exécutez :  
  ```    
  ALTER AUTHORIZATION ON database::testdb TO DisabledLogin;  
  ```    
2.  Créer un groupe Azure AD doit propriétaire de la base de données et l’ajouter en tant qu’utilisateur à la base de données utilisateur. Exemple :  
  ```    
  CREATE USER [mydbogroup] FROM EXTERNAL PROVIDER;  
  ```    
3.  Dans la base de données utilisateur, ajoutez l’utilisateur qui représente le groupe d’Azure AD, à la **db_owner** rôle de base de données fixe. Exemple :  
  ```    
  ALTER ROLE db_owner ADD MEMBER mydbogroup;  
  ```    
  
Maintenant le `mydbogroup` membres peuvent gérer de manière centralisée la base de données en tant que membres de la **db_owner** rôle.  
- Lorsque les membres de ce groupe sont supprimés du groupe d’Azure AD, ils perdent automatiquement les autorisations dbo pour cette base de données.  
- Même si de nouveaux membres sont ajoutés à `mydbogroup` groupe Azure AD, ils d’accéder automatiquement le dbo de cette base de données.  
  
Pour vérifier si un utilisateur a l’autorisation effective dbo, inviter l’utilisateur à exécuter l’instruction suivante :  
    
```    
SELECT IS_MEMBER ('db_owner');  
```    
  
Une valeur de retour de 1 indique que l’utilisateur est membre du rôle.  
   
    
## <a name="permissions"></a>Permissions    
 Il faut obligatoirement l'autorisation TAKE OWNERSHIP sur l'entité. Si le nouveau propriétaire n'est pas l'utilisateur qui exécute cette instruction, il faut aussi soit 1) l'autorisation IMPERSONATE sur le nouveau propriétaire s'il s'agit d'un utilisateur ou d'une connexion, soit 2) si le nouveau propriétaire est un rôle, l'appartenance à ce rôle ou l'autorisation ALTER sur le rôle, soit 3) si le nouveau propriétaire est un rôle d'application, l'autorisation ALTER sur le rôle d'application.    
    
## <a name="examples"></a>Exemples    
    
### <a name="a-transfer-ownership-of-a-table"></a>A. Transfert de la propriété d'une table    
 L'exemple suivant transfère la propriété de la table `Sprockets` à l'utilisateur `MichikoOsada`. La table se trouve dans le schéma `Parts`.    
    
```    
ALTER AUTHORIZATION ON OBJECT::Parts.Sprockets TO MichikoOsada;    
GO    
```    
    
 La requête peut aussi se présenter de la façon suivante :    
    
```    
ALTER AUTHORIZATION ON Parts.Sprockets TO MichikoOsada;    
GO    
```    
    
 Si le schéma d’objets n’est pas inclus dans le cadre de l’instruction, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] recherche l’objet dans le schéma par défaut aux utilisateurs. Exemple :    
    
```    
ALTER AUTHORIZATION ON Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::Sprockets TO MichikoOsada;    
```    
    
### <a name="b-transfer-ownership-of-a-view-to-the-schema-owner"></a>B. Transfert de la propriété d'une vue au propriétaire du schéma    
 L'exemple suivant transfère la propriété de la vue `ProductionView06` au propriétaire du schéma qui la contient. La vue se trouve dans le schéma `Production`.    
    
```    
ALTER AUTHORIZATION ON OBJECT::Production.ProductionView06 TO SCHEMA OWNER;    
GO    
```    
    
### <a name="c-transfer-ownership-of-a-schema-to-a-user"></a>C. Transfert de la propriété d'un schéma à un utilisateur    
 L'exemple suivant transfère la propriété du schéma `SeattleProduction11` à l'utilisateur `SandraAlayo`.    
    
```    
ALTER AUTHORIZATION ON SCHEMA::SeattleProduction11 TO SandraAlayo;    
GO    
```    
    
### <a name="d-transfer-ownership-of-an-endpoint-to-a-sql-server-login"></a>D. Transfert de la propriété d'un point de terminaison à un compte de connexion SQL Server    
 L'exemple suivant transfère la propriété du point de terminaison `CantabSalesServer1` à `JaePak`. Comme le point de terminaison est un élément sécurisable au niveau serveur, il ne peut être transféré qu'à un principal au niveau du serveur.    
    
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].    
    
```    
ALTER AUTHORIZATION ON ENDPOINT::CantabSalesServer1 TO JaePak;    
GO    
```    
    
### <a name="e-changing-the-owner-of-a-table"></a>E. La modification du propriétaire d’une table    
 Chacun des exemples suivants modifie le propriétaire de la `Sprockets` de table dans le `Parts` base de données à l’utilisateur de base de données `MichikoOsada`.    
```    
ALTER AUTHORIZATION ON Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON dbo.Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::dbo.Sprockets TO MichikoOsada;    
```    
    
### <a name="f-changing-the-owner-of-a-database"></a>F. Modification du propriétaire d’une base de données    
 **S’applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].    
    
 L’exemple suivant modifier le propriétaire de la `Parts` base de données à la connexion `MichikoOsada`.    
    
```    
ALTER AUTHORIZATION ON DATABASE::Parts TO MichikoOsada;    
```    
  
### <a name="g-changing-the-owner-of-a-sql-database-to-an-azure-ad-user"></a>G. Changement de propriétaire d’une base de données SQL à un utilisateur d’Azure AD  
Dans l’exemple suivant, un administrateur d’Azure Active Directory pour SQL Server dans une organisation avec un annuaire active directory nommé `cqclinic.onmicrosoft.com`, peut modifier la propriété de base de données `targetDB` et faire d’un utilisateur d’AAD `richel@cqclinic.onmicorsoft.com` le nouveau propriétaire de base de données à l’aide de la commande suivante :  
    
```    
ALTER AUTHORIZATION ON database::targetDB TO [rachel@cqclinic.onmicrosoft.com];   
```    
    
 Notez que les crochets autour du nom d’utilisateur doivent être utilisés pour les utilisateurs Azure AD.  
  
    
## <a name="see-also"></a>Voir aussi    
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)     
 [TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)     
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)    
 

