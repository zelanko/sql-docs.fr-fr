---
title: "Les autorisations GRANT DENY REVOKE-Azure SQL Data et entrepôts de données en parallèle | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5a3b7424-408e-4cb0-8957-667ebf4596fc
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3c4beb3881b983c0af3add7671dc4c7155649497
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse"></a>Autorisations : GRANT, DENY et REVOKE (entrepôt de données SQL Azure, entrepôt de données en parallèle)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Utilisez [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] **GRANT** et **DENY** instructions pour accorder ou refuser une autorisation (tels que **mise à jour**) sur un élément sécurisable (par exemple, une base de données, table, vue, etc.) à un principal de sécurité (un compte de connexion, un utilisateur de base de données ou un rôle de base de données). Utilisez **RÉVOQUER** pour supprimer l’octroi ou de refus d’une autorisation.  
  
 Autorisations de niveau serveur sont appliquées aux connexions. Les autorisations de niveau base de données sont appliquées à des utilisateurs de base de données et les rôles de base de données.  
  
 Pour voir quelles autorisations ont été accordées et refusées, interrogez les vues sys.server_permissions et sys.database_permissions. Les autorisations qui ne sont pas explicitement accordées ou refusées à un principal de sécurité peuvent être héritées par ayant une appartenance à un rôle qui dispose des autorisations. Les autorisations des rôles de base de données fixe ne peut pas être modifiées et n’apparaissent pas dans les vues sys.server_permissions et sys.database_permissions.  
  
-   **GRANT** accorde explicitement une ou plusieurs autorisations.  
  
-   **DENY** refuse explicitement l’entité de sécurité de l’utilisation d’une ou plusieurs autorisations.  
  
-   **RÉVOQUER** supprime **GRANT** ou **DENY** autorisations.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
GRANT   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
[;]  
  
DENY   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
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
 \<autorisation > [ **,**... *n* ]  
 Une ou plusieurs autorisations à accorder, refuser ou révoquer.  
  
 ON [ \<class_type > ::] *sécurisable* le **ON** clause décrit le paramètre d’élément sécurisable auquel accorder, refuser ou révoquer des autorisations.  
  
 \<class_type > le type de classe de l’élément sécurisable. Cela peut être **connexion**, **base de données**, **objet**, **schéma**, **rôle**, ou **utilisateur**. Les autorisations peuvent également être accordées à la **SERVER***class_type*, mais **SERVER** n’est pas spécifié pour ces autorisations. **Base de données** n’est pas spécifié lorsque l’autorisation inclut le mot **base de données** (par exemple **ALTER ANY DATABASE**). Lorsqu’aucun *class_type* est spécifié et le type d’autorisation n’est pas limité sur le serveur ou de la classe de base de données, la classe est censée pour être **objet**.  
  
 *élément sécurisable*  
 Le nom de la connexion, de base de données, table, vue, schéma, procédure, rôle ou utilisateur auquel accorder, refuser ou révoquer des autorisations. Le nom de l’objet peut être spécifié avec les règles d’affectation des noms en trois parties qui sont décrites dans [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
 POUR *principal* [ **,**... *n* ]  
 Un ou plusieurs principaux accordées, refusées ou révoquées autorisations. Principal est le nom de connexion, l’utilisateur de base de données ou le rôle de base de données.  
  
 À partir de *principal* [ **,**... *n* ]  
 Un ou plusieurs principaux pour révoquer des autorisations à partir de.  Principal est le nom de connexion, l’utilisateur de base de données ou le rôle de base de données. **À partir de** peut uniquement être utilisé avec un **RÉVOQUER** instruction. **POUR** peut être utilisé avec **GRANT**, **DENY**, ou **RÉVOQUER**.  
  
 WITH GRANT OPTION  
 Indique que le détenteur de l'autorisation a également la possibilité d'accorder l'autorisation spécifiée à d'autres principaux.  
  
 CASCADE  
 Indique que l’autorisation est refusée ou révoquée pour le principal spécifié et à tous les autres principaux auxquels le principal de l’autorisation. Obligatoire lorsque le principal dispose de l’autorisation avec **l’option GRANT OPTION**.  
  
 GRANT OPTION FOR  
 Indique que la possibilité d'accorder l'autorisation spécifiée sera révoquée. Cela est nécessaire lorsque vous utilisez la **CASCADE** argument.  
  
> [!IMPORTANT]  
>  Si le principal possède l’autorisation spécifiée sans la **GRANT** option, l’autorisation elle-même sera révoquée.  
  
## <a name="permissions"></a>Permissions  
 Pour accorder une autorisation, le fournisseur d’autorisations doit avoir l’autorisation elle-même avec le **WITH GRANT OPTION**, ou doit avoir une autorisation plus élevée qui implique l’autorisation accordée.  Les propriétaires d'objets peuvent accorder des autorisations sur les objets qu'ils possèdent. Les principaux avec **contrôle** autorisation sur un élément sécurisable permettre accorder une autorisation sur cet élément sécurisable.  Membres de la **db_owner** et **db_securityadmin** des rôles de base de données fixe peuvent accorder une autorisation dans la base de données.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Ou le refus ou révocation d’autorisations à un principal n’affecte pas les demandes qui ont réussi d’autorisation et qui sont en cours d’exécution. Pour restreindre l’accès immédiatement, vous devez annuler les demandes actives ou arrêter des sessions en cours.  
  
> [!NOTE]  
>  La plupart des rôles de serveur ne sont pas disponibles dans cette version. Utilisez à la place des rôles de base de données défini par l’utilisateur. Les connexions ne peuvent pas être ajoutées à la **sysadmin** rôle serveur fixe. Octroi le **CONTROL SERVER** autorisation est une approximation de l’appartenance à la **sysadmin** rôle serveur fixe.  
  
 Certaines instructions requièrent plusieurs autorisations. Par exemple, pour créer une table requiert le **CREATE TABLE** autorisations dans la base de données et le **ALTER SCHEMA** autorisation pour la table qui contiendra la table.  
  
 PDW exécute parfois des procédures stockées pour distribuer les actions utilisateur pour les nœuds de calcul. Par conséquent, l’autorisation execute pour une base de données entière ne peut pas être refusée. (Par exemple `DENY EXECUTE ON DATABASE::<name> TO <user>;` échouera.) Pour contourner ce problème, refuser l’autorisation execute pour les schémas d’utilisateur ou des objets spécifiques (procédures).  
  
### <a name="implicit-and-explicit-permissions"></a>Autorisations implicites et explicites  
 Un *autorisation explicite* est un **GRANT** ou **DENY** autorisation donnée à un principal par un **GRANT** ou **DENY** instruction.  
  
 Un *autorisation implicite* est un **GRANT** ou **DENY** autorisation une entité de sécurité (connexion, utilisateur ou rôle de base de données) a hérité d’un autre rôle de base de données.  
  
 Autorisation implicite peut également être héritée à partir d’une couverture ou l’autorisation parente. Par exemple, **mise à jour** autorisation sur une table peut être héritée par ayant **mise à jour** autorisation sur le schéma qui contient la table, ou **contrôle** autorisation sur la table.  
  
### <a name="ownership-chaining"></a>Chaînage des propriétés  
 Lorsque plusieurs objets de base de données uns aux autres de manière séquentielle, la séquence est connue comme une *chaîne*. Bien que de telles chaînes n'existent pas indépendamment les unes des autres, lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] parcourt les liens d'une chaîne, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] évalue les autorisations sur les objets constitutifs différemment de ce qu'il ferait s'il accédait aux objets séparément. Le chaînage des propriétés a des implications importantes pour la gestion de la sécurité. Pour plus d’informations sur les chaînes de propriétés, consultez [chaînes](http://msdn.microsoft.com/en-us/library/ms188676\(v=sql11\).aspx) et [didacticiel : chaînes de propriétés et changement de contexte](http://msdn.microsoft.com/en-us/library/bb153640\(v=sql11\).aspx).  
  
## <a name="permission-list"></a>Liste des autorisations  
  
### <a name="server-level-permissions"></a>Autorisations de niveau serveur  
 Autorisations de niveau serveur peuvent être accordées, refusées et révoquées de connexions.  
  
 **Autorisations qui s’appliquent aux serveurs**  
  
-   CONTROL SERVER  
  
-   ADMINISTER BULK OPERATIONS  
  
-   ALTER ANY CONNECTION  
  
-   ALTER ANY DATABASE  
  
-   CREATE ANY DATABASE  
  
-   ALTER ANY EXTERNAL DATA SOURCE  
  
-   ALTER ANY EXTERNAL FILE FORMAT  
  
-   ALTER ANY LOGIN  
  
-   ALTER SERVER STATE  
  
-   CONNECT SQL  
  
-   VIEW ANY DEFINITION  
  
-   VIEW ANY DATABASE  
  
-   VIEW SERVER STATE  
  
 **Autorisations qui s’appliquent aux connexions**  
  
-   SUR LA CONNEXION DE CONTRÔLE  
  
-   ALTER SUR LA CONNEXION  
  
-   EMPRUNTER L’IDENTITÉ DE LA CONNEXION  
  
-   VIEW DEFINITION  
  
### <a name="database-level-permissions"></a>Autorisations de niveau base de données  
 Les autorisations de niveau base de données peuvent être accordées, refusées et révoqués à partir des utilisateurs de base de données et les rôles de base de données défini par l’utilisateur.  
  
 **Autorisations qui s’appliquent à toutes les classes de base de données**  
  
-   CONTROL  
  
-   ALTER  
  
-   VIEW DEFINITION  
  
 **Autorisations qui s’appliquent à toutes les classes de base de données à l’exception des utilisateurs**  
  
-   TAKE OWNERSHIP  
  
 **Autorisations qui s’appliquent uniquement aux bases de données**  
  
-   ALTER ANY DATABASE  
  
-   ALTER SUR LA BASE DE DONNÉES  
  
-   ALTER ANY DATASPACE  
  
-   ALTER ANY ROLE  
  
-   ALTER ANY SCHEMA  
  
-   ALTER ANY USER  
  
-   BACKUP DATABASE  
  
-   SE CONNECTER SUR LA BASE DE DONNÉES  
  
-   CREATE PROCEDURE  
  
-   CREATE ROLE  
  
-   CREATE SCHEMA  
  
-   CREATE TABLE  
  
-   CREATE VIEW  
  
-   SHOWPLAN  
  
 **Autorisations qui s’appliquent uniquement aux utilisateurs**  
  
-   IMPERSONATE  
  
 **Autorisations qui s’appliquent aux bases de données, des schémas et des objets**  
  
-   ALTER  
  
-   DELETE  
  
-   EXECUTE  
  
-   INSERT  
  
-   SELECT  
  
-   UPDATE  
  
-   REFRENCES  
  
 Pour une définition de chaque type d’autorisation, consultez [autorisations (moteur de base de données)](http://msdn.microsoft.com/library/ms191291.aspx).  
  
### <a name="chart-of-permissions"></a>Graphique des autorisations  
 Toutes les autorisations sont représentées graphiquement dans ce poster. Il s’agit de la façon la plus simple pour afficher une hiérarchie imbriquée d’autorisations. Par exemple le **ALTER ON LOGIN** autorisation peut être accordée par lui-même, mais il est également inclus si une connexion est accordée le **contrôle** autorisation sur cette connexion, ou si une connexion est accordée le **ALTER ANY LOGIN** autorisation.  
  
 ![Poster des autorisations sécurité APS](../../t-sql/statements/media/aps-security-perms-poster.png "poster des autorisations sécurité APS")  
  
 Pour télécharger une version de la taille totale de cette affiche, consultez [autorisations de SQL Server PDW](http://go.microsoft.com/fwlink/?LinkId=244249)dans la section des fichiers du site Yammer de points d’accès (ou une demande par courrier électronique à partir de  **apsdoc@microsoft.com** .  
  
## <a name="default-permissions"></a>Autorisations par défaut  
 La liste suivante décrit les autorisations par défaut :  
  
-   Lorsqu’une connexion est créée à l’aide de la **CREATE LOGIN** instruction la nouvelle connexion reçoit le **CONNECT SQL** autorisation.  
  
-   Toutes les connexions sont membres de la **public** rôle de serveur et ne peut pas être supprimé **public**.  
  
-   Lorsqu’un utilisateur de base de données est créé à l’aide de la **CREATE USER** autorisation, l’utilisateur de base de données reçoit le **CONNECT** autorisation dans la base de données.  
  
-   Tous les principaux, y compris le **public** rôle bénéficient pas d’autorisations explicites ou implicites par défaut.  
  
-   Lorsqu’une connexion ou un utilisateur devient le propriétaire d’un objet ou une base de données, la connexion ou l’utilisateur a toujours toutes les autorisations sur la base de données ou l’objet. Les autorisations de la propriété ne peut pas être modifiées et ne sont pas visibles en tant qu’autorisations explicites. Le **GRANT**, **DENY**, et **RÉVOQUER** instructions n’ont aucun effet sur les propriétaires.  
  
-   Le **sa** connexion dispose de toutes les autorisations sur l’appareil. Similaires aux autorisations de la propriété, le **sa** autorisations ne peut pas être modifiées et ne sont pas visibles en tant qu’autorisations explicites. Le **GRANT**, **DENY**, et **RÉVOQUER** instructions n’ont aucun effet **sa** connexion. Le **sa** connexion ne peut pas être renommée.  
  
-   Le **utilisez** instruction ne requiert pas d’autorisations. Tous les principaux peuvent exécuter la **utilisez** instruction sur une base de données.  
  
##  <a name="Examples"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-granting-a-server-level-permission-to-a-login"></a>A. Octroi d’une autorisation de niveau serveur à une connexion  
 Les deux instructions suivantes accorder une autorisation de niveau serveur à une connexion.  
  
```  
GRANT CONTROL SERVER TO [Ted];  
```  
  
```  
GRANT ALTER ANY DATABASE TO Mary;  
```  
  
### <a name="b-granting-a-server-level-permission-to-a-login"></a>B. Octroi d’une autorisation de niveau serveur à une connexion  
 L’exemple suivant accorde une autorisation au niveau du serveur sur une connexion à un serveur principal (connexion à un autre).  
  
```  
GRANT  VIEW DEFINITION ON LOGIN::Ted TO Mary;  
```  
  
### <a name="c-granting-a-database-level-permission-to-a-user"></a>C. Octroi d’une autorisation de niveau de base de données à un utilisateur  
 L’exemple suivant accorde une autorisation au niveau de la base de données sur un utilisateur à une base de données principal (un autre utilisateur).  
  
```  
GRANT VIEW DEFINITION ON USER::[Ted] TO Mary;  
```  
  
### <a name="d-granting-denying-and-revoking-a-schema-permission"></a>D. Octroi, de refus et de révocation d’une autorisation de schéma  
 Les éléments suivants **GRANT** instruction accorde Yuen la possibilité de sélectionner des données dans une table ou une vue dans le schéma dbo.  
  
```  
GRANT SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
 Les éléments suivants **DENY** instruction empêche Yuen à partir de la sélection de données dans une table ou une vue dans le schéma dbo. Yuen ne peut pas lire les données même s’il a l’autorisation d’une autre manière, par exemple via une appartenance au rôle.  
  
```  
DENY SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
 Les éléments suivants **RÉVOQUER** instruction supprime le **DENY** autorisation. Désormais, les autorisations explicites de Yuen sont neutres. Yuen peut être en mesure de sélectionner des données à partir de n’importe quelle table par le biais des autres autorisations implicites telles que l’appartenance d’un rôle.  
  
```  
REVOKE SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
### <a name="e-demonstrating-the-optional-object-clause"></a>E. Démonstration de l’objet facultatif :: clause  
 Étant donné que l’objet est la classe par défaut pour une instruction d’autorisation, les deux instructions suivantes sont identiques. Le **objet ::** clause est facultative.  
  
```  
GRANT UPDATE ON OBJECT::dbo.StatusTable TO [Ted];  
```  
  
```  
GRANT UPDATE ON dbo.StatusTable TO [Ted];  
```  
  
  


