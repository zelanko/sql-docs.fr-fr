---
title: ALTER FUNCTION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_FUNCTION_TSQL
- ALTER FUNCTION
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER FUNCTION statement
- modifying functions
- functions [SQL Server], modifying
ms.assetid: 89f066ee-05ac-4439-ab04-d8c3d5911179
caps.latest.revision: 62
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3da4c3a8e76a48db0eee940e969ddf24dc147149
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-function-transact-sql"></a>ALTER FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Modifie une fonction existante [!INCLUDE[tsql](../../includes/tsql-md.md)] ou CLR, créée précédemment à l'aide de l'instruction CREATE FUNCTION, sans changer les autorisations ni affecter les fonctions, les procédures stockées ou les déclencheurs dépendant de celle-ci.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Transact-SQL Scalar Function Syntax    
ALTER FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ = default ] }   
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
ALTER FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
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
-- Transact-SQL Multistatement Table-valued Function Syntax
ALTER FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
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
-- CLR Scalar and Table-Valued Function Syntax
ALTER FUNCTION [ schema_name. ] function_name   
( { @parameter_name [AS] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
)  
RETURNS { return_data_type | TABLE <clr_table_type_definition> }  
    [ WITH <clr_function_option> [ ,...n ] ]  
    [ AS ] EXTERNAL NAME <method_specifier>  
[ ; ]  
```
  
```
-- CLR Function Clauses
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
-- Syntax for In-Memory OLTP: Natively compiled, scalar user-defined function  
ALTER FUNCTION [ schema_name. ] function_name    
 ( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ NULL | NOT NULL ] [ = default ] }   
    [ ,...n ]   
  ]   
)   
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]   
    [ AS ]   
    BEGIN ATOMIC WITH (set_option [ ,... n ])  
        function_body   
        RETURN scalar_expression  
    END  
    
<function_option>::=   
{ |  NATIVE_COMPILATION   
  |  SCHEMABINDING   
  | [ EXECUTE_AS_Clause ]   
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]   
}  
```   
  
## <a name="arguments"></a>Arguments  
 *schema_name*  
 Nom du schéma auquel appartient la fonction définie par l'utilisateur.  
  
 *nom de la fonction*  
 Fonction à modifier, définie par l'utilisateur.  
  
> [!NOTE]  
>  Les parenthèses sont requises après le nom de fonction même si aucun paramètre n'est spécifié.  
  
 **@***nom_paramètre*  
 Paramètre dans la fonction définie par l'utilisateur. Un ou plusieurs paramètres peuvent être déclarés.  
  
 Une fonction peut comprendre au maximum 2 100 paramètres. La valeur de chaque paramètre déclaré doit être fournie par l'utilisateur lors de l'exécution de la fonction, sauf si vous définissez une valeur par défaut pour le paramètre.  
  
 Spécifiez un nom de paramètre à l’aide un arobase (**@**) comme premier caractère. Le nom du paramètre doit respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md). Un paramètre étant local à une fonction, vous pouvez utiliser le même nom dans d'autres fonctions. Les paramètres ne peuvent que prendre la place de constantes ; ils ne peuvent pas être utilisés à la place de noms de tables, de colonnes ou d'autres objets de base de données.  
  
> [!NOTE]  
>  L'option ANSI_WARNINGS n'est pas reconnue lors d'un passage de paramètres dans une procédure stockée ou dans une fonction définie par l'utilisateur, ou bien lors de la déclaration et de la définition de variables dans une instruction par lot. Par exemple, si une variable est définie en tant que **char (3)**, puis définissez une valeur supérieure à trois caractères, les données sont tronquées à la taille définie et l’insertion ou instruction de mise à jour réussit.  
  
 [ *type_schema_name.* ] *parameter_data_type*  
 Type de données de paramètre et, éventuellement, schéma auquel il appartient. Pour [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions, tous les types de données, y compris les types CLR définis par l’utilisateur sont autorisées à l’exception de la **timestamp** type de données. Pour les fonctions CLR, tous les types de données, y compris les types CLR définis par l’utilisateur sont autorisées à l’exception de **texte**, **ntext**, **image**, et **timestamp** des types de données. Les types non scalaires **curseur** et **table** ne peut pas être spécifié comme un type de données de paramètre dans [!INCLUDE[tsql](../../includes/tsql-md.md)] ou des fonctions CLR.  
  
 Si *type_schema_name* n’est pas spécifié, le [!INCLUDE[ssDEversion2005](../../includes/ssdeversion2005-md.md)] recherche le *parameter_data_type* dans l’ordre suivant :  
  
-   Schéma qui contient les noms des types de données système SQL Server.  
  
-   Le schéma par défaut de l'utilisateur actuel dans la base de données active  
  
-   Schéma **dbo** dans la base de données active.  
  
 [  **=**  *par défaut* ]  
 Valeur par défaut pour le paramètre. Si un *par défaut* la valeur est définie, la fonction peut être exécutée sans spécifier de valeur pour ce paramètre.  
  
> [!NOTE]  
>  Les valeurs de paramètre par défaut peuvent être spécifiées pour les fonctions CLR à l’exception de **varchar (max)** et **varbinary (max)** des types de données.  
  
 Lorsqu'un des paramètres de la fonction possède une valeur par défaut, le mot clé DEFAULT doit être spécifié lors de l'appel de la fonction afin d'extraire la valeur par défaut. Ce comportement est différent de l'utilisation de paramètres avec des valeurs par défaut dans des procédures stockées pour lesquelles l'omission du paramètre implique également la prise en compte de la valeur par défaut.  
  
 *return_data_type*  
 Valeur de retour d'une fonction scalaire définie par l'utilisateur. Pour [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctions, tous les types de données, y compris les types CLR définis par l’utilisateur sont autorisées à l’exception de la **timestamp** type de données. Pour les fonctions CLR, tous les types de données, y compris les types CLR définis par l’utilisateur sont autorisées à l’exception de **texte**, **ntext**, **image**, et **timestamp** des types de données. Les types non scalaires **curseur** et **table** ne peut pas être spécifié comme un type de données de retour dans [!INCLUDE[tsql](../../includes/tsql-md.md)] ou des fonctions CLR.  
  
 *function_body*  
 Spécifie qu'une série d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui ne produisent pas ensemble un effet secondaire, tel que la modification d'une table, définissent la valeur de la fonction. *function_body* est utilisé uniquement dans les fonctions scalaires et fonctions table à instructions multiples.  
  
 Dans les fonctions scalaires, *function_body* est une série de [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions ensemble, retournent une valeur scalaire.  
  
 Dans les fonctions table à instructions multiples, *function_body* est une série de [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions remplissent une TABLE de retournent la variable.  
  
 *scalar_expression*  
 Indique que la fonction scalaire retourne une valeur scalaire.  
  
 TABLE  
 Indique que la valeur de retour de la fonction table est une table. Seules les constantes et  **@**  *local_variables* peuvent être passés aux fonctions table.  
  
 Dans les fonctions table en ligne, la valeur de retour TABLE est définie par le biais d'une instruction SELECT unique. Aucune variable retournée n'est associée à une fonction en ligne.  
  
 Dans les fonctions table à instructions multiples,  **@**  *return_variable* est une variable TABLE utilisée pour stocker et accumuler les lignes qui doivent être retournés en tant que la valeur de la fonction. **@***return_variable* peut uniquement être spécifiée pour [!INCLUDE[tsql](../../includes/tsql-md.md)] des fonctions et pas pour les fonctions CLR.  
  
 *Sélectionnez-stmt*  
 Représente l'instruction SELECT unique qui définit la valeur de retour d'une fonction table en ligne.  
  
 NOM externe \<method_specifier >*assembly_name.class_name*. *nom_méthode*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie la méthode d'un assembly à lier avec la fonction. *ASSEMBLY_NAME* doit correspondre à un assembly existant dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la base de données actuelle avec visibilité activée. *CLASS_NAME* doit être valide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificateur et doit exister en tant que classe dans l’assembly. Si la classe a un nom qualifié d’espace de noms qui utilise une période (**.**) pour séparer les parties de l’espace de noms, le nom de classe doit être délimité par des crochets (**[]**) ou des guillemets (**» «**). *nom_méthode* doit être valide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificateur et doit exister en tant que méthode statique dans la classe spécifiée.  
  
> [!NOTE]  
>  Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas exécuter du code CLR. Vous pouvez créer, modifier et supprimer des objets de base de données qui référencent des modules de runtime de langage commun ; Toutefois, vous ne pouvez pas exécuter ces références dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jusqu'à ce que vous activiez la [option clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md). Pour activer l’option, utilisez [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
> [!NOTE]  
>  Cette option n'est pas disponible dans une base de données à relation contenant-contenu.  
  
 *\<*table_type_definition*>***(** { \<column_definition > \<column_constraint > | \<computed_column_definition >} [ \<table_constraint >] [ **,**... *n* ]**)**  
 Définit le type de données de table pour une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)]. La déclaration de table comprend des définitions de colonne et des contraintes de colonne ou de table.  
  
\<clr_table_type_definition > **(** { *column_name**data_type* } [ **,**...  *n*  ] **)** **S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([Aperçu dans certaines régions](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).  
  
 Définit les types de données de table pour une fonction CLR. La déclaration de table ne comprend que des types de données et des noms de colonne.  
  
 NULL | NON NULL  
 Prise en charge uniquement pour les fonctions définies par l’utilisateur scalaires compilées en mode natif. Pour plus d’informations, consultez [Scalar User-Defined des fonctions pour l’OLTP en mémoire](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
 NATIVE_COMPILATION  
 Indique si une fonction définie par l’utilisateur est en mode natif compilée. Cet argument est obligatoire pour les fonctions définies par l’utilisateur scalaires compilées en mode natif.  
  
 L’argument NATIVE_COMPILATION est requis lorsque vous modifiez la fonction et pouvez uniquement être utilisé, si la fonction a été créée avec l’argument NATIVE_COMPILATION.  
  
 BEGIN ATOMIC AVEC  
 Cette prise en charge uniquement pour compilées en mode natif, fonctions scalaires définies par l’utilisateur et est obligatoire. Pour plus d’informations, consultez [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md).  
  
 SCHEMABINDING  
 L’argument SCHEMABINDING est requis pour les fonctions définies par l’utilisateur scalaires compilées en mode natif.  
  
 **\<function_option > :: = et \<clr_function_option > :: =**  
  
 Spécifie que la fonction aura une ou plusieurs des options suivantes.  
  
 ENCRYPTION  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indique que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] chiffre les colonnes d'affichage catalogue qui contiennent le texte de l'instruction ALTER FUNCTION. L'utilisation de l'argument ENCRYPTION évite la publication de la fonction dans le cadre de la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'argument ENCRYPTION ne peut pas être spécifié pour les fonctions CLR.  
  
 SCHEMABINDING  
 Indique que la fonction est liée aux objets de base de données auxquels elle fait référence. Cette condition empêche que des modifications ne soient apportées à la fonction si d'autres objets liés au schéma y font référence.  
  
 La liaison de la fonction aux objets auxquels elle fait référence est supprimée uniquement lorsqu'une des actions suivantes se produit :  
  
-   La fonction est supprimée.  
  
-   La fonction est modifiée, avec l'instruction ALTER, sans spécification de l'option SCHEMABINDING.  
  
Pour obtenir la liste des conditions qui doivent être remplies avant une fonction peut être liée au schéma, consultez [CREATE FUNCTION &#40; Transact-SQL &#41; ](../../t-sql/statements/create-function-transact-sql.md).  
  
 RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT  
 Spécifie le **OnNULLCall** attribut d’une fonction scalaire. S'il n'est pas spécifié, l'argument CALLED ON NULL INPUT est implicite par défaut. Cela signifie que le corps de la fonction est exécuté même si la valeur NULL est transmise comme argument.  
  
 Si l'argument RETURNS NULL ON NULL INPUT est spécifié dans une fonction CLR, il indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner la valeur NULL lorsque n'importe lequel des arguments qu'il reçoit a la valeur NULL, sans réellement appeler le corps de la fonction. Si la méthode spécifiée dans \<method_specifier > possède déjà un attribut personnalisé qui indique RETURNS NULL ON NULL INPUT, mais l’instruction ALTER FUNCTION indique CALLED ON NULL INPUT, l’instruction ALTER FUNCTION est prioritaire. Le **OnNULLCall** attribut ne peut pas être spécifié pour les fonctions table CLR.  
  
 Clause EXECUTE AS  
 Spécifie le contexte de sécurité dans lequel la fonction définie par l'utilisateur est exécutée. Par conséquent, vous pouvez choisir le compte d'utilisateur que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit utiliser pour valider les autorisations sur tous les objets de base de données référencés par la fonction.  
  
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
 Indique le classement de la colonne. Si l'argument n'est pas spécifié, c'est le classement par défaut de la base de données qui est affecté à la colonne. Le nom du classement peut être un nom de classement Windows ou SQL. Pour obtenir la liste des et plus d’informations, consultez [nom de classement Windows &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md) et [SQL Server nom du classement &#40; Transact-SQL &#41; ](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
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
  
 PAD_INDEX = { ON | OFF }  
 Spécifie le remplissage de l'index. La valeur par défaut est OFF.  
  
 FILLFACTOR = *facteur de remplissage*  
 Spécifie un pourcentage indiquant le [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit remplir le niveau feuille de chaque page d’index lors de la création d’index ou la modifier. *facteur de remplissage* doit être un entier compris entre 1 et 100. La valeur par défaut est 0.  
  
 IGNORE_DUP_KEY = { ON | OFF }  
 Spécifie la réponse d'erreur lorsqu'une opération d'insertion essaie d'insérer des valeurs de clés en double dans un index unique. L'option IGNORE_DUP_KEY s'applique uniquement aux opérations d'insertion après la création ou la régénération de l'index. La valeur par défaut est OFF.  
  
 STATISTICS_NORECOMPUTE = { ON | OFF }  
 Spécifie si les statistiques de distribution sont recalculées. La valeur par défaut est OFF.  
  
 ALLOW_ROW_LOCKS = { ON | OFF }  
 Indique si les verrous de ligne sont autorisés ou non. La valeur par défaut est ON.  
  
 ALLOW_PAGE_LOCKS = { ON | OFF }  
 Indique si les verrous de page sont autorisés. La valeur par défaut est ON.  
  
## <a name="remarks"></a>Notes  
 ALTER FUNCTION ne peut pas être utilisé pour convertir une fonction à valeur scalaire en une fonction à valeur de table, et inversement. En outre, ALTER FUNCTION ne peut pas être utilisé pour convertir une fonction Inline en une fonction à instructions multiples, et inversement. ALTER FUNCTION ne peut pas être utilisé pour convertir une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] en une fonction clr, et inversement.  
  
 Les instructions Service Broker suivantes ne peuvent pas être incluses dans la définition d’un [!INCLUDE[tsql](../../includes/tsql-md.md)] fonction définie par l’utilisateur :  
  
-   BEGIN DIALOG CONVERSATION  
-   END CONVERSATION  
-   GET CONVERSATION GROUP  
-   MOVE CONVERSATION  
-   RECEIVE  
-   SEND  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER sur la fonction ou sur le schéma. Si la fonction spécifie un type défini par l'utilisateur, elle requiert l'autorisation EXECUTE sur le type.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [DROP FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-function-transact-sql.md)   
 [Modifier le schéma dans les bases de données de publication](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

