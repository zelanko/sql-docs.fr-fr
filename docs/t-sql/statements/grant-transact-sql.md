---
title: GRANT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/12/2017
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
- GRANT_TSQL
- GRANT
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], GRANT statement
- schema-level securables [SQL Server]
- GRANT statement
- cross-database permissions
- GRANT statement, about GRANT statement
- server-level securables [SQL Server]
- database-level securables [SQL Server]
- permissions [SQL Server], granting
ms.assetid: a760c16a-4d2d-43f2-be81-ae9315f38185
caps.latest.revision: 64
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bb9bf548f042a4a6f41322fb789a2cd7e5b6bec9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="grant-transact-sql"></a>GRANT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Accorde des autorisations à un principal sur un élément sécurisable.  Le concept général consiste à accorder \<des autorisations > ON \<un objet > à \<certains utilisateurs, la connexion ou le groupe >. Pour obtenir une présentation générale d’autorisations, consultez [autorisations &#40; moteur de base de données &#41;](../../relational-databases/security/permissions-database-engine.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for GRANT  
GRANT { ALL [ PRIVILEGES ] }  
      | permission [ ( column [ ,...n ] ) ] [ ,...n ]  
      [ ON [ class :: ] securable ] TO principal [ ,...n ]   
      [ WITH GRANT OPTION ] [ AS principal ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
GRANT   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
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
 ALL  
 Cette option est déconseillée mais maintenue uniquement pour la compatibilité descendante. Elle n'accorde pas toutes les autorisations possibles. Elle revient à accorder les autorisations suivantes.  
  
-   Si l'élément sécurisable est une base de données, ALL représente BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE et CREATE VIEW.  
  
-   Si l'élément sécurisable est une fonction scalaire, ALL représente EXECUTE et REFERENCES.  
  
-   Si l'élément sécurisable est une fonction table, ALL représente DELETE, INSERT, REFERENCES, SELECT et UPDATE.  
  
-   Si l'élément sécurisable est une procédure stockée, ALL représente EXECUTE.  
  
-   Si l'élément sécurisable est une table, ALL représente DELETE, INSERT, REFERENCES, SELECT et UPDATE.  
  
-   Si l'élément sécurisable est une vue, ALL représente DELETE, INSERT, REFERENCES, SELECT et UPDATE.  
  
PRIVILEGES  
 Inclus pour la conformité aux normes ISO. Ne change pas le comportement de l'option ALL.  
  
*autorisation*  
 Nom d'une autorisation. Les mappages valides des autorisations des éléments sécurisables sont décrits dans les sous-rubriques qui suivent.  
  
*colonne*  
 Spécifie le nom de la colonne d'une table à laquelle les autorisations s'appliquent. Les parenthèses () sont requises.  
  
*classe*  
 Indique la classe de l'élément sécurisable sur laquelle l'autorisation est accordée. Le qualificateur d’étendue **::** est requis.  
  
*élément sécurisable*  
 Indique l'élément sécurisable sur lequel l'autorisation est accordée.  
  
POUR *principal*  
 Est le nom d’un principal. Les principaux auxquels il est possible d'accorder des autorisations sur un élément sécurisable varient en fonction de l'élément sécurisable. Voir les sous-rubriques ci-dessous pour connaître les combinaisons acceptées.  
  
GRANT OPTION  
 Indique que le détenteur de l'autorisation a également la possibilité d'accorder l'autorisation spécifiée à d'autres principaux.  
  
AS *principal*  
 Utilisez la clause principale pour indiquer que le principal enregistrées en tant que la personne qui accorde l’autorisation doit être un principal de la personne qui exécute l’instruction. Par exemple, supposons qu’utilisateur Marie est principal_id 12 et utilisateur Raul est 15 principal. Mary exécute `GRANT SELECT ON OBJECT::X TO Steven WITH GRANT OPTION AS Raul;` maintenant la table sys.database_permissions indique que le grantor_prinicpal_id a 15 (Raul), même si l’instruction a été réellement exécutée par l’utilisateur 13 (Mary).

À l’aide de la clause AS n’est généralement pas recommandé, sauf si vous devez définir explicitement la chaîne d’autorisation. Pour plus d’informations, consultez la **résumé de l’algorithme de vérification d’autorisation** section de [autorisations (moteur de base de données)](../../relational-databases/security/permissions-database-engine.md).

L’utilisation de, comme dans cette instruction n’implique pas la possibilité d’emprunter l’identité d’un autre utilisateur. 
  
## <a name="remarks"></a>Notes  
 La syntaxe complète de l'instruction GRANT est complexe. Le diagramme de syntaxe ci-dessus a été simplifié pour attirer l'attention sur sa structure. La syntaxe complète d'accord des autorisations sur des éléments sécurisables particuliers est décrite dans les rubriques ci-dessous.  
  
 L'instruction REVOKE peut s'utiliser pour supprimer des autorisations accordées et l'instruction DENY pour empêcher un principal d'obtenir une autorisation particulière au moyen d'une instruction GRANT.  
  
 L'accord d'une autorisation supprime l'option DENY ou REVOKE de cette autorisation sur l'élément sécurisable spécifié. Si la même autorisation est refusée dans une étendue plus élevée qui contient l'élément sécurisable, l'option DENY est prioritaire. Cependant, la révocation de l'autorisation accordée dans une étendue plus élevée n'est pas prioritaire.  
  
 Les autorisations au niveau base de données sont accordées sur l'étendue de la base de données spécifiée. Si un utilisateur a besoin d'autorisations sur des objets dans une autre base de données, créez le compte de l'utilisateur dans cette autre base de données ou autorisez le compte de l'utilisateur à accéder à la fois à cette autre base de données et à la base de données active.  
  
> [!CAUTION]  
>  Une instruction DENY de niveau table n'a pas la priorité sur une instruction GRANT de niveau colonne. Cette incohérence dans la hiérarchie des autorisations a été conservée pour des raisons de compatibilité descendante. Elle sera supprimée dans une version ultérieure.  
  
 La procédure système stockée sp_helprotect répertorie les autorisations sur un élément sécurisable au niveau base de données.  
  
## <a name="with-grant-option"></a>WITH GRANT OPTION  
 Le **GRANT** ... **AVEC l’OPTION GRANT** précise que le principal de sécurité reçoit l’autorisation est la possibilité d’accorder l’autorisation spécifiée à d’autres comptes de sécurité. Lorsque l’entité qui reçoit l’autorisation est un rôle ou un groupe Windows, le **AS** clause doit être utilisée lors de l’autorisation de l’objet doit être accordée aux utilisateurs qui ne sont pas membres du groupe ou du rôle. Étant donné que seul un utilisateur, au lieu d’un groupe ou du rôle peut exécuter un **GRANT** instruction, un membre spécifique du groupe ou du rôle doit utiliser le **AS** clause pour appeler explicitement l’appartenance de groupe ou de rôle lorsque vous accordez l’autorisation. L’exemple suivant montre comment la **WITH GRANT OPTION** est utilisé quand accordé à un rôle ou un groupe Windows.  
  
```  
-- Execute the following as a database owner  
GRANT EXECUTE ON TestProc TO TesterRole WITH GRANT OPTION;  
EXEC sp_addrolemember TesterRole, User1;  
-- Execute the following as User1  
-- The following fails because User1 does not have the permission as the User1  
GRANT EXECUTE ON TestMe TO User2;  
-- The following succeeds because User1 invokes the TesterRole membership  
GRANT EXECUTE ON TestMe TO User2 AS TesterRole;  
```  
  
## <a name="chart-of-sql-server-permissions"></a>Graphique des autorisations SQL Server  
 Pour obtenir un graphique de la taille d’une affiche de toutes les autorisations du [!INCLUDE[ssDE](../../includes/ssde-md.md)] au format PDF, consultez [http://go.microsoft.com/fwlink/?LinkId=229142](http://go.microsoft.com/fwlink/?LinkId=229142).  
  
## <a name="permissions"></a>Permissions  
 Le fournisseur d'autorisations (ou le principal spécifié avec l'option AS) doit posséder l'autorisation elle-même avec l'option GRANT OPTION ou une autorisation plus élevée qui implique l'autorisation accordée. En cas d'utilisation de l'option AS, d'autres critères s'appliquent. Pour plus d'informations, consultez la rubrique sur les éléments sécurisables.  
  
 Les propriétaires d'objets peuvent accorder des autorisations sur les objets qu'ils possèdent. Les principaux ayant l'autorisation CONTROL sur un élément sécurisable peuvent accorder une autorisation sur cet élément.  
  
 Les détenteurs de l'autorisation CONTROL SERVER, tels que les membres du rôle serveur fixe sysadmin, peuvent accorder une autorisation sur n'importe quel élément sécurisable du serveur. Les bénéficiaires de l'autorisation CONTROL sur une base de données, tels que les membres du rôle de base de données fixe db_owner, peuvent accorder une autorisation quelconque sur tout élément sécurisable inclus dans la base de données. Les détenteurs de l'autorisation CONTROL sur un schéma peuvent accorder une autorisation sur n'importe quel objet dans ce schéma.  
  
## <a name="examples"></a>Exemples  
 Le tableau suivant répertorie les éléments sécurisables et les rubriques qui décrivent la syntaxe spécifique à l’élément sécurisable.  
  
|||  
|-|-|  
|Rôle d'application|[ACCORDER des autorisations de Principal de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Assembly|[ACCORDER des autorisations sur un Assembly &#40; Transact-SQL &#41;](../../t-sql/statements/grant-assembly-permissions-transact-sql.md)|  
|Clé asymétrique|[ACCORDER des autorisations de clé asymétrique &#40; Transact-SQL &#41;](../../t-sql/statements/grant-asymmetric-key-permissions-transact-sql.md)|  
|Groupe de disponibilité|[Autorisations de groupe de disponibilité GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)|  
|Certificat|[Autorisations de certificat GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-certificate-permissions-transact-sql.md)|  
|Contrat|[Autorisations GRANT Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Base de données|[Les autorisations de base de données GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)|
|Étendue de la base de données d’informations d’identification|[Base de données de l’octroi d’une étendue d’informations d’identification (Transact-SQL)](../../t-sql/statements/grant-database-scoped-credential-transact-sql.md)|  
|Point de terminaison|[ACCORDER des autorisations de point de terminaison &#40; Transact-SQL &#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)|  
|Catalogue de texte intégral|[Les autorisations GRANT recherche en texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/grant-full-text-permissions-transact-sql.md)|  
|Liste de mots vides de texte intégral|[Les autorisations GRANT recherche en texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/grant-full-text-permissions-transact-sql.md)|  
|Fonction|[ACCORDER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Connexion|[ACCORDER des autorisations de Principal de serveur &#40; Transact-SQL &#41;](../../t-sql/statements/grant-server-principal-permissions-transact-sql.md)|  
|Type de message|[Autorisations GRANT Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Objet|[ACCORDER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|File d'attente|[ACCORDER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Liaisons de service distant|[Autorisations GRANT Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Rôle|[ACCORDER des autorisations de Principal de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Itinéraire|[Autorisations GRANT Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|schéma|[ACCORDER des autorisations sur les schémas &#40; Transact-SQL &#41;](../../t-sql/statements/grant-schema-permissions-transact-sql.md)|  
|Liste de propriétés de recherche|[Autorisations de liste de propriétés de recherche GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-search-property-list-permissions-transact-sql.md)|  
|Server|[Autorisations de serveur GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-server-permissions-transact-sql.md)|  
|Service|[Autorisations GRANT Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|Procédure stockée|[ACCORDER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Clé symétrique|[ACCORDER des autorisations de clé symétrique &#40; Transact-SQL &#41;](../../t-sql/statements/grant-symmetric-key-permissions-transact-sql.md)|  
|Synonyme|[ACCORDER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Objets système|[GRANT – octroi d’autorisations d’objet système &#40;Transact-SQL&#41;](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)|  
|Table|[ACCORDER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Type|[Type d’octroi des autorisations &#40; Transact-SQL &#41;](../../t-sql/statements/grant-type-permissions-transact-sql.md)|  
|Utilisateur|[ACCORDER des autorisations de Principal de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Affichage|[ACCORDER des autorisations d’objet &#40; Transact-SQL &#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Collection de schémas XML|[ACCORDER des autorisations de Collection de schémas XML &#40; Transact-SQL &#41;](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  

