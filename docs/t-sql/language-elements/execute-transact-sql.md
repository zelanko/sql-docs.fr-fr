---
title: EXECUTE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXEC
- EXECUTE_TSQL
- EXECUTE
- EXEC_TSQL
dev_langs: TSQL
helpviewer_keywords:
- remote stored procedures [SQL Server]
- command strings [SQL Server]
- extended stored procedures [SQL Server], executing
- stored procedures [SQL Server], executing
- Transact-SQL statements, executing
- strings [SQL Server], executing
- statements [SQL Server], executing
- context switching [SQL Server], execution context
- user-defined functions [SQL Server], executing
- character strings [SQL Server], executing
- switching execution context
- EXECUTE statement
ms.assetid: bc806b71-cc55-470a-913e-c5f761d5c4b7
caps.latest.revision: "104"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 52a896293ad991509884b45979be0129bd56f287
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="execute-transact-sql"></a>EXECUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Exécute une chaîne de commande ou une chaîne de caractères dans un [!INCLUDE[tsql](../../includes/tsql-md.md)] lot ou l’un des modules suivants : système stockées procédure, procédure stockée définie par l’utilisateur, procédure stockée CLR, fonction définie par l’utilisateur scalaire ou de la procédure stockée étendue. L'instruction EXECUTE peut être utilisée pour envoyer des commandes directes à des serveurs liés. De plus, il est possible de définir explicitement le contexte dans lequel une chaîne de caractères ou une commande s'exécute. Les métadonnées pour le jeu de résultats peuvent être définies à l'aide des options WITH RESULT SETS.
  
> [!IMPORTANT]  
>  Avant d'appeler EXECUTE avec une chaîne de caractères, validez cette dernière. N'exécutez jamais une commande construite par une entrée utilisateur qui n'a pas été validée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server  
  
Execute a stored procedure or function  
[ { EXEC | EXECUTE } ]  
    {   
      [ @return_status = ]  
      { module_name [ ;number ] | @module_name_var }   
        [ [ @parameter = ] { value   
                           | @variable [ OUTPUT ]   
                           | [ DEFAULT ]   
                           }  
        ]  
      [ ,...n ]  
      [ WITH <execute_option> [ ,...n ] ]  
    }  
[;]  
  
Execute a character string  
{ EXEC | EXECUTE }   
    ( { @string_variable | [ N ]'tsql_string' } [ + ...n ] )  
    [ AS { LOGIN | USER } = ' name ' ]  
[;]  
  
Execute a pass-through command against a linked server  
{ EXEC | EXECUTE }  
    ( { @string_variable | [ N ] 'command_string [ ? ]' } [ + ...n ]  
        [ { , { value | @variable [ OUTPUT ] } } [ ...n ] ]  
    )   
    [ AS { LOGIN | USER } = ' name ' ]  
    [ AT linked_server_name ]  
[;]  
  
<execute_option>::=  
{  
        RECOMPILE   
    | { RESULT SETS UNDEFINED }   
    | { RESULT SETS NONE }   
    | { RESULT SETS ( <result_sets_definition> [,...n ] ) }  
}   
  
<result_sets_definition> ::=   
{  
    (  
         { column_name   
           data_type   
         [ COLLATE collation_name ]   
         [ NULL | NOT NULL ] }  
         [,...n ]  
    )  
    | AS OBJECT   
        [ db_name . [ schema_name ] . | schema_name . ]   
        {table_name | view_name | table_valued_function_name }  
    | AS TYPE [ schema_name.]table_type_name  
    | AS FOR XML   
}  
```  
  
```  
-- In-Memory OLTP   

Execute a natively compiled, scalar user-defined function  
[ { EXEC | EXECUTE } ]   
    {   
      [ @return_status = ]   
      { module_name | @module_name_var }   
        [ [ @parameter = ] { value   
                           | @variable   
                           | [ DEFAULT ]   
                           }  
        ]   
      [ ,...n ]   
      [ WITH <execute_option> [ ,...n ] ]   
    }  
<execute_option>::=  
{  
    | { RESULT SETS UNDEFINED }   
    | { RESULT SETS NONE }   
    | { RESULT SETS ( <result_sets_definition> [,...n ] ) }  
}  
```  
  
```  
-- Syntax for Azure SQL Database   
  
Execute a stored procedure or function  
[ { EXEC | EXECUTE } ]  
    {   
      [ @return_status = ]  
      { module_name  | @module_name_var }   
        [ [ @parameter = ] { value   
                           | @variable [ OUTPUT ]   
                           | [ DEFAULT ]   
                           }  
        ]  
      [ ,...n ]  
      [ WITH RECOMPILE ]  
    }  
[;]  
  
Execute a character string  
{ EXEC | EXECUTE }   
    ( { @string_variable | [ N ]'tsql_string' } [ + ...n ] )  
    [ AS {  USER } = ' name ' ]  
[;]  
  
<execute_option>::=  
{  
        RECOMPILE   
    | { RESULT SETS UNDEFINED }   
    | { RESULT SETS NONE }   
    | { RESULT SETS ( <result_sets_definition> [,...n ] ) }  
}   
  
<result_sets_definition> ::=   
{  
    (  
         { column_name   
           data_type   
         [ COLLATE collation_name ]   
         [ NULL | NOT NULL ] }  
         [,...n ]  
    )  
    | AS OBJECT   
        [ db_name . [ schema_name ] . | schema_name . ]   
        {table_name | view_name | table_valued_function_name }  
    | AS TYPE [ schema_name.]table_type_name  
    | AS FOR XML  
  
```  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Execute a stored procedure  
[ { EXEC | EXECUTE } ]  
    procedure_name   
        [ { value | @variable [ OUT | OUTPUT ] } ] [ ,...n ] }  
[;]  
  
-- Execute a SQL string  
{ EXEC | EXECUTE }  
    ( { @string_variable | [ N ] 'tsql_string' } [ +...n ] )  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 @*état_de_retour*  
 Variable facultative de type entier qui stocke l'état du résultat d'un module. Cette variable doit être déclarée dans le traitement, la procédure stockée ou la fonction avant d'être utilisée dans une instruction EXECUTE.  
  
 Lorsqu’il est utilisé pour appeler une fonction de défini par l’utilisateur scalaire, le @*état_de_retour* variable peut être de n’importe quel type de données scalaire.  
  
 *nom_module*  
 Nom complet ou partiel de la procédure stockée ou de la fonction scalaire définie par l'utilisateur à appeler. Les noms de module doivent respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md). Les noms des procédures stockées étendues distinguent toujours les majuscules et les minuscules, quel que soit le classement du serveur.  
  
 Un module créé dans une autre base de données peut être exécuté si l'utilisateur est propriétaire du module ou possède l'autorisation nécessaire pour l'exécuter dans la base de données en question. Un module peut être exécuté sur un autre serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si l'utilisateur qui l'exécute a l'autorisation nécessaire pour utiliser ce serveur (accès à distance) et pour exécuter le module dans la base de données. Si le nom d'un serveur est spécifié mais qu'aucun nom de base de données n'est spécifié, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] recherche le module dans la base de données par défaut de l'utilisateur.  
  
 ; *nombre*  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Entier facultatif qui regroupe les procédures de même nom. Ce paramètre n'est pas utilisé pour les procédures stockées étendues.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Pour plus d’informations sur les groupes de procédures, consultez [CREATE PROCEDURE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-procedure-transact-sql.md).  
  
 @*module_name_var*  
 Nom d'une variable définie localement qui représente le nom d'un module.  
  
 Cela peut être une variable qui conserve le nom d’une fonction définie par l’utilisateur compilée en mode natif, scalaire.  
  
 @*paramètre*  
 Paramètre de *nom_module*, comme défini dans le module. Les noms des paramètres doivent être précédés du symbole (@). Lorsqu’il est utilisé avec le @*nom_paramètre*=*valeur* formulaire, les noms de paramètres et les constantes n’ont pas de les fournir dans l’ordre dans lequel ils sont définis dans le module. Toutefois, si le @*nom_paramètre*=*valeur* formulaire est utilisé pour n’importe quel paramètre, il doit être utilisé pour tous les paramètres suivants.  
  
 Par défaut, les paramètres acceptent les valeurs NULL.  
  
 *valeur*  
 Valeur du paramètre à passer au module ou à la commande directe. Si les noms des paramètres ne sont pas spécifiés, les valeurs des paramètres doivent être fournies dans l'ordre défini dans le module.  
  
 Lors de l'exécution de commandes directes sur des serveurs liés, l'ordre des valeurs des paramètres dépend du fournisseur OLE DB du serveur lié. La plupart des fournisseurs OLE DB lient les valeurs aux paramètres de gauche à droite.  
  
 Si la valeur d'un paramètre est le nom d'un objet, une chaîne de caractères, ou si elle est déterminée par le nom d'une base de données ou d'un schéma, le nom complet doit être placé entre guillemets simples. Si la valeur d'un paramètre est un mot clé, ce mot clé doit être mis entre guillemets doubles.  
  
 Si une valeur par défaut est définie dans le module, l'utilisateur peut exécuter le module sans spécifier de paramètre.  
  
 La valeur par défaut peut également être NULL. La définition du module indique généralement l'action à réaliser si la valeur d'un paramètre est NULL.  
  
 @*variable*  
 Variable qui stocke un paramètre ou un paramètre de retour.  
  
 OUTPUT  
 Spécifie que le module ou la chaîne de commandes renvoie un paramètre. Le paramètre correspondant dans le module ou la chaîne de commandes doit également avoir été créé à l'aide du mot clé OUTPUT. Utilisez ce mot clé lorsque vous utilisez des variables de curseur comme paramètres.  
  
 Si *valeur* est défini en tant que sortie d’un module exécuté sur un serveur lié, toute modification apportée aux correspondants*paramètre* effectuée par OLE DB fournisseur doivent être copié dans la variable à la fin de l’exécution du module.  
  
 Si des paramètres OUTPUT sont utilisés et l’objectif est d’utiliser les valeurs de retournés dans d’autres instructions à l’intérieur du module ou un lot d’appel, la valeur du paramètre doit être passée en tant que variable, telles que*paramètre* = @*variable*. Vous ne pouvez pas exécuter un module en spécifiant OUTPUT pour un paramètre qui n'est pas défini comme paramètre OUTPUT dans le module. Il est impossible de passer des constantes à un module en utilisant OUTPUT ; le paramètre de retour nécessite le nom d'une variable. Le type de données de la variable doit être déclaré et une valeur doit être affectée avant d'exécuter la procédure.  
  
 Lorsque l'instruction EXECUTE est utilisée sur une procédure stockée distante ou pour exécuter une commande directe sur un serveur lié, les paramètres OUTPUT ne peuvent pas avoir l'un des types de données des objets LOB.  
  
 Les paramètres de retour peuvent être de n'importe quel type, à l'exception des types LOB.  
  
 DEFAULT  
 Fournit la valeur par défaut du paramètre telle qu'elle est définie dans le module. Une erreur se produit quand le module attend une valeur pour un paramètre qui n'a pas de valeur définie par défaut et qu'un paramètre est manquant ou que le mot clé DEFAULT est spécifié.  
  
 @*string_variable*  
 Nom d'une variable locale. @*string_variable* peut être **char**, **varchar**, **nchar**, ou **nvarchar** type de données. Celles-ci incluent la **(max)** des types de données.  
  
 [N] '*tsql_string*'  
 Chaîne constante. *tsql_string* peut être **nvarchar** ou **varchar** type de données. Si N est inclus, la chaîne est interprétée en tant que **nvarchar** type de données.  
  
 En tant que \<context_specification >  
 Spécifie le contexte dans lequel l'instruction est exécutée.  
  
 Connexion  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Spécifie que le contexte dont l'identité doit être empruntée est une connexion. L'étendue de l'emprunt d'identité est le serveur.  
  
 Utilisateur  
 Spécifie que le contexte dont l'identité doit être empruntée est un utilisateur de la base de données active. L'étendue de l'emprunt d'identité est limitée à la base de données active. Le changement de contexte vers un utilisateur de base de données n'hérite pas des autorisations de cet utilisateur au niveau serveur.  
  
> [!IMPORTANT]  
>  Lorsque le changement de contexte vers l'utilisateur de base de données est actif, toute tentative d'accès aux ressources en dehors de la base de données entraîne l'échec de l'instruction. Cela inclut l’utilisation *base de données* , les requêtes distribuées, requêtes et instructions qui font référence à une autre base de données à l’aide d’identificateurs de trois ou quatre parties.  
  
 '*nom*'  
 Nom d'utilisateur ou de connexion valide. *nom* doit être membre du rôle serveur fixe sysadmin ou exister en tant que principal dans [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) ou [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md), respectivement.  
  
 *nom* ne peut pas être un compte intégré, tel que NT AUTHORITY\LocalService, NT AUTHORITY\NetworkService ou NT AUTHORITY\LocalSystem.  
  
 Pour plus d’informations, consultez [spécifiant un utilisateur ou un nom de connexion](#_user) plus loin dans cette rubrique.  
  
 [N] '*chaîne_de_commande*'  
 Chaîne constante qui contient la commande à passer via le serveur lié. Si N est inclus, la chaîne est interprétée en tant que **nvarchar** type de données.  
  
 [?]  
 Indique les paramètres dont les valeurs sont fournies dans le \<arg-list > de commandes directes qui sont utilisés dans un EXEC('...', \<arg-list>) à \<linkedsrv > instruction.  
  
 À *linked_server_name*  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Spécifie que *chaîne_de_commande* est exécutée sur *linked_server_name* et, le cas échéant, sont renvoyés au client. *linked_server_name* doit faire référence à une définition de serveur lié existante sur le serveur local. Serveurs liés sont définis à l’aide de [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).  
  
 AVEC \<execute_option >  
 Options d'exécution possibles. Les options RESULT SETS ne peuvent pas être spécifiées dans une instruction INSERT… EXEC.  
  
|Terme|Définition|  
|----------|----------------|  
|RECOMPILE|Impose la compilation, l'utilisation et la suppression d'un nouveau plan après l'exécution du module. S'il existe un plan de requêtes pour le module, ce plan reste en mémoire cache.<br /><br /> Utilisez cette option si le paramètre que vous fournissez est atypique ou si les données ont changé de manière significative. Cette option n'est pas utilisée pour les procédures stockées étendues. Nous recommandons d'utiliser cette option modérément car elle est coûteuse.<br /><br /> **Remarque :** ne pourrez pas utiliser WITH RECOMPILE lorsque vous appelez une procédure stockée qui utilise la syntaxe OPENDATASOURCE. L'option WITH RECOMPILE est ignorée lorsqu'un nom d'objet en quatre parties est spécifié.<br /><br /> **Remarque :** RECOMPILE n’est pas pris en charge avec les fonctions définies par l’utilisateur scalaires compilées en mode natif. Si vous devez recompiler, utilisez [sp_recompile &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-recompile-transact-sql.md).|  
|**JEUX DE RÉSULTATS NON DÉFINIS**|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> Cette option ne fournit aucune garantie quant aux résultats retournés, le cas échéant, et aucune définition n'est fournie. L'instruction s'exécute sans erreur si des résultats sont retournés ou aucun résultat n'est retourné. RESULT SETS UNDEFINED correspond au comportement par défaut si aucun result_sets_option n'est fourni.<br /><br /> Pour interpréter les fonctions scalaires définies par l’utilisateur et les fonctions scalaires définies par l’utilisateur compilées en mode natif, cette option n’est pas opérationnelle, car les fonctions retournent jamais un jeu de résultats.|  
|RESULT SETS NONE|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> Garantit que l'instruction d'exécution ne retournera pas de résultats. Si des résultats sont retournés, le traitement est abandonné.<br /><br /> Pour interpréter les fonctions scalaires définies par l’utilisateur et les fonctions scalaires définies par l’utilisateur compilées en mode natif, cette option n’est pas opérationnelle, car les fonctions retournent jamais un jeu de résultats.|  
|*\<result_sets_definition >*|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> Offre une garantie selon laquelle le résultat reviendra comme spécifié dans result_sets_definition. Pour les instructions qui retournent plusieurs jeux de résultats, fournissez plusieurs *result_sets_definition* sections. Placez chaque *result_sets_definition* entre parenthèses, séparées par des virgules. Pour plus d’informations, consultez \<result_sets_definition > plus loin dans cette rubrique.<br /><br /> Cette option est toujours génère une erreur pour les fonctions définies par l’utilisateur scalaires compilées en mode natif, car les fonctions retournent jamais un jeu de résultats.|
  
\<result_sets_definition > **s’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
  
 Décrit les jeux de résultats retournés par les instructions exécutées. Les clauses de result_sets_definition ont la signification suivante  
  
|Terme|Définition|  
|----------|----------------|  
|{<br /><br /> column_name<br /><br /> data_type<br /><br /> [ COLLATE collation_name]<br /><br /> [NULL &#124; NON NULL]<br /><br /> }|Consultez le tableau ci-dessous.|  
|db_name|Nom de la base de données contenant la table, la vue ou la fonction table.|  
|schema_name|Nom du schéma propriétaire de la table, de la vue ou de la fonction table.|  
|table_name &#124; view_name &#124; table_valued_function_name|Spécifie que les colonnes retournées seront celles spécifiées dans la table, la vue ou la fonction table nommée. Les variables de table, les tables temporaires et les synonymes ne sont pas pris en charge dans la syntaxe d'objet d'AS.|  
|AS TYPE [schema_name.]table_type_name|Spécifie que les colonnes retournées seront celles spécifiées dans le type de table.|  
|AS FOR XML|Spécifie que les résultats XML de l'instruction, ou de la procédure stockée appelée par l'instruction EXECUTE, sont convertis dans le même format que s'ils avaient été produits par une instruction SELECT … FOR XML … . Tous les formats des directives de type dans l'instruction d'origine sont supprimés, et les résultats retournés sont les mêmes que si aucune directive de type n'avait été spécifiée. AS FOR XML ne convertit pas les résultats tabulaires non XML de l'instruction ou de la procédure stockée exécutée en XML.|  
  
|Terme|Définition|  
|----------|----------------|  
|column_name|Nom de chaque colonne. Si le nombre de colonnes diffère du jeu de résultats, une erreur se produit et le lot est abandonné. Si le nom d'une colonne diffère du jeu de résultats, le nom de colonne retourné correspondra au nom défini.|  
|data_type|Types de données de chaque colonne. Si les types de données diffèrent, une conversion implicite vers le type de données défini est effectuée. Si la conversion échoue, le lot est abandonné|  
|COLLATE collation_name|Classement de chaque colonne. En cas d'incompatibilité de classement, un classement implicite est tenté. Si cette opération échoue, le lot est abandonné.|  
|NULL &#124; NON NULL|Valeur Null possible dans chaque colonne. Si la possibilité de valeur NULL définie est NOT NULL et que les données retournées contiennent des valeurs NULL, une erreur a lieu et le lot est abandonné. En l'absence de spécification, la valeur par défaut se conforme au paramètre des options ANSI_NULL_DFLT_ON et ANSI_NULL_DFLT_OFF.|  
  
 Le jeu de résultats réel qui est retourné pendant l'exécution peut différer du résultat défini à l'aide de la clause WITH RESULT SETS de l'une des manières suivantes : nombre de jeux de résultats, nombre de colonnes, nom de colonne, possibilité de valeur NULL et type de données. Si le nombre de jeu de résultats diffère, une erreur se produit et le lot est abandonné.  
  
## <a name="remarks"></a>Notes   
 Paramètres peuvent être fournis à l’aide *valeur* ou à l’aide de*nom_paramètre*=*valeur.* Un paramètre ne fait pas partie d’une transaction. Ainsi, si vous modifiez l’un d’eux dans une transaction et que vous restaurez cette dernière par la suite, le paramètre ne reprend pas sa valeur initiale. La valeur renvoyée à l'appelant est toujours la valeur au moment du renvoie du module.  
  
 L'imbrication a lieu lorsqu'un module en appelle un autre ou exécute du code managé en faisant référence à un module CLR (Common Language Runtime), un type défini par l'utilisateur ou un agrégat. Le niveau d'imbrication augmente au début de l'exécution du module appelé ou de la référence au code managé ; il diminue à la fin de l'exécution du module appelé ou de la référence au code managé. Au-delà de 32 niveaux d'imbrication, l'ensemble de la chaîne d'appel échoue. Le niveau d’imbrication actuel est stocké dans le @@NESTLEVEL fonction système.  
  
 Les procédures stockées distantes et les procédures stockées étendues n'étant pas incluses dans l'étendue d'une transaction (à moins qu'elles proviennent d'une instruction BEGIN DISTRIBUTED TRANSACTION ou qu'elles soient utilisées avec des options de configuration diverses), il est impossible d'annuler les commandes exécutées par l'appel de ces procédures. Pour plus d’informations, consultez [procédures stockées système &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) et [BEGIN DISTRIBUTED TRANSACTION &#40; Transact-SQL &#41; ](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md).  
  
 Lorsque vous utilisez des variables de curseur, une erreur se produit si vous exécutez une procédure qui passe une variable de curseur avec un curseur qui lui est alloué.  
  
 Il n'est pas nécessaire de spécifier le mot clé EXECUTE lorsque vous exécutez des modules si l'instruction est la première d'un lot.  
  
 Pour plus d'informations spécifiques aux procédures stockées CLR, consultez Procédures stockées CLR.  
  
## <a name="using-execute-with-stored-procedures"></a>Utilisation de l'instruction EXECUTE avec des procédures stockées  
 Il n'est pas nécessaire de spécifier le mot clé EXECUTE lorsque vous exécutez des procédures stockées si l'instruction est la première du traitement.  
  
 Les procédures stockées système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commencent par les caractères sp_. Elles sont stockées physiquement dans le [base de données Resource](../../relational-databases/databases/resource-database.md), mais apparaissent logiquement dans le schéma sys de chaque système et la base de données défini par l’utilisateur. Lorsque vous exécutez une procédure stockée système, que ce soit dans un lot ou dans un module, telle qu'une procédure stockée ou une fonction définie par l'utilisateur, il est recommandé de qualifier son nom avec le nom de schéma sys.  
  
 Les procédures stockées étendues système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commencent par les caractères xp_, : elles se trouvent dans le schéma dbo de la base de données master. Lorsque vous exécutez une procédure stockée système étendue, que ce soit dans un lot ou dans un module, telle qu'une procédure stockée ou une fonction définie par l'utilisateur, il est recommandé de qualifier son nom avec master.dbo.  
  
 Lorsque vous exécutez une procédure stockée définie par l'utilisateur, que ce soit dans un lot ou dans un module, telle qu'une procédure stockée ou une fonction définie par l'utilisateur, il est recommandé de qualifier son nom avec un nom de schéma. Il n'est pas conseillé de nommer une procédure stockée définie par l'utilisateur avec le même nom qu'une procédure stockée système. Pour plus d’informations sur l’exécution des procédures stockées, consultez [exécuter une procédure stockée](../../relational-databases/stored-procedures/execute-a-stored-procedure.md).  
  
## <a name="using-execute-with-a-character-string"></a>Utilisation de l'instruction EXECUTE avec une chaîne de caractères  
 Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les chaînes de caractères sont limitées à 8 000 octets. Cela nécessite de concaténer les chaînes volumineuses pour l'exécution dynamique. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le **varchar (max)** et **nvarchar (max)** peuvent être spécifiés des types de données qui autorisent des chaînes de caractères à être jusqu'à 2 gigaoctets de données.  
  
 Les modifications du contexte de la base de données ne durent que jusqu'à la fin de l'instruction EXECUTE. Dans le code exemple qui suit, après l'exécution de l'instruction `EXEC`, le contexte de la base de données est master.  
  
```sql  
USE master; EXEC ('USE AdventureWorks2012; SELECT BusinessEntityID, JobTitle FROM HumanResources.Employee;');  
```  
  
## <a name="context-switching"></a>Changement de contexte  
 Vous pouvez utiliser la clause `AS { LOGIN | USER } = ' name '` pour changer le contexte d'exécution d'une instruction dynamique. Lorsque le changement de contexte est spécifié sous la forme `EXECUTE ('string') AS <context_specification>`, la durée du changement est limitée à l'étendue de la requête en cours d'exécution.  
  
###  <a name="_user"></a>Spécification d’un utilisateur ou un nom de connexion  
 L'utilisateur ou le nom de connexion spécifié dans `AS { LOGIN | USER } = ' name '` doit exister en tant que principal respectivement dans sys.database_principals ou sys.server_principals, faute de quoi l'instruction échoue. De plus, les autorisations IMPERSONATE doivent être accordées sur le principal. À moins que l'appelant soit le propriétaire de la base de données ou un membre du rôle serveur fixe sysadmin, le principal doit exister même lorsque l'utilisateur accède à la base de données ou à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais d'une appartenance à un groupe Windows. Par exemple, supposons les conditions suivantes :  
  
-   Le groupe CompanyDomain\SQLUsers a accès à la base de données Sales.  
  
-   L'utilisateur CompanyDomain\SqlUser1 est membre de SQLUsers : il a donc un accès implicite à la base de données Sales.  
  
 Bien que CompanyDomain\SqlUser1 ait accès à la base de données via l’appartenance dans SQLUsers groupe, l’instruction `EXECUTE @string_variable AS USER = 'CompanyDomain\SqlUser1'` vont échouer car `CompanyDomain\SqlUser1` n’existe pas en tant que principal dans la base de données.  
  
### <a name="best-practices"></a>Bonnes pratiques  
 Spécifiez une connexion ou un utilisateur qui possède les privilèges minimum requis pour effectuer les opérations définies dans l'instruction ou le module. Par exemple, ne spécifiez pas un nom de connexion qui a des autorisations au niveau serveur, si seules des autorisations au niveau base de données sont requises. Ne spécifiez pas non plus le compte d'un propriétaire de base de données, excepté si ces autorisations sont exigées.  
  
## <a name="permissions"></a>Autorisations  
 Aucune autorisation n'est requise pour exécuter l'instruction EXECUTE. Cependant, des autorisations sont requises sur les éléments sécurisables référencés dans la chaîne EXECUTE. Par exemple, si la chaîne contient une instruction INSERT, l'appelant de l'instruction EXECUTE doit posséder l'autorisation INSERT sur la table cible. Les autorisations sont vérifiées au moment où l'instruction EXECUTE est rencontrée, même si celle-ci est incluse dans un module.  
  
 Les autorisations EXECUTE pour un module sont accordées par défaut au propriétaire du module, qui peut les transmettre à d'autres utilisateurs. Lorsqu'un module qui exécute une chaîne est lancé, les autorisations sont vérifiées dans le contexte non pas de l'utilisateur qui a créé le module, mais de celui qui exécute le module. Cependant, si le même utilisateur est propriétaire du module appelant et du module appelé, la vérification de l'autorisation EXECUTE n'a pas lieu pour le second module.  
  
 Si le module accède à d'autres objets de la base de données, l'exécution réussit lorsque vous avez l'autorisation EXECUTE sur le module et si l'une des conditions suivantes est remplie :  
  
-   Le module est repéré avec EXECUTE AS USER ou SELF et son propriétaire a les autorisations correspondantes sur l'objet référencé. Pour plus d’informations sur l’emprunt d’identité dans un module, consultez [Clause EXECUTE AS &#40; Transact-SQL &#41; ](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
-   Le module est repéré avec EXECUTE AS CALLER et vous avez les autorisations correspondantes sur l'objet.  
  
-   Le module est repéré avec EXECUTE AS *nom_utilisateur*, et *nom_utilisateur* a les autorisations correspondantes sur l’objet.  
  
### <a name="context-switching-permissions"></a>Autorisations pour les changements de contexte  
 Pour spécifier EXECUTE AS sur une connexion, l'appelant doit posséder les autorisations IMPERSONATE sur le nom de connexion spécifié. Pour spécifier EXECUTE AS sur un utilisateur de base de données, l'appelant doit posséder les autorisations IMPERSONATE sur le nom d'utilisateur spécifié. Lorsqu'aucun contexte d'exécution n'est spécifié ou lorsque EXECUTE AS CALLER est spécifié, les autorisations IMPERSONATE ne sont pas requises.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-execute-to-pass-a-single-parameter"></a>A. Utilisation de l'instruction EXECUTE pour passer un seul paramètre  
 La procédure stockée `uspGetEmployeeManagers` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] attend un seul paramètre (`@EmployeeID`). L’exemple suivant exécute la `uspGetEmployeeManagers` procédure stockée avec `Employee ID 6` comme valeur de paramètre.  
  
```  
EXEC dbo.uspGetEmployeeManagers 6;  
GO  
```  
  
 La variable peut être désignée explicitement dans l'exécution :  
  
```  
EXEC dbo.uspGetEmployeeManagers @EmployeeID = 6;  
GO  
```  
  
 Si ce qui suit est la première instruction dans un lot ou une **osql** ou **sqlcmd** script, EXEC n’est pas requis.  
  
```  
dbo.uspGetEmployeeManagers 6;  
GO  
--Or  
dbo.uspGetEmployeeManagers @EmployeeID = 6;  
GO  
```  
  
### <a name="b-using-multiple-parameters"></a>B. Utilisation de plusieurs paramètres  
 L'exemple suivant exécute la procédure stockée `spGetWhereUsedProductID` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Il passe deux paramètres : le premier est l'identificateur d'un produit (`819`), et le second paramètre, `@CheckDate,`, est une valeur `datetime`.  
  
```  
DECLARE @CheckDate datetime;  
SET @CheckDate = GETDATE();  
EXEC dbo.uspGetWhereUsedProductID 819, @CheckDate;  
GO  
```  
  
### <a name="c-using-execute-tsqlstring-with-a-variable"></a>C. Utilisation de l'instruction EXECUTE 'tsql_string' avec une variable  
 Le code exemple suivant montre comment `EXECUTE` manipule les chaînes construites dynamiquement qui contiennent des variables. Cet exemple crée le curseur `tables_cursor` pour contenir la liste de toutes les tables définies par l'utilisateur dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], puis utilise cette liste pour reconstruire tous les index des tables.  
  
```  
DECLARE tables_cursor CURSOR  
   FOR  
   SELECT s.name, t.name   
   FROM sys.objects AS t  
   JOIN sys.schemas AS s ON s.schema_id = t.schema_id  
   WHERE t.type = 'U';  
OPEN tables_cursor;  
DECLARE @schemaname sysname;  
DECLARE @tablename sysname;  
FETCH NEXT FROM tables_cursor INTO @schemaname, @tablename;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN;  
   EXECUTE ('ALTER INDEX ALL ON ' + @schemaname + '.' + @tablename + ' REBUILD;');  
   FETCH NEXT FROM tables_cursor INTO @schemaname, @tablename;  
END;  
PRINT 'The indexes on all tables have been rebuilt.';  
CLOSE tables_cursor;  
DEALLOCATE tables_cursor;  
GO  
  
```  
  
### <a name="d-using-execute-with-a-remote-stored-procedure"></a>D. Utilisation de l'instruction EXECUTE avec une procédure stockée distante  
 Le code exemple suivant exécute la procédure stockée `uspGetEmployeeManagers` sur le serveur distant `SQLSERVER1` et stocke dans `@retstat` l'état du résultat qui indique la réussite ou l'échec.  
  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
DECLARE @retstat int;  
EXECUTE @retstat = SQLSERVER1.AdventureWorks2012.dbo.uspGetEmployeeManagers @BusinessEntityID = 6;  
```  
  
### <a name="e-using-execute-with-a-stored-procedure-variable"></a>E. Utilisation de l'instruction EXECUTE avec une variable de procédure stockée  
 Le code exemple suivant crée une variable qui représente le nom d'une procédure stockée.  
  
```sql  
DECLARE @proc_name varchar(30);  
SET @proc_name = 'sys.sp_who';  
EXEC @proc_name;  
  
```  
  
### <a name="f-using-execute-with-default"></a>F. Utilisation de l'instruction EXECUTE avec l'option DEFAULT  
 Le code exemple suivant crée une procédure stockée avec des valeurs par défaut pour les premier et troisième paramètres. Lorsque la procédure est exécutée, ces valeurs par défaut sont insérées pour les premier et troisième paramètres si aucune valeur n'est passée dans l'appel ou si la valeur par défaut est spécifiée. Notez les différentes façons d'utiliser le mot clé `DEFAULT`.  
  
```  
IF OBJECT_ID(N'dbo.ProcTestDefaults', N'P')IS NOT NULL  
   DROP PROCEDURE dbo.ProcTestDefaults;  
GO  
-- Create the stored procedure.  
CREATE PROCEDURE dbo.ProcTestDefaults (  
@p1 smallint = 42,   
@p2 char(1),   
@p3 varchar(8) = 'CAR')  
AS   
   SET NOCOUNT ON;  
   SELECT @p1, @p2, @p3  
;  
GO  
  
```  
  
 L'exécution de la procédure stockée `Proc_Test_Defaults` peut s'effectuer selon plusieurs combinaisons.  
  
```  
-- Specifying a value only for one parameter (@p2).  
EXECUTE dbo.ProcTestDefaults @p2 = 'A';  
-- Specifying a value for the first two parameters.  
EXECUTE dbo.ProcTestDefaults 68, 'B';  
-- Specifying a value for all three parameters.  
EXECUTE dbo.ProcTestDefaults 68, 'C', 'House';  
-- Using the DEFAULT keyword for the first parameter.  
EXECUTE dbo.ProcTestDefaults @p1 = DEFAULT, @p2 = 'D';  
-- Specifying the parameters in an order different from the order defined in the procedure.  
EXECUTE dbo.ProcTestDefaults DEFAULT, @p3 = 'Local', @p2 = 'E';  
-- Using the DEFAULT keyword for the first and third parameters.  
EXECUTE dbo.ProcTestDefaults DEFAULT, 'H', DEFAULT;  
EXECUTE dbo.ProcTestDefaults DEFAULT, 'I', @p3 = DEFAULT;  
  
```  
  
### <a name="g-using-execute-with-at-linkedservername"></a>G. Utilisation de l'instruction EXECUTE avec AT linked_server_name  
 Le code exemple suivant passe une chaîne de commandes à un serveur distant. Il crée un serveur lié `SeattleSales` qui pointe vers une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et exécute une instruction DDL (`CREATE TABLE`) sur ce serveur lié.  
  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
EXEC sp_addlinkedserver 'SeattleSales', 'SQL Server'  
GO  
EXECUTE ( 'CREATE TABLE AdventureWorks2012.dbo.SalesTbl   
(SalesID int, SalesName varchar(10)) ; ' ) AT SeattleSales;  
GO  
```  
  
### <a name="h-using-execute-with-recompile"></a>H. Utilisation de l'instruction EXECUTE WITH RECOMPILE  
 L’exemple suivant exécute la `Proc_Test_Defaults` procédure stockée et force un nouveau plan de requête à compiler, utilisé et supprimées une fois que le module est exécuté.  
  
```  
EXECUTE dbo.Proc_Test_Defaults @p2 = 'A' WITH RECOMPILE;  
GO  
```  
  
### <a name="i-using-execute-with-a-user-defined-function"></a>I. Utilisation de l'instruction EXECUTE avec une fonction définie par l'utilisateur  
 Le code exemple suivant exécute la fonction scalaire `ufnGetSalesOrderStatusText` définie par l'utilisateur dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Il utilise la variable `@returnstatus` pour stocker la valeur renvoyée par la fonction. Celle-ci attend un seul paramètre d'entrée, `@Status`, Cela est défini comme un **tinyint** type de données.  
  
```  
DECLARE @returnstatus nvarchar(15);  
SET @returnstatus = NULL;  
EXEC @returnstatus = dbo.ufnGetSalesOrderStatusText @Status = 2;  
PRINT @returnstatus;  
GO  
```  
  
### <a name="j-using-execute-to-query-an-oracle-database-on-a-linked-server"></a>J. Utilisation de l'instruction EXECUTE pour interroger une base de données Oracle sur un serveur lié  
 Le code exemple suivant exécute plusieurs instructions `SELECT` sur le serveur Oracle distant. Il commence par ajouter le serveur Oracle comme serveur lié puis crée ensuite la connexion au serveur lié.  
  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
-- Setup the linked server.  
EXEC sp_addlinkedserver    
        @server='ORACLE',  
        @srvproduct='Oracle',  
        @provider='OraOLEDB.Oracle',   
        @datasrc='ORACLE10';  
  
EXEC sp_addlinkedsrvlogin   
    @rmtsrvname='ORACLE',  
    @useself='false',   
    @locallogin=null,   
    @rmtuser='scott',   
    @rmtpassword='tiger';  
  
EXEC sp_serveroption 'ORACLE', 'rpc out', true;  
GO  
  
-- Execute several statements on the linked Oracle server.  
EXEC ( 'SELECT * FROM scott.emp') AT ORACLE;  
GO  
EXEC ( 'SELECT * FROM scott.emp WHERE MGR = ?', 7902) AT ORACLE;  
GO  
DECLARE @v INT;   
SET @v = 7902;  
EXEC ( 'SELECT * FROM scott.emp WHERE MGR = ?', @v) AT ORACLE;  
GO   
```  
  
### <a name="k-using-execute-as-user-to-switch-context-to-another-user"></a>K. Utilisation de l'instruction EXECUTE AS USER pour basculer le contexte vers un autre utilisateur  
 Le code exemple suivant exécute une chaîne [!INCLUDE[tsql](../../includes/tsql-md.md)] qui crée une table et spécifie la clause `AS USER` pour basculer le contexte d'exécution de l'instruction de l'appelant vers l'utilisateur `User1`. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] vérifie les autorisations de `User1` lorsque l'instruction est exécutée. `User1` doit exister dans la base de données et posséder l'autorisation de créer des tables dans le schéma `Sales`, faute de quoi l'instruction échoue.  
  
```  
EXECUTE ('CREATE TABLE Sales.SalesTable (SalesID int, SalesName varchar(10));')  
AS USER = 'User1';  
GO  
```  
  
### <a name="l-using-a-parameter-with-execute-and-at-linkedservername"></a>L. Utilisation d'un paramètre avec l'instruction EXECUTE et AT linked_server_name  
 L'exemple suivant passe une chaîne de commande à un serveur distant en utilisant un point d'interrogation (`?`) comme espace réservé pour un paramètre. Cet exemple crée un serveur lié `SeattleSales` qui pointe vers une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et exécute une instruction `SELECT` sur ce serveur lié. L'instruction `SELECT` utilise le point d'interrogation comme espace réservé pour le paramètre `ProductID` (`952`) qui est fourni après l'instruction.  
  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
-- Setup the linked server.  
EXEC sp_addlinkedserver 'SeattleSales', 'SQL Server'  
GO  
-- Execute the SELECT statement.  
EXECUTE ('SELECT ProductID, Name   
    FROM AdventureWorks2012.Production.Product  
    WHERE ProductID = ? ', 952) AT SeattleSales;  
GO  
```  
  
### <a name="m-using-execute-to-redefine-a-single-result-set"></a>M. Utilisation de l'instruction EXECUTE pour redéfinir un jeu de résultats unique  
 Certains des exemples précédents ont exécuté `EXEC dbo.uspGetEmployeeManagers 6;` qui a retourné 7 colonnes. L'exemple suivant montre l'utilisation de la syntaxe `WITH RESULT SET` pour modifier les noms et types de données du jeu de résultats retourné.  
  
**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
  
```  
EXEC uspGetEmployeeManagers 16  
WITH RESULT SETS  
(   
   ([Reporting Level] int NOT NULL,  
    [ID of Employee] int NOT NULL,  
    [Employee First Name] nvarchar(50) NOT NULL,  
    [Employee Last Name] nvarchar(50) NOT NULL,  
    [Employee ID of Manager] nvarchar(max) NOT NULL,  
    [Manager First Name] nvarchar(50) NOT NULL,  
    [Manager Last Name] nvarchar(50) NOT NULL )  
);  
  
```  
  
### <a name="n-using-execute-to-redefine-a-two-result-sets"></a>N. Utilisation de l'instruction EXECUTE pour redéfinir deux jeux de résultats  
 Lorsque vous exécutez une instruction qui retourne plusieurs jeux de résultats, définissez chaque jeu de résultats attendu. L'exemple suivant dans [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] crée une procédure qui retourne deux jeux de résultats. Ensuite, la procédure est exécutée à l’aide de la **WITH RESULT SETS** clause et en spécifiant les résultats de deux définitions de jeu.  
  
**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
  
```  
--Create the procedure  
CREATE PROC Production.ProductList @ProdName nvarchar(50)  
AS  
-- First result set  
SELECT ProductID, Name, ListPrice  
    FROM Production.Product  
    WHERE Name LIKE @ProdName;  
-- Second result set   
SELECT Name, COUNT(S.ProductID) AS NumberOfOrders  
    FROM Production.Product AS P  
    JOIN Sales.SalesOrderDetail AS S  
        ON P.ProductID  = S.ProductID   
    WHERE Name LIKE @ProdName  
    GROUP BY Name;  
GO  
  
-- Execute the procedure   
EXEC Production.ProductList '%tire%'  
WITH RESULT SETS   
(  
    (ProductID int,   -- first result set definition starts here  
    Name Name,  
    ListPrice money)  
    ,                 -- comma separates result set definitions  
    (Name Name,       -- second result set definition starts here  
    NumberOfOrders int)  
);  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="example-o-basic-procedure-execution"></a>Exemple O: exécution de la procédure de base  
 Exécution d’une procédure stockée :  
  
```  
EXEC proc1;  
```  
  
 Appel d’une procédure stockée avec le nom déterminé lors de l’exécution :  
  
```  
EXEC ('EXEC ' + @var);  
```  
  
 Appel d’une procédure stockée à partir d’une procédure stockée :  
  
```  
CREATE sp_first AS EXEC sp_second; EXEC sp_third;  
```  
  
### <a name="example-p-executing-strings"></a>Exemple P: l’exécution de chaînes  
 Exécution d’une chaîne SQL :  
  
```  
EXEC ('SELECT * FROM sys.types');  
```  
  
 Exécution d’une chaîne imbriquée :  
  
```  
EXEC ('EXEC (''SELECT * FROM sys.types'')');  
```  
  
 Exécution d’une variable de chaîne :  
  
```  
DECLARE @stringVar nvarchar(100);  
SET @stringVar = N'SELECT name FROM' + ' sys.sql_logins';  
EXEC (@stringVar);  
```  
  
### <a name="example-q-procedures-with-parameters"></a>Exemple q : procédures avec des paramètres  
 L’exemple suivant crée une procédure avec des paramètres et illustre les 3 façons d’exécuter la procédure :  
  
```  
-- Uses AdventureWorks  
  
CREATE PROC ProcWithParameters  
    @name nvarchar(50),  
@color nvarchar (15)  
AS   
SELECT ProductKey, EnglishProductName, Color FROM [dbo].[DimProduct]  
WHERE EnglishProductName LIKE @name  
AND Color = @color;  
GO  
  
-- Executing using positional parameters  
EXEC ProcWithParameters N'%arm%', N'Black';  
-- Executing using named parameters in order  
EXEC ProcWithParameters @name = N'%arm%', @color = N'Black';  
-- Executing using named parameters out of order  
EXEC ProcWithParameters @color = N'Black', @name = N'%arm%';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [@@NESTLEVEL &#40;Transact-SQL&#41;](../../t-sql/functions/nestlevel-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [Clause EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)   
 [Utilitaire osql](../../tools/osql-utility.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Rétablir &#40; Transact-SQL &#41;](../../t-sql/statements/revert-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [SUSER_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/suser-name-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [User_name &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [OPENDATASOURCE &#40;Transact-SQL&#41;](../../t-sql/functions/opendatasource-transact-sql.md)   
 [Fonctions scalaires définies par l’utilisateur pour l’OLTP en mémoire](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)  
  
  
