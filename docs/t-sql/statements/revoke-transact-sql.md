---
title: REVOKE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVOKE_TSQL
- REVOKE
dev_langs:
- TSQL
helpviewer_keywords:
- schema-level securables [SQL Server]
- REVOKE statement, Transact-SQL syntax
- removing permissions
- server-level securables [SQL Server]
- deleting permissions
- revoking permissions [SQL Server]
- REVOKE statement
- denying permissions [SQL Server], removing
- database-level securables [SQL Server]
- granting permissions [SQL Server], removing
- permissions [SQL Server], revoking
- dropping permissions
ms.assetid: 9d31d3e7-0883-45cd-bf0e-f0361bbb0956
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa08be63c0d792ed1e0422860b55a0c8f2abdc8b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-transact-sql"></a>REVOKE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Supprime une autorisation accordée ou refusée antérieurement.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for REVOKE  
REVOKE [ GRANT OPTION FOR ]  
      {   
        [ ALL [ PRIVILEGES ] ]  
        |  
                permission [ ( column [ ,...n ] ) ] [ ,...n ]  
      }  
      [ ON [ class :: ] securable ]   
      { TO | FROM } principal [ ,...n ]   
      [ CASCADE] [ AS principal ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
REVOKE   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    [ FROM | TO ] principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class_type> ::=  
{  
      LOGIN  
    | DATABASE  
    | OBJECT  
    | ROLE  
    | SCHEMA  
    | USER  
}  
```  
  
## <a name="arguments"></a>Arguments  
 GRANT OPTION FOR  
 Indique que la possibilité d'accorder l'autorisation spécifiée sera révoquée. C'est obligatoire si vous utilisez l'argument CASCADE.  
  
> [!IMPORTANT]  
>  Si le principal possède l'autorisation spécifiée sans l'option GRANT, l'autorisation elle-même sera révoquée.  
  
 ALL  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Cette option ne révoque pas toutes les autorisations possibles. La révocation complète, ALL, équivaut à révoquer les autorisations suivantes.  
  
-   Si l'élément sécurisable est une base de données, ALL représente BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE et CREATE VIEW.  
  
-   Si l'élément sécurisable est une fonction scalaire, ALL représente EXECUTE et REFERENCES.  
  
-   Si l'élément sécurisable est une fonction table, ALL représente DELETE, INSERT, REFERENCES, SELECT et UPDATE.  
  
-   Si l'élément sécurisable est une procédure stockée, ALL représente EXECUTE.  
  
-   Si l'élément sécurisable est une table, ALL représente DELETE, INSERT, REFERENCES, SELECT et UPDATE.  
  
-   Si l'élément sécurisable est une vue, ALL représente DELETE, INSERT, REFERENCES, SELECT et UPDATE.  
  
> [!NOTE]  
>  La syntaxe REVOKE ALL est déconseillée. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Révoquez des autorisations spécifiques à la place.  
  
 PRIVILEGES  
 Inclus pour la conformité aux normes ISO. Ne change pas le comportement de l'option ALL.  
  
 *autorisation*  
 Nom d'une autorisation. Les mappages valides des autorisations aux éléments sécurisables sont décrits dans les rubriques répertoriées dans [syntaxe spécifique sécurisables](#securable) plus loin dans cette rubrique.  
  
 *colonne*  
 Spécifie le nom d'une colonne d'une table sur laquelle les autorisations sont révoquées. Les parenthèses sont obligatoires.  
  
 *classe*  
 Spécifie la classe de l'élément sécurisable sur lequel l'autorisation est révoquée. Le qualificateur d’étendue **::** est requis.  
  
 *élément sécurisable*  
 Spécifie l'élément sécurisable sur lequel l'autorisation est révoquée.  
  
 POUR | À partir de *principal*  
 Est le nom d’un principal. Les principaux d'où les autorisations portant sur un élément sécurisable peuvent être révoquées varient, selon cet élément sécurisable. Pour plus d’informations sur les combinaisons valides, consultez les rubriques répertoriées dans [syntaxe spécifique sécurisables](#securable) plus loin dans cette rubrique.  
  
 CASCADE  
 Indique que l'autorisation qui est révoquée l'est aussi à partir d'autres principaux auxquels elle a été accordée par ce principal. Lorsque vous utilisez l'argument CASCADE, vous devez également inclure l'argument GRANT OPTION FOR.  
  
> [!CAUTION]  
>  Une révocation en cascade d'une autorisation accordée avec l'option WITH GRANT OPTION entraîne la révocation des deux options GRANT et DENY de cette autorisation.  
  
 AS *principal*  
 Utilisez la clause principale pour indiquer que vous révoquez une autorisation qui a été accordée par une entité autre que vous. Par exemple, supposons qu’utilisateur Marie est principal_id 12 et utilisateur Raul est 15 principal. Mary et Raul accordent à qu'un utilisateur nommé Stéphane la même autorisation. La table sys.database_permissions indique les autorisations à deux reprises, mais ils auront chacun une valeur différente de grantor_prinicpal_id. Mary peut révoquer l’autorisation à l’aide de la `AS RAUL` clause pour supprimer l’allocation de Raul de l’autorisation.
 
L’utilisation de, comme dans cette instruction n’implique pas la possibilité d’emprunter l’identité d’un autre utilisateur.  
  
## <a name="remarks"></a>Notes  
 La syntaxe complète de l'instruction REVOKE est complexe. Le diagramme de syntaxe ci-dessus a été simplifié pour attirer l'attention sur sa structure. La syntaxe complète pour la révocation d’autorisations sur des éléments sécurisables spécifiques est décrite dans les rubriques répertoriées dans [syntaxe spécifique sécurisables](#securable) plus loin dans cette rubrique.  
  
 L'instruction REVOKE peut s'utiliser pour supprimer des autorisations accordées et l'instruction DENY pour empêcher un principal d'obtenir une autorisation particulière au moyen d'une instruction GRANT.  
  
 L'accord d'une autorisation supprime l'option DENY ou REVOKE de cette autorisation sur l'élément sécurisable spécifié. Si la même autorisation est refusée dans une étendue plus élevée qui contient l'élément sécurisable, l'option DENY est prioritaire. Toutefois, la révocation de l'autorisation accordée à une étendue supérieure ne devient pas prioritaire.  
  
> [!CAUTION]  
>  Une instruction DENY de niveau table n'a pas la priorité sur une instruction GRANT de niveau colonne. Cette incohérence dans la hiérarchie des autorisations a été conservée pour des raisons de compatibilité descendante. Elle sera supprimée dans une version ultérieure.  
  
 La procédure stockée système sp_helprotect répertorie les autorisations sur un élément sécurisable au niveau de la base de données.  
  
 L'instruction REVOKE échoue si l'argument CASCADE n'est pas spécifié lorsque vous révoquez une autorisation d'un principal auquel a été accordée cette autorisation avec GRANT OPTION spécifié.  
  
## <a name="permissions"></a>Permissions  
 Les principaux avec l'autorisation CONTROL sur un élément sécurisable peuvent révoquer l'autorisation sur cet élément sécurisable. Les propriétaires d'objets peuvent révoquer des autorisations sur les objets qu'ils possèdent.  
  
 Les bénéficiaires de l'autorisation CONTROL SERVER, par exemple les membres du rôle serveur fixe sysadmin, peuvent révoquer n'importe quelle autorisation sur n'importe quel élément sécurisable du serveur. Les bénéficiaires de l'autorisation CONTROL sur une base de données, par exemple les membres du rôle de base de données fixe db_owner, peuvent révoquer n'importe quelle autorisation sur n'importe quel élément sécurisable de la base de données. Les bénéficiaires de l'autorisation CONTROL sur un schéma peuvent révoquer n'importe quelle autorisation sur n'importe quel objet du schéma.  
  
##  <a name="securable"></a>Leur syntaxe  
 Le tableau suivant répertorie les éléments sécurisables et les rubriques qui décrivent la syntaxe spécifique à l’élément sécurisable.  
  
|Élément sécurisable|Rubrique|  
|---------------|-----------|  
|Rôle d'application|[RÉVOQUER les autorisations de Principal de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Assembly|[RÉVOQUER des autorisations sur un Assembly &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-assembly-permissions-transact-sql.md)|  
|Clé asymétrique|[RÉVOQUER les autorisations de clé asymétrique &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-asymmetric-key-permissions-transact-sql.md)|  
|Groupe de disponibilité|[Autorisations de groupe de disponibilité REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)|  
|Certificat|[RÉVOQUER les autorisations de certificats &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-certificate-permissions-transact-sql.md)|  
|Contrat|[RÉVOQUER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Base de données|[RÉVOQUER les autorisations de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-permissions-transact-sql.md)|  
|Point de terminaison|[RÉVOQUER les autorisations de point de terminaison &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)|  
|Étendue de la base de données d’informations d’identification|[Base de données de la révocation d’une étendue d’informations d’identification (Transact-SQL)](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)|  
|Catalogue de texte intégral|[RÉVOQUER les autorisations de recherche en texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|Liste de mots vides de texte intégral|[RÉVOQUER les autorisations de recherche en texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|Fonction|[RÉVOQUER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Connexion|[RÉVOQUER les autorisations du Principal de serveur &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-server-principal-permissions-transact-sql.md)|  
|Type de message|[RÉVOQUER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Objet|[RÉVOQUER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|File d'attente|[RÉVOQUER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Liaisons de service distant|[RÉVOQUER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Rôle|[RÉVOQUER les autorisations de Principal de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Itinéraire|[RÉVOQUER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|schéma|[RÉVOQUER des autorisations sur les schémas &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-schema-permissions-transact-sql.md)|  
|Liste de propriétés de recherche|[RÉVOQUER les autorisations de liste de propriétés de recherche &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-search-property-list-permissions-transact-sql.md)|  
|Server|[RÉVOQUER les autorisations de serveur &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-server-permissions-transact-sql.md)|  
|Service|[RÉVOQUER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|Procédure stockée|[RÉVOQUER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Clé symétrique|[RÉVOQUER les autorisations de clé symétrique &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-symmetric-key-permissions-transact-sql.md)|  
|Synonyme|[RÉVOQUER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Objets système|[Autorisations d’objet système REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)|  
|Table|[RÉVOQUER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Type|[RÉVOQUER les autorisations de Type &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-type-permissions-transact-sql.md)|  
|Utilisateur|[RÉVOQUER les autorisations de Principal de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Affichage|[RÉVOQUER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Collection de schémas XML|[RÉVOQUER les autorisations de Collection de schémas XML &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie des autorisations &#40;Moteur de base de données&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  

