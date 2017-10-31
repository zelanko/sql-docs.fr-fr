---
title: "CRÉER (fonction) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FUNCTION
- CREATE FUNCTION
- CREATE_FUNCTION_TSQL
- FUNCTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- invoking functions
- extended stored procedures [SQL Server], functions
- table-valued parameters
- user-defined functions [SQL Server], creating
- CLR functions [SQL Server]
- CREATE FUNCTION statement
- nondeterministic functions
- user-defined data types
- functions [SQL Server], creating
- inline table-valued functions [SQL Server]
- multi-statement table-valued functions [SQL Server]
- table-valued functions [SQL Server], CREATE FUNCTION
- parameters [SQL Server], functions
- nesting user-defined functions
- deterministic functions
- scalar-valued functions
- functions [SQL Server], invoking
ms.assetid: 864b393f-225f-4895-8c8d-4db59ea60032
caps.latest.revision: 162
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: c74e3a3322dcc2268fa8e386fda5d55f59be98c5
ms.contentlocale: fr-fr
ms.lasthandoff: 10/24/2017

---
# <a name="create-function-transact-sql"></a>CREATE FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crée une fonction définie par l'utilisateur dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Une fonction définie par l'utilisateur est une routine [!INCLUDE[tsql](../../includes/tsql-md.md)] ou CLR (Common Language Runtime) qui accepte des paramètres, exécute une action, par exemple un calcul complexe, et retourne le résultat de cette action sous forme de valeur. La valeur retournée peut être une valeur scalaire (unique) ou une table. Utilisez cette instruction pour créer une routine réutilisable, exploitable :  
  
-   dans des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] telles que SELECT ;  
  
-   dans des applications appelant la fonction ;  
  
-   dans la définition d'une autre fonction définie par l'utilisateur ;  
  
-   pour paramétrer une vue ou améliorer la fonctionnalité d'une vue indexée ;  
  
-   pour définir une colonne dans une table ;  
  
-   pour définir une contrainte CHECK sur une colonne ;  
  
-   pour remplacer une procédure stockée.  
  
-   Utiliser une fonction comme prédicat de filtre pour une stratégie de sécurité  
  
> [!NOTE]  
>  L’intégration du CLR .NET Framework dans SQL Server est décrite dans cette rubrique. Intégration du CLR ne s’applique pas à la base de données SQL Azure.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Transact-SQL Scalar Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ = default ] [ READONLY ] }   
    [ ,...n ]  
  ]  
)  
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN scalar_expression  
    END  
[ ; ]  
```  
  
```  
-- Transact-SQL Inline Table-Valued Function Syntax   
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] [ READONLY ] }   
    [ ,...n ]  
  ]  
)  
RETURNS TABLE  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    RETURN [ ( ] select_stmt [ ) ]  
[ ; ]  
  
```  
  
```  
-- Transact-SQL Multi-Statement Table-Valued Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] [READONLY] }   
    [ ,...n ]  
  ]  
)  
RETURNS @return_variable TABLE <table_type_definition>  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN  
    END  
[ ; ]  
  
```  

```  
-- Transact-SQL Function Clauses   
<function_option>::=   
{  
    [ ENCRYPTION ]  
  | [ SCHEMABINDING ]  
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
  | [ EXECUTE_AS_Clause ]  
}  
  
<table_type_definition>:: =   
( { <column_definition> <column_constraint>   
  | <computed_column_definition> }   
    [ <table_constraint> ] [ ,...n ]  
)   
<column_definition>::=  
{  
    { column_name data_type }  
    [ [ DEFAULT constant_expression ]   
      [ COLLATE collation_name ] | [ ROWGUIDCOL ]  
    ]  
    | [ IDENTITY [ (seed , increment ) ] ]  
    [ <column_constraint> [ ...n ] ]   
}  
  
<column_constraint>::=   
{  
    [ NULL | NOT NULL ]   
    { PRIMARY KEY | UNIQUE }  
      [ CLUSTERED | NONCLUSTERED ]   
      [ WITH FILLFACTOR = fillfactor   
        | WITH ( < index_option > [ , ...n ] )  
      [ ON { filegroup | "default" } ]  
  | [ CHECK ( logical_expression ) ] [ ,...n ]  
}  
  
<computed_column_definition>::=  
column_name AS computed_column_expression   
  
<table_constraint>::=  
{   
    { PRIMARY KEY | UNIQUE }  
      [ CLUSTERED | NONCLUSTERED ]   
      ( column_name [ ASC | DESC ] [ ,...n ] )  
        [ WITH FILLFACTOR = fillfactor   
        | WITH ( <index_option> [ , ...n ] )  
  | [ CHECK ( logical_expression ) ] [ ,...n ]  
}  
  
<index_option>::=  
{   
    PAD_INDEX = { ON | OFF }   
  | FILLFACTOR = fillfactor   
  | IGNORE_DUP_KEY = { ON | OFF }  
  | STATISTICS_NORECOMPUTE = { ON | OFF }   
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS ={ ON | OFF }   
}  
```  
  
```  
-- CLR Scalar Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( { @parameter_name [AS] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
)  
RETURNS { return_data_type }  
    [ WITH <clr_function_option> [ ,...n ] ]  
    [ AS ] EXTERNAL NAME <method_specifier>  
[ ; ]  
```  
  
```  
-- CLR Table-Valued Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( { @parameter_name [AS] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
)  
RETURNS TABLE <clr_table_type_definition>   
    [ WITH <clr_function_option> [ ,...n ] ]  
    [ ORDER ( <order_clause> ) ]  
    [ AS ] EXTERNAL NAME <method_specifier>  
[ ; ]  
```  

```  
-- CLR Function Clauses  
<order_clause> ::=   
{  
   <column_name_in_clr_table_type_definition>  
   [ ASC | DESC ]   
} [ ,...n]   
  
<method_specifier>::=  
    assembly_name.class_name.method_name  
  
<clr_function_option>::=  
}  
    [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
  | [ EXECUTE_AS_Clause ]  
}  
  
<clr_table_type_definition>::=   
( { column_name data_type } [ ,...n ] )  
  
```  
  
```  
-- In-Memory OLTP: Syntax for natively compiled, scalar user-defined function  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
 ( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ NULL | NOT NULL ] [ = default ] [ READONLY ] }   
    [ ,...n ]   
  ]   
)   
RETURNS return_data_type  
     WITH <function_option> [ ,...n ]   
    [ AS ]   
    BEGIN ATOMIC WITH (set_option [ ,... n ])   
        function_body   
        RETURN scalar_expression  
    END  
  
<function_option>::=   
{  
  |  NATIVE_COMPILATION   
  |  SCHEMABINDING   
  | [ EXECUTE_AS_Clause ]   
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]   
}  
  
```  
  
## <a name="arguments"></a>Arguments
*OU ALTER*  
 **S’applique aux**: Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (en commençant par [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1).  
  
 Conditionnellement modifie la fonction uniquement s’il existe déjà. 
 
> [!NOTE]  
>  Syntaxe [ou ALTER] facultatifs pour le CLR est disponible à partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU1.   
 
 *schema_name*  
 Nom du schéma auquel appartient la fonction définie par l'utilisateur.  
  
 *nom de la fonction*  
 Nom de la fonction définie par l'utilisateur. Les noms de fonctions doivent respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md) et doivent être uniques au sein de la base de données et son schéma.  
  
> [!NOTE]  
>  Les parenthèses sont requises après le nom de fonction même si aucun paramètre n'est spécifié.  
  
 @*nom_paramètre*  
 Paramètre dans la fonction définie par l'utilisateur. Un ou plusieurs paramètres peuvent être déclarés.  
  
 Une fonction peut comprendre au maximum 2 100 paramètres. La valeur de chaque paramètre déclaré doit être fournie par l'utilisateur lors de l'exécution de la fonction, sauf si vous définissez une valeur par défaut pour le paramètre.  
  
 Spécifiez un nom de paramètre en plaçant le signe @ comme premier caractère. Le nom de paramètre doit suivre les règles applicables aux identificateurs. Un paramètre étant local à une fonction, vous pouvez utiliser le même nom dans d'autres fonctions. Les paramètres ne peuvent que prendre la place de constantes ; ils ne peuvent pas être utilisés à la place de noms de tables, de colonnes ou d'autres objets de base de données.  
  
> [!NOTE]  
>  ANSI_WARNINGS n'est pas honoré lorsque vous transmettez des paramètres dans une procédure stockée, dans une fonction définie par l'utilisateur ou lorsque vous déclarez et définissez des variables dans une instruction par lot. Par exemple, si une variable est définie en tant que **char (3)**, puis définissez une valeur supérieure à trois caractères, les données sont tronquées à la taille définie et l’insertion ou instruction de mise à jour réussit.  
  
 [ *type_schema_name*. ] *parameter_data_type*  
 Type de données de paramètre et, éventuellement, schéma auquel il appartient. Pour [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions, tous les types de données, y compris les types CLR définis par l’utilisateur et les types de table défini par l’utilisateur, sont autorisées à l’exception de la **timestamp** type de données. Pour les fonctions CLR, tous les types de données, y compris les types CLR définis par l’utilisateur sont autorisées à l’exception de **texte**, **ntext**, **image**définie par l’utilisateur les types de table et **timestamp** des types de données. Les types non scalaires, **curseur** et **table**, ne peut pas être spécifié comme un type de données de paramètre dans [!INCLUDE[tsql](../../includes/tsql-md.md)] ou des fonctions CLR.  
  
 Si *type_schema_name* n’est pas spécifié, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] recherche le *scalar_parameter_data_type* dans l’ordre suivant :  
  
-   Schéma qui contient les noms des types de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Le schéma par défaut de l'utilisateur actuel dans la base de données active  
  
-   Schéma **dbo** dans la base de données active.  
  
 [=*par défaut* ]  
 Valeur par défaut pour le paramètre. Si un *par défaut* la valeur est définie, la fonction peut être exécutée sans spécifier de valeur pour ce paramètre.  
  
> [!NOTE]  
>  Les valeurs de paramètre par défaut peuvent être spécifiées pour les fonctions CLR à l’exception de la **varchar (max)** et **varbinary (max)** des types de données.  
  
 Lorsque l'un des paramètres de la fonction possède une valeur par défaut, le mot clé DEFAULT doit être spécifié lors de l'appel de la fonction afin de récupérer la valeur par défaut. Ce comportement est différent de l'utilisation de paramètres avec des valeurs par défaut dans des procédures stockées pour lesquelles l'omission du paramètre implique également la prise en compte de la valeur par défaut. Toutefois, le mot clé DEFAULT n'est pas requis lors de l'appel d'une fonction scalaire à l'aide de l'instruction EXECUTE.  
  
 READONLY  
 Indique que le paramètre ne peut pas être mis à jour ni modifié dans la définition de la fonction. Si le type de paramètre est un type de table défini par l'utilisateur, READONLY doit être spécifié.  
  
 *return_data_type*  
 Valeur de retour d'une fonction scalaire définie par l'utilisateur. Pour [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions, tous les types de données, y compris les types CLR définis par l’utilisateur sont autorisées à l’exception de la **timestamp** type de données. Pour les fonctions CLR, tous les types de données, y compris les types CLR définis par l’utilisateur sont autorisées à l’exception de la **texte**, **ntext**, **image**, et **timestamp** des types de données. Les types non scalaires, **curseur** et **table**, ne peut pas être spécifié comme un type de données de retour dans [!INCLUDE[tsql](../../includes/tsql-md.md)] ou des fonctions CLR.  
  
 *function_body*  
 Spécifie qu'une série d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui ne produisent pas ensemble un effet secondaire, tel que la modification d'une table, définissent la valeur de la fonction. *function_body* est utilisé uniquement dans les fonctions scalaires et fonctions table à instructions multiples.  
  
 Dans les fonctions scalaires, *function_body* est une série de [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions ensemble, retournent une valeur scalaire.  
  
 Dans les fonctions table à instructions multiples, *function_body* est une série de [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions remplissent une TABLE de retournent la variable.  
  
 *scalar_expression*  
 Indique la valeur scalaire retournée par la fonction scalaire.  
  
 TABLE  
 Indique que la valeur de retour de la fonction table est une table. Seules les constantes et @*local_variables* peuvent être passés aux fonctions table.  
  
 Dans les fonctions table en ligne, la valeur de retour TABLE est définie par le biais d'une instruction SELECT unique. Aucune variable retournée n'est associée à une fonction en ligne.  
  
 Dans les fonctions table à instructions multiples, @*return_variable* est une variable TABLE, utilisée pour stocker et accumuler les lignes qui doivent être retournés en tant que la valeur de la fonction. @*return_variable* peut uniquement être spécifiée pour [!INCLUDE[tsql](../../includes/tsql-md.md)] des fonctions et pas pour les fonctions CLR.  
  
> [!WARNING]  
>  Jointure à une table à instructions multiples de la fonction de table un **FROM** clause est possible, mais peut donner des performances médiocres. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas en mesure d'utiliser toutes les techniques optimisées sur certaines instructions pouvant être incluses dans une fonction à instructions multiples, par conséquent le plan de requête ne sera pas optimal. Pour obtenir de meilleures performances, quand cela est possible, utilisez des jointures entre les tables de base au lieu des fonctions.  
  
 *select_stmt*  
 Représente l'instruction SELECT unique qui définit la valeur de retour d'une fonction table en ligne.  
  
 COMMANDE (\<order_clause >) spécifie l’ordre dans lequel les résultats sont retournés à partir de la fonction table. Pour plus d'informations, consultez la section « Instructions d'utilisation de l'ordre de tri », plus loin dans cette rubrique.  
  
 NOM externe \<method_specifier > *assembly_name*. *CLASS_NAME*. *nom_méthode* **s’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie l'assembly et la méthode auxquels doit se référer le nom de la fonction créée.  
  
-   *ASSEMBLY_NAME* -doit correspondre à une valeur dans la `name` colonne de   
    `SELECT * FROM sys.assemblies;`.  
    Il s'agit du nom qui a été utilisé dans l'instruction `CREATE ASSEMBLY`.  
  
-   *CLASS_NAME* -doit correspondre à une valeur dans la `assembly_name` colonne de  
    `SELECT * FROM sys.assembly_modules;`.  
    La valeur contient souvent un point incorporé. Dans ce cas, l’instruction Transact-SQL syntaxe requiert que la valeur soit délimitée par une paire de crochets droits [], ou avec une paire de guillemets doubles « ».  
  
-   *nom_méthode* -doit correspondre à une valeur dans la `method_name` colonne de   
    `SELECT * FROM sys.assembly_modules;`.  
    La méthode doit être statique.  
  
 Dans un exemple classique, pour MyFood.DLL, dans lequel tous les types sont dans l'espace de noms MyFood, la valeur `EXTERNAL NAME` peut être :   
`MyFood.[MyFood.MyClass].MyStaticMethod`  
  
> [!NOTE]  
>  Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas exécuter du code CLR. Vous pouvez créer, modifier et supprimer des objets de base de données qui référencent des modules de runtime de langage commun ; Toutefois, vous ne pouvez pas exécuter ces références dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jusqu'à ce que vous activiez la [option clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md). Pour activer cette option, utilisez [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
> [!NOTE]  
>  Cette option n'est pas disponible dans une base de données à relation contenant-contenu.  
  
 *\<*table_type_definition *>*  ({ \<column_definition > \<column_constraint > | \<computed_column_definition >}    [ \<table_constraint >] [ ,...*n*  ]) Définit les données de table de type pour un [!INCLUDE[tsql](../../includes/tsql-md.md)] (fonction). La déclaration de table comprend des définitions de colonne et des contraintes de colonne ou de table. La table est toujours placée dans le groupe de fichiers primaire.  
  
 \<clr_table_type_definition > ({ *column_name**data_type* } [ ,...*n*  ]) **S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([Aperçu dans certaines régions](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)). |  
  
 Définit les types de données de table pour une fonction CLR. La déclaration de table ne comprend que des types de données et des noms de colonne. La table est toujours placée dans le groupe de fichiers primaire.  
  
 NULL | NON NULL  
 Prise en charge uniquement pour les fonctions définies par l’utilisateur scalaires compilées en mode natif. Pour plus d’informations, consultez [Scalar User-Defined des fonctions pour l’OLTP en mémoire](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
 NATIVE_COMPILATION  
 Indique si une fonction définie par l’utilisateur est en mode natif compilée. Cet argument est obligatoire pour les fonctions définies par l’utilisateur scalaires compilées en mode natif.  
  
 BEGIN ATOMIC AVEC  
 Cette prise en charge uniquement pour compilées en mode natif, fonctions scalaires définies par l’utilisateur et est obligatoire. Pour plus d’informations, consultez [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md).  
  
 SCHEMABINDING  
 L’argument SCHEMABINDING est requis pour les fonctions définies par l’utilisateur scalaires compilées en mode natif.  
  
 EXECUTE AS  
 EXECUTE AS est requise pour les fonctions définies par l’utilisateur scalaires compilées en mode natif.  
  
 **\<function_option > :: = et \<clr_function_option > :: =** 
  
 Spécifie que la fonction aura une ou plusieurs des options ci-dessous.  
  
 ENCRYPTION  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indique que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] se charge de convertir le texte d'origine provenant de l'instruction CREATE FUNCTION dans un format obscurci. La sortie générée par l'obfuscation n'est pas visible directement dans les affichages catalogue. Les utilisateurs n'ayant pas accès aux tables système ou aux fichiers de base de données ne peuvent pas récupérer le texte d'obfuscation. Toutefois, le texte sera disponible pour les utilisateurs disposant de privilèges qui peuvent accéder soit les tables système via la [port DAC](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md) ou accéder directement aux fichiers de base de données. Les utilisateurs qui peuvent associer un débogueur au processus serveur peuvent également récupérer la procédure d'origine de la mémoire au moment de l'exécution. Pour plus d’informations sur l’accès aux métadonnées système, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
 L'utilisation cette option empêche la publication de la fonction dans le cadre de la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option ne peut pas être spécifiée pour les fonctions CLR.  
  
 SCHEMABINDING  
 Indique que la fonction est liée aux objets de base de données auxquels elle fait référence. Si SCHEMABINDING est précisé, les objets de base ne peuvent pas être modifiés d'une manière susceptible d'affecter la définition de la fonction. Cette dernière doit d'ailleurs être modifiée ou supprimée au préalable pour supprimer les dépendances par rapport à l'objet qui doit être modifié.  
  
 La liaison de la fonction aux objets auxquels elle fait référence est supprimée uniquement lorsqu'une des actions suivantes se produit : 
  
-   La fonction est supprimée.  
  
-   La fonction est modifiée, avec l'instruction ALTER, sans spécification de l'option SCHEMABINDING.  
  
 Une fonction peut être liée au schéma uniquement si les conditions suivantes sont vérifiées :  
  
-   La fonction est une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Les fonctions utilisateur et vues référencées par la fonction sont également liées au schéma.  
  
-   La fonction fait référence aux objets à partir d'un nom en deux parties.  
  
-   La fonction et les objets auxquels elle fait référence appartiennent à la même base de données.  
  
-   L'utilisateur qui exécute l'instruction CREATE FUNCTION dispose de l'autorisation REFERENCES pour les objets de base de données auxquels la fonction fait référence.  
  
 RETOURNE LA VALEUR NULL EN ENTRÉE NULL | **APPELÉE SUR UNE ENTRÉE NULL**  
 Spécifie le **OnNULLCall** attribut d’une fonction scalaire. S'il n'est pas spécifié, l'argument CALLED ON NULL INPUT est implicite par défaut. Cela signifie que le corps de la fonction est exécuté même si la valeur NULL est transmise comme argument.  
  
 Si l'argument RETURNS NULL ON NULL INPUT est spécifié dans une fonction CLR, il indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner la valeur NULL lorsque n'importe lequel des arguments qu'il reçoit a la valeur NULL, sans réellement appeler le corps de la fonction. Si la méthode d’une fonction CLR spécifiée dans \<method_specifier > possède déjà un attribut personnalisé qui indique RETURNS NULL ON NULL INPUT, mais l’instruction CREATE FUNCTION indique CALLED ON NULL INPUT, l’instruction CREATE FUNCTION est prioritaire. Le **OnNULLCall** attribut ne peut pas être spécifié pour les fonctions table CLR. 
  
 Clause EXECUTE AS  
 Spécifie le contexte de sécurité dans lequel la fonction définie par l'utilisateur est exécutée. Par conséquent, vous pouvez contrôler le compte d’utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise pour valider les autorisations sur tous les objets de base de données qui sont référencées par la fonction.  
  
> [!NOTE]  
>  La clause EXECUTE AS ne peut pas être spécifiée pour les fonctions incluses définies par l'utilisateur.  
  
 Pour plus d’informations, consultez [Clause EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 **\<column_definition > :: =** 
  
 Définit le type de données de la table. La déclaration de table comprend des contraintes et des définitions de colonne. Pour les fonctions CLR, uniquement *column_name* et *data_type* peut être spécifié.  
  
 *nom_colonne*  
 Nom d'une colonne de la table. Les noms de colonnes doivent respecter les règles des identificateurs et doivent être uniques au sein de la table. *column_name* peut comporter entre 1 et 128 caractères.  
  
 *data_type*  
 Indique le type de données de la colonne. Pour [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions, tous les types de données, y compris les types CLR définis par l’utilisateur sont autorisées à l’exception de **timestamp**. Pour les fonctions CLR, tous les types de données, y compris les types CLR définis par l’utilisateur sont autorisées à l’exception de **texte**, **ntext**, **image**, **char**, **varchar**, **varchar (max)**, et **timestamp**. Le type non scalaires **curseur** ne peut pas être spécifié comme type de données de colonne, que ce soit [!INCLUDE[tsql](../../includes/tsql-md.md)] ou des fonctions CLR.  
  
 Par défaut *expression_constante*  
 Spécifie la valeur fournie pour la colonne lorsque vous n'avez pas spécifié explicitement de valeur lors d'une insertion. *expression_constante* est une constante, NULL ou une valeur de la fonction système. Les définitions DEFAULT peuvent être appliquées à n'importe quelle colonne, sauf à celles qui possèdent la propriété IDENTITY. L'argument DEFAULT ne peut pas être spécifié pour les fonctions table CLR.  
  
 COLLATE *collation_name*  
 Indique le classement de la colonne. Si l'argument n'est pas spécifié, c'est le classement par défaut de la base de données qui est affecté à la colonne. Le nom du classement peut être un nom de classement Windows ou SQL. Pour obtenir la liste des et plus d’informations sur les classements, consultez [nom de classement Windows &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md) et [SQL Server nom du classement &#40; Transact-SQL &#41; ](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 La clause COLLATE peut être utilisée pour modifier seulement les classements des colonnes de la **char**, **varchar**, **nchar**, et **nvarchar** des types de données.  
  
 L'argument COLLATE ne peut pas être spécifié pour les fonctions table CLR.  
  
 ROWGUIDCOL  
 Indique que la nouvelle colonne est une colonne d'identificateur unique global de ligne. Seul **uniqueidentifier** colonne par table peut être désignée comme colonne ROWGUIDCOL. La propriété ROWGUIDCOL peut être affectée qu’à un **uniqueidentifier** colonne.  
  
 La propriété ROWGUIDCOL n'assure pas l'unicité des valeurs stockées dans la colonne. Elle ne peut de plus générer automatiquement de valeurs pour les nouvelles lignes insérées dans la table. Pour générer des valeurs uniques pour chaque colonne, utilisez la fonction NEWID dans des instructions INSERT. Une valeur par défaut peut être spécifiée, mais ce ne peut pas être NEWID.  
  
 IDENTITY  
 Indique que la nouvelle colonne est une colonne d'identité. Lorsqu'une ligne est ajoutée à la table, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affecte une valeur incrémentée unique à la colonne. Les colonnes d'identité sont généralement utilisées avec les contraintes PRIMARY KEY comme identificateur unique de ligne pour la table. La propriété IDENTITY peut être affectée à **tinyint**, **smallint**, **int**, **bigint**, **decimal(p,0)**, ou **numeric(p,0)** colonnes. Une seule colonne d'identité peut être créée par table. Il n'est pas possible d'utiliser des valeurs par défaut liées et des contraintes DEFAULT avec une colonne d'identité. Vous devez spécifier à la fois le *seed* et *incrément* ou aucun. Si vous n'en spécifiez aucun, la valeur par défaut est (1,1).  
  
 L'argument IDENTITY ne peut pas être spécifié pour les fonctions table CLR.  
  
 *valeur initiale*  
 Entier à affecter à la première ligne de la table.  
  
 *incrément*  
 Valeur entière à ajouter à la *seed* valeur pour les lignes de la table.  
  
 **\<column_constraint > :: = et \< table_constraint > :: =** 
  
 Définit la contrainte d'une colonne ou table spécifiée. Dans le cas des fonctions CLR, le seul type de contrainte autorisé est NULL. L'utilisation de contraintes nommées n'est pas autorisée.  
  
 NULL | NOT NULL  
 Détermine si les valeurs Null sont autorisées dans la colonne. NULL n'est pas strictement une contrainte, mais peut être spécifié comme NOT NULL. L'argument NOT NULL ne peut pas être spécifié pour les fonctions table CLR.  
  
 PRIMARY KEY  
 Contrainte assurant l'intégrité de l'entité d'une colonne spécifiée au moyen d'un index unique. Dans les fonctions table définies par l'utilisateur, la contrainte PRIMARY KEY ne peut être créée que sur une colonne par table. L'argument PRIMARY KEY ne peut pas être spécifié pour les fonctions table CLR.  
  
 UNIQUE  
 Contrainte assurant l'intégrité de l'entité d'une colonne ou de plusieurs colonnes spécifiées au moyen d'un index unique. Une table peut comprendre plusieurs contraintes UNIQUE. L'argument UNIQUE ne peut pas être spécifié pour les fonctions table CLR.  
  
 CLUSTERED et NONCLUSTERED  
 Indique qu'un index, cluster ou non cluster, est créé pour la contrainte PRIMARY KEY ou UNIQUE. Les contraintes PRIMARY KEY utilisent CLUSTERED, tandis que les contraintes UNIQUE recourent à NONCLUSTERED.  
  
 CLUSTERED peut être spécifié pour une seule contrainte. Si CLUSTERED est spécifié pour une contrainte UNIQUE et qu'une contrainte PRIMARY KEY est également spécifiée, la contrainte PRIMARY KEY utilise NONCLUSTERED.  
  
 Les arguments CLUSTERED et NONCLUSTERED ne peuvent pas être spécifiés pour les fonctions table CLR.  
  
 CHECK  
 Contrainte qui assure l'intégrité du domaine en limitant les valeurs possibles pouvant être entrées dans une ou plusieurs colonnes. Les contraintes CHECK ne peuvent pas être spécifiées pour les fonctions table CLR.  
  
 *Logical_Expression*  
 Expression logique qui retourne TRUE ou FALSE.  
  
 **\<computed_column_definition > :: =**  
  
 Spécifie une colonne calculée. Pour plus d’informations sur les colonnes calculées, consultez [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 *nom_colonne*  
 Nom de la colonne calculée.  
  
 *computed_column_expression*  
 Expression définissant la valeur d'une colonne calculée.  
  
 **\<index_option > :: =**  
  
 Spécifie les options de l'index PRIMARY KEY ou UNIQUE. Pour plus d’informations sur les options d’index, consultez [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
 PAD_INDEX = {ON | **OFF** }  
 Spécifie le remplissage de l'index. La valeur par défaut est OFF.  
  
 FILLFACTOR = *facteur de remplissage*  
 Spécifie un pourcentage indiquant le [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit remplir le niveau feuille de chaque page d’index lors de la création d’index ou la modifier. *facteur de remplissage* doit être un entier compris entre 1 et 100. La valeur par défaut est 0.  
  
 IGNORE_DUP_KEY = {ON | **OFF** }  
 Spécifie la réponse d'erreur lorsqu'une opération d'insertion essaie d'insérer des valeurs de clés en double dans un index unique. L'option IGNORE_DUP_KEY s'applique uniquement aux opérations d'insertion après la création ou la régénération de l'index. La valeur par défaut est OFF.  
  
 STATISTICS_NORECOMPUTE = {ON | **OFF** }  
 Spécifie si les statistiques de distribution sont recalculées. La valeur par défaut est OFF.  
  
 ALLOW_ROW_LOCKS = { **ON** | {OFF}  
 Indique si les verrous de ligne sont autorisés ou non. La valeur par défaut est ON.  
  
 ALLOW_PAGE_LOCKS = { **ON** | {OFF}  
 Indique si les verrous de page sont autorisés. La valeur par défaut est ON.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Si une fonction définie par l'utilisateur n'est pas créée avec la clause SCHEMABINDING, les modifications apportées aux objets sous-jacents peuvent affecter la définition de la fonction et produire des résultats inattendus en cas d'appel. Nous vous recommandons d'implémenter l'une des méthodes suivantes pour vous assurer que la fonction ne devient pas obsolète en raison des modifications apportées à ses objets sous-jacents :  
  
-   Spécifiez la clause WITH SCHEMABINDING lors de la création de la fonction. Vous vous assurez ainsi que les objets référencés dans la définition de la fonction ne peuvent pas être modifiés sauf si la fonction est également modifiée.  
  
-   Exécutez le [sp_refreshsqlmodule](../../relational-databases/system-stored-procedures/sp-refreshsqlmodule-transact-sql.md) procédure stockée après la modification de tout objet qui est spécifié dans la définition de la fonction.  
  
## <a name="data-types"></a>Types de données  
 Si les paramètres sont spécifiés dans une fonction CLR, ils doivent être [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] défini précédemment pour les types *scalar_parameter_data_type*. Pour plus d’informations sur la comparaison [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des types de données système pour les types de données de l’intégration de CLR ou [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] types de données common language runtime, consultez [de mappage de données de paramètre CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
 Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour faire référence à la méthode adéquate surchargée dans une classe, la méthode indiquée dans \<method_specifier > doit présenter les caractéristiques suivantes : 
  
-   Recevoir le même nombre de paramètres que ceux spécifiés dans [ ,...*n* ].  
  
-   Recevoir tous les paramètres par valeur, non par référence.  
  
-   Utiliser des types de paramètre compatibles avec ceux spécifiés dans la fonction [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Si le type de données de retour de la fonction CLR spécifie un type de table (RETURNS TABLE), le type de données de retour de la méthode dans \<method_specifier > doit être de type **IEnumerator** ou **IEnumerable**, et il est supposé que l’interface est implémentée par le créateur de la fonction. Contrairement aux [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions, des fonctions CLR ne peut pas inclure des contraintes KEY, UNIQUE ou CHECK primaire dans \<table_type_definition >. Les types de données des colonnes spécifiées dans \<table_type_definition > doivent correspondre les types de colonnes correspondantes du jeu de résultats retourné par la méthode dans \<method_specifier > au moment de l’exécution. Cette vérification de type n'est pas réalisée à la création de la fonction. 
  
 Pour plus d’informations sur la façon de programmer des fonctions CLR, consultez [les fonctions](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md).  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Les fonctions scalaires peuvent être appelées là où sont utilisées les expressions scalaires. C'est notamment le cas dans les colonnes calculées et les définitions de contraintes CHECK. Les fonctions scalaires peuvent également être exécutées à l’aide de la [EXECUTE](../../t-sql/language-elements/execute-transact-sql.md) instruction. Les fonctions scalaires doivent être appelées à l'aide, au moins, du nom en deux parties de la fonction. Pour plus d’informations sur les noms en plusieurs parties, consultez [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md). Les fonctions table peuvent être appelées là où sont autorisées les expressions de table dans la clause FROM des instructions SELECT, INSERT, UPDATE ou DELETE. Pour plus d’informations, consultez [les fonctions définies par l’utilisateur d’exécuter](../../relational-databases/user-defined-functions/execute-user-defined-functions.md).  
  
## <a name="interoperability"></a>Interopérabilité  
 Les instructions suivantes sont valides dans une fonction :  
  
-   Instructions d'affectation  
  
-   Instructions de contrôle de flux à l'exception des instructions TRY...CATCH  
  
-   Instructions DECLARE définissant des variables de données locales et des curseurs locaux  
  
-   Instructions SELECT qui contiennent des listes de sélection avec des expressions affectant des valeurs aux variables locales  
  
-   Opérations de curseur faisant référence à des curseurs locaux déclarés, ouverts, fermés et libérés dans la fonction. Seules les instructions FETCH affectant des valeurs aux variables locales à l'aide de la clause INTO sont autorisées ; les instructions FETCH qui retournent des données au client ne sont pas autorisées.  
  
-   Instructions INSERT, UPDATE et DELETE modifiant des variables de table locales.  
  
-   Instructions EXECUTE appelant des procédures stockées étendues  
  
-   Pour plus d’informations, consultez [définie par l’utilisateur de créer des fonctions &#40; moteur de base de données &#41;](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md).  
  
### <a name="computed-column-interoperability"></a>Interopérabilité des colonnes calculées  
 Les fonctions ont les propriétés suivantes. Les valeurs de ces propriétés déterminent si les fonctions sont utilisables dans des colonnes calculées pouvant être indexées ou rendues persistantes.  
  
|Propriété| Description|Remarques|  
|--------------|-----------------|-----------|  
|**IsDeterministic**|La fonction est déterministe ou non déterministe.|L'accès local aux données est autorisé dans les fonctions déterministes. Par exemple, une fonction est dite déterministe si elle retourne toujours le même résultat chaque fois qu'elle est appelée à l'aide d'un ensemble spécifique de valeurs d'entrée et que la base de données présente le même état.|  
|**IsPrecise**|La fonction est précise ou imprécise.|Les fonctions imprécises contiennent des opérations telles que les opérations à virgule flottante.|  
|**IsSystemVerified**|Les propriétés de précision et de déterminisme de la fonction peuvent être vérifiées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].||  
|**SystemDataAccess**|La fonction accède aux données système (catalogues système ou tables système virtuelles) dans l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].||  
|**UserDataAccess**|La fonction accède aux données utilisateur dans l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Comprend les tables définies par l'utilisateur et les tables temporaires, mais pas les variables de table.|  
  
 Les propriétés de précision et de déterminisme des fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] sont automatiquement déterminées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les propriétés d'accès aux données et de déterminisme des fonctions CLR peuvent être spécifiées par l'utilisateur. Pour plus d’informations, consultez [vue d’ensemble du CLR Integration Custom Attributes](http://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820).  
  
 Pour afficher les valeurs actuelles de ces propriétés, utilisez [OBJECTPROPERTYEX](../../t-sql/functions/objectpropertyex-transact-sql.md).  
  
 Les fonctions doivent être créées avec une liaison de schéma pour être déterministes.  
  
 Une colonne calculée qui appelle une fonction définie par l'utilisateur peut être utilisée dans un index lorsque la fonction possède les valeurs de propriété suivantes :  
  
-   **IsDeterministic** = true  
  
-   **IsSystemVerified** = true (sauf si la colonne calculée est persistante)  
  
-   **UserDataAccess** = false  
  
-   **SystemDataAccess** = false  
  
 Pour plus d'informations, consultez [Indexes on Computed Columns](../../relational-databases/indexes/indexes-on-computed-columns.md).  
  
### <a name="calling-extended-stored-procedures-from-functions"></a>Appel de procédures stockées étendues à partir de fonctions  
 Une procédure stockée étendue appelée à partir d'une fonction ne peut pas retourner de jeux de résultats au client. Les API ODS qui retournent des jeux de résultats au client retournent FAIL. La procédure stockée étendue peut se reconnecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; toutefois, elle ne doit pas joindre la même transaction que la fonction l'ayant appelée.  
  
 À l'image des appels à partir d'un lot ou d'une procédure stockée, la procédure stockée étendue est exécutée dans le contexte du compte de sécurité Windows sous lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est exécuté. Le propriétaire de la procédure stockée doit tenir compte de cet élément lors de l'octroi de l'autorisation EXECUTE sur la procédure.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Les fonctions définies par l'utilisateur ne permettent pas d'exécuter des actions qui modifient l'état des bases de données.  
  
 Les fonctions définies par l'utilisateur ne peuvent pas contenir de clause OUTPUT INTO avec une table comme cible.  
  
 Les instructions [!INCLUDE[ssSB](../../includes/sssb-md.md)] suivantes ne peuvent pas être incluses dans la définition d'une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] définie par l'utilisateur :  
  
-   BEGIN DIALOG CONVERSATION  
  
-   END CONVERSATION  
  
-   GET CONVERSATION GROUP  
  
-   MOVE CONVERSATION  
  
-   RECEIVE  
  
-   SEND  
  
 Les fonctions définies par l'utilisateur peuvent être imbriquées ; en d'autres termes, une fonction définie par l'utilisateur peut en appeler une autre. Le niveau d'imbrication est incrémenté lorsque la fonction appelée commence à s'exécuter, et décrémenté lorsque l'exécution est terminée. Les fonctions définies par l'utilisateur peuvent être imbriquées jusqu'à 32 niveaux. Le dépassement des niveaux d'imbrication maximum autorisés, provoque l'échec de la totalité de la chaîne de fonctions appelantes. Toute référence à du code managé depuis une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] définie par l'utilisateur compte pour un niveau parmi les 32 niveaux d'imbrication possibles. Les méthodes appelées à partir du code managé ne comptent pas par rapport à cette limite.  
  
### <a name="using-sort-order-in-clr-table-valued-functions"></a>Utilisation de l'ordre de tri dans les fonctions table CLR  
 Lorsque vous utilisez la clause ORDER dans des fonctions table CLR, prenez en compte les indications suivantes :  
  
-   Vous devez faire en sorte que les résultats soient toujours triés dans l'ordre spécifié. Si les résultats ne sont pas dans l'ordre spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] générera un message d'erreur lors de l'exécution de la requête.  
  
-   Si une clause ORDER est spécifiée, la sortie de la fonction table doit être triée en fonction du classement de la colonne (explicite ou implicite). Par exemple, si le classement de la colonne est chinois (spécifié dans le DDL pour la fonction table ou obtenu à partir du classement de la base de données), les résultats retournés doivent être triés conformément aux règles de tri chinoises.  
  
-   La clause ORDER, si elle est spécifiée, est toujours vérifiée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsque des résultats sont retournés, qu'elle soit utilisée ou non par le processeur de requêtes pour effectuer des optimisations supplémentaires. Utilisez la clause ORDER seulement si vous savez que cela est utile pour le processeur de requêtes.  
  
-   Le processeur de requêtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tire automatiquement parti de la clause ORDER dans les cas suivants :  
  
    -   Requêtes Insert dans lesquelles la clause ORDER est compatible avec un index.  
  
    -   Clauses ORDER BY qui sont compatibles avec la clause ORDER.  
  
    -   Agrégats dans lesquels GROUP BY est compatible avec la clause ORDER.  
  
    -   Agrégats DISTINCT dans lesquels les colonnes distinctes sont compatibles avec la clause ORDER.  
  
 La clause ORDER ne garantit pas des résultats ordonnés lorsqu'une requête SELECT est exécutée, sauf si la clause ORDER BY est également spécifiée dans la requête. Consultez [sys.function_order_columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-function-order-columns-transact-sql.md) pour plus d’informations sur la façon de rechercher des colonnes incluses dans l’ordre de tri pour les fonctions table.  
  
## <a name="metadata"></a>Métadonnées  
 Le tableau suivant répertorie les affichages catalogue système que vous pouvez utiliser pour retourner des métadonnées sur les fonctions définies par l'utilisateur.  
  
|Affichage système| Description|  
|-----------------|-----------------|  
|[sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)|Consultez l’exemple E dans la section exemples ci-dessous.|  
|[Sys.assembly_modules](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)|Affiche des informations sur les fonctions définies par l'utilisateur CLR.|  
|[Sys.Parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)|Affiche des informations sur les paramètres définis dans les fonctions définies par l'utilisateur.|  
|[sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)|Affiche les objets sous-jacents référencés par une fonction.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CREATE FUNCTION dans la base de données et l'autorisation ALTER sur le schéma dans lequel la fonction est en cours de création. Si la fonction spécifie un type défini par l'utilisateur, elle requiert l'autorisation EXECUTE sur le type.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-a-scalar-valued-user-defined-function-that-calculates-the-iso-week"></a>A. Utilisation d'une fonction scalaire définie par l'utilisateur calculant la semaine ISO  
 L'exemple suivant crée la fonction définie par l'utilisateur `ISOweek`. Cette fonction contient un argument date et calcule le numéro de semaine ISO. Pour que ce calcul puisse être correctement réalisé, `SET DATEFIRST 1` doit être appelée avant la fonction.  
  
 L’exemple illustre également l’utilisation du [EXECUTE AS](../../t-sql/statements/execute-as-clause-transact-sql.md) clause pour spécifier le contexte de sécurité dans lequel une procédure stockée peut être exécutée. Dans l'exemple, l'option `CALLER` spécifie que la procédure sera exécutée dans le contexte de l'utilisateur qui l'appelle. Les autres options que vous pouvez spécifier sont SELF, OWNER et *nom_utilisateur*.  
  
 Voici l'appel de la fonction. Notez que `DATEFIRST` a la valeur `1`.  
  
```tsql
CREATE FUNCTION dbo.ISOweek (@DATE datetime)  
RETURNS int  
WITH EXECUTE AS CALLER  
AS  
BEGIN  
     DECLARE @ISOweek int;  
     SET @ISOweek= DATEPART(wk,@DATE)+1  
          -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104');  
--Special cases: Jan 1-3 may belong to the previous year  
     IF (@ISOweek=0)   
          SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1   
               AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1;  
--Special case: Dec 29-31 may belong to the next year  
     IF ((DATEPART(mm,@DATE)=12) AND   
          ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28))  
          SET @ISOweek=1;  
     RETURN(@ISOweek);  
END;  
GO  
SET DATEFIRST 1;  
SELECT dbo.ISOweek(CONVERT(DATETIME,'12/26/2004',101)) AS 'ISO Week';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
``` 
ISO Week  
----------------  
52  
```  
  
### <a name="b-creating-an-inline-table-valued-function"></a>B. Création d'une fonction table incluse  
 L'exemple suivant retourne une fonction table incluse dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Il retourne trois colonnes `ProductID`, `Name` et l’agrégation des totaux year-to-date par magasin sous `YTD Total` pour chaque produit vendu au magasin.  
  
```tsql  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
GO  
```

 Pour appeler la fonction, exécutez la requête suivante :    

```tsql  
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
### <a name="c-creating-a-multi-statement-table-valued-function"></a>C. Création d'une fonction table à instructions multiples  
 L'exemple suivant crée la fonction table `fn_FindReports(InEmpID)` dans la base de données AdventureWorks2012. Lorsqu'elle est fournie avec un ID d'employé valide, la fonction retourne une table répertoriant tous les employés qui rendent compte à l'employé directement ou indirectement. La fonction utilise une expression de table commune (CTE, Common Table Expression) récursive pour générer la liste hiérarchique des employés. Pour plus d’informations sur CTE récursives, consultez [avec common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
```tsql  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        -- Get the initial list of Employees for Manager n
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0   
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        -- Join recursive member to anchor
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1   
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);   
  
GO  
```  
  
### <a name="d-creating-a-clr-function"></a>D. Création d'une fonction CLR  
 L’exemple crée la fonction CLR `len_s`. Avant que la fonction ne soit créée, l'assembly `SurrogateStringFunction.dll` est inscrit dans la base de données locale.  
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```tsql  
DECLARE @SamplesPath nvarchar(1024);  
-- You may have to modify the value of this variable if you have  
-- installed the sample in a location other than the default location.  
SELECT @SamplesPath = REPLACE(physical_name, 'Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\master.mdf', 
                                              'Microsoft SQL Server\130\Samples\Engine\Programmability\CLR\')   
    FROM master.sys.database_files   
    WHERE name = 'master';  
  
CREATE ASSEMBLY [SurrogateStringFunction]  
FROM @SamplesPath + 'StringManipulate\CS\StringManipulate\bin\debug\SurrogateStringFunction.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION [dbo].[len_s] (@str nvarchar(4000))  
RETURNS bigint  
AS EXTERNAL NAME [SurrogateStringFunction].[Microsoft.Samples.SqlServer.SurrogateStringFunction].[LenS];  
GO  
```  
  
 Pour obtenir un exemple montrant comment créer une fonction table CLR, consultez [fonctions table du CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md).  
  
### <a name="e-displaying-the-definition-of-includetsqlincludestsql-mdmd-user-defined-functions"></a>E. Affichage de la définition de [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions définies par l’utilisateur  
  
```tsql  
SELECT definition, type   
FROM sys.sql_modules AS m  
JOIN sys.objects AS o ON m.object_id = o.object_id   
    AND type IN ('FN', 'IF', 'TF');  
GO  
```  
  
 La définition de fonctions créées à l'aide de l'option ENCRYPTION ne peut pas être affichée à l'aide de sys.sql_modules ; toutefois, d'autres informations sur les fonctions chiffrées apparaissent.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-function-transact-sql.md)   
 [DROP FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-function-transact-sql.md)   
 [OBJECTPROPERTYEX &#40; Transact-SQL &#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [Fonctions CLR définies par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [CRÉER une stratégie de sécurité &#40; Transact-SQL &#41;](../../t-sql/statements/create-security-policy-transact-sql.md)  
  
 


