---
title: DENY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/15/2017
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
- DENY
- DENY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- schema-level securables [SQL Server]
- security [SQL Server], denying access
- DENY statement
- permissions [SQL Server], denying
- server-level securables [SQL Server]
- inherited security settings [SQL Server]
- denying permissions [SQL Server], DENY statement
- principal security [SQL Server]
- database-level securables [SQL Server]
- denying permissions [SQL Server]
ms.assetid: c32d1e01-9ee9-4665-a516-fcfece58078e
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 08f2d3c555dceef71e331b6df8727afb5780b86b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="deny-transact-sql"></a>DENY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Refuse une autorisation à un principal. Empêche ce principal d'hériter de l'autorisation par ses appartenances à des groupes ou à des rôles. DENY a priorité sur toutes les autorisations, à ceci près que DENY ne s’applique pas aux propriétaires d’objets ou les membres du rôle serveur fixe sysadmin.
  **Note de sécurité** membres du rôle sysadmin du rôle serveur fixe et les propriétaires d’objets ne peut pas être refusées. »
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for DENY  
DENY   { ALL [ PRIVILEGES ] } 
     | <permission>  [ ( column [ ,...n ] ) ] [ ,...n ]  
    [ ON [ <class> :: ] securable ] 
    TO principal [ ,...n ]   
    [ CASCADE] [ AS principal ]  
[;]

<permission> ::=  
{ see the tables below }  
  
<class> ::=  
{ see the tables below }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DENY   
    <permission> [ ,...n ]  
    [ ON [ <class_> :: ] securable ]   
    TO principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class> ::=  
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
 ALL  
 Cette option n'interdit pas toutes les autorisations possibles. Cette option revient à interdire les autorisations suivantes.  
  
-   Si l'élément sécurisable est une base de données, ALL représente BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE et CREATE VIEW.  
  
-   Si l'élément sécurisable est une fonction scalaire, ALL représente EXECUTE et REFERENCES.  
  
-   Si l'élément sécurisable est une fonction table, ALL représente DELETE, INSERT, REFERENCES, SELECT et UPDATE.  
  
-   Si l'élément sécurisable est une procédure stockée, ALL représente EXECUTE.  
  
-   Si l'élément sécurisable est une table, ALL représente DELETE, INSERT, REFERENCES, SELECT et UPDATE.  
  
-   Si l'élément sécurisable est une vue, ALL représente DELETE, INSERT, REFERENCES, SELECT et UPDATE.  
  
> [!NOTE]  
>  La syntaxe DENY ALL est déconseillée. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Refusez des autorisations spécifiques à la place.  
  
 PRIVILEGES  
 Inclus pour la conformité aux normes ISO. Ne change pas le comportement de l'option ALL.  
  
 *autorisation*  
 Nom d'une autorisation. Les mappages valides des autorisations des éléments sécurisables sont décrits dans les sous-rubriques qui suivent.  
  
 *colonne*  
 Spécifie le nom de la colonne d'une table à laquelle les interdictions s'appliquent. Les parenthèses () sont requises.  
  
 *classe*  
 Indique la classe de l'élément sécurisable sur laquelle l'autorisation est refusée. Le qualificateur d’étendue **::** est requis.  
  
 *élément sécurisable*  
 Indique l'élément sécurisable sur lequel l'autorisation est refusée.  
  
 POUR *principal*  
 Est le nom d’un principal. Les principaux auxquels il est possible de refuser des autorisations sur un élément sécurisable varient en fonction de l'élément sécurisable. Voir les rubriques ci-dessous relatives aux éléments sécurisables pour connaître les combinaisons acceptées.  
  
 CASCADE  
 Indique que l'autorisation est refusée au principal spécifié et à tous les autres principaux auxquels le principal a accordé cette autorisation. Nécessaire lorsque le principal a l'autorisation avec l'option GRANT OPTION.  
  
 AS *principal*  
  Utilisez la clause principale pour indiquer que l’entité de sécurité enregistré comme le deniers de l’autorisation doit être un principal de la personne qui exécute l’instruction. Par exemple, supposons qu’utilisateur Marie est principal_id 12 et utilisateur Raul est 15 principal. Mary exécute `DENY SELECT ON OBJECT::X TO Steven WITH GRANT OPTION AS Raul;` maintenant la table sys.database_permissions indique que le grantor_prinicpal_id de l’instruction deny a 15 (Raul), même si l’instruction a été réellement exécutée par l’utilisateur 13 (Mary).
  
L’utilisation de, comme dans cette instruction n’implique pas la possibilité d’emprunter l’identité d’un autre utilisateur.  
  
## <a name="remarks"></a>Notes  
 La syntaxe complète de l'instruction DENY est complexe. Le diagramme de syntaxe ci-dessus a été simplifié pour attirer l'attention sur sa structure. La syntaxe complète du refus des autorisations sur des éléments sécurisables particuliers est décrite dans les rubriques ci-dessous.  
  
 DENY échoue si CASCADE n'est pas spécifié lors du refus d'une autorisation à un principal auquel cette autorisation a été accordée avec GRANT OPTION.  
  
 La procédure système stockée sp_helprotect répertorie les autorisations sur un élément sécurisable au niveau base de données.  
  
> [!CAUTION]  
>  Une instruction DENY de niveau table n'a pas la priorité sur une instruction GRANT de niveau colonne. Cette incohérence dans la hiérarchie des autorisations a été conservée pour des raisons de compatibilité descendante. Elle sera supprimée dans une version ultérieure.  
  
> [!CAUTION]  
>  Le refus de l'autorisation CONTROL sur une base de données refuse implicitement l'autorisation CONNECT sur la base de données. Un principal dont l'autorisation CONTROL est refusée sur une base de données ne pourra pas se connecter à cette base de données.  
  
> [!CAUTION]  
>  Le refus de l'autorisation CONTROL SERVER entraîne implicitement le refus de l'autorisation CONNECT SQL sur le serveur. Un principal auquel l'autorisation CONTROL SERVER est refusée sur un serveur ne pourra pas se connecter à ce serveur.  
  
## <a name="permissions"></a>Permissions  
 L'appelant (ou le principal spécifié avec l'option AS) doit avoir l'autorisation CONTROL sur l'élément sécurisable ou une autorisation plus élevée qui implique cette autorisation. Si vous utilisez l'option AS, le principal spécifié doit être propriétaire de l'élément sécurisable auquel l'autorisation est refusée.  
  
 Les détenteurs de l'autorisation CONTROL SERVER, tels que les membres du rôle de serveur fixe sysadmin, peuvent refuser une autorisation sur n'importe quel élément sécurisable du serveur. Les détenteurs de l'autorisation CONTROL sur la base de données, tels que les membres du rôle de base de données fixe db_owner, peuvent refuser une autorisation sur n'importe quel élément sécurisable de la base de données. Les détenteurs de l'autorisation CONTROL sur un schéma peuvent refuser une autorisation sur n'importe quel objet dans ce schéma. Si vous utilisez la clause AS, le principal spécifié doit être propriétaire de l'élément sécurisable auquel les autorisations sont refusées.  
  
## <a name="examples"></a>Exemples  
 Le tableau suivant répertorie les éléments sécurisables et les rubriques qui décrivent la syntaxe spécifique à l’élément sécurisable.  
  
|||  
|-|-|  
|Rôle d'application|[REFUSER des autorisations de Principal de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Assembly|[REFUSER des autorisations sur un Assembly &#40; Transact-SQL &#41;](../../t-sql/statements/deny-assembly-permissions-transact-sql.md)|  
|Clé asymétrique|[REFUSER des autorisations de clé asymétrique &#40; Transact-SQL &#41;](../../t-sql/statements/deny-asymmetric-key-permissions-transact-sql.md)|  
|Groupe de disponibilité|[REFUSER des autorisations de groupe de disponibilité &#40; Transact-SQL &#41;](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)|  
|Certificat|[REFUSER des autorisations de certificats &#40; Transact-SQL &#41;](../../t-sql/statements/deny-certificate-permissions-transact-sql.md)|  
|Contrat|[REFUSER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Base de données|[REFUSER des autorisations de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-permissions-transact-sql.md)|  
|Étendue de la base de données d’informations d’identification|[REFUSER l’étendue de la base de données d’informations d’identification (Transact-SQL)](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)|  
|Point de terminaison|[REFUSER des autorisations de point de terminaison &#40; Transact-SQL &#41;](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)|  
|Catalogue de texte intégral|[REFUSER des autorisations de recherche en texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/deny-full-text-permissions-transact-sql.md)|  
|Liste de mots vides de texte intégral|[REFUSER des autorisations de recherche en texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/deny-full-text-permissions-transact-sql.md)|  
|Fonction|[REFUSER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Connexion|[REFUSER des autorisations de Principal de serveur &#40; Transact-SQL &#41;](../../t-sql/statements/deny-server-principal-permissions-transact-sql.md)|  
|Type de message|[REFUSER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Objet|[REFUSER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|File d'attente|[REFUSER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Liaisons de service distant|[REFUSER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Rôle|[REFUSER des autorisations de Principal de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Itinéraire|[REFUSER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|schéma|[REFUSER des autorisations sur les schémas &#40; Transact-SQL &#41;](../../t-sql/statements/deny-schema-permissions-transact-sql.md)|  
|Liste de propriétés de recherche|[REFUSER des autorisations de liste de propriétés de recherche &#40; Transact-SQL &#41;](../../t-sql/statements/deny-search-property-list-permissions-transact-sql.md)|  
|Server|[REFUSER des autorisations de serveur &#40; Transact-SQL &#41;](../../t-sql/statements/deny-server-permissions-transact-sql.md)|  
|Service|[REFUSER des autorisations au Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Procédure stockée|[REFUSER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Clé symétrique|[REFUSER des autorisations de clé symétrique &#40; Transact-SQL &#41;](../../t-sql/statements/deny-symmetric-key-permissions-transact-sql.md)|  
|Synonyme|[REFUSER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Objets système|[REFUSER des autorisations d’objet système &#40; Transact-SQL &#41;](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)|  
|Table|[REFUSER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Type|[REFUSER des autorisations de Type &#40; Transact-SQL &#41;](../../t-sql/statements/deny-type-permissions-transact-sql.md)|  
|Utilisateur|[REFUSER des autorisations de Principal de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Affichage|[REFUSER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Collection de schémas XML|[REFUSER des autorisations de Collection de schémas XML &#40; Transact-SQL &#41;](../../t-sql/statements/deny-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  

