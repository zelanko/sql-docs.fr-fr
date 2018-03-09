---
title: CREATE TYPE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql13.swb.sysdatatype.properties.f1
- CREATE TYPE
- TYPE_TSQL
- TYPE
- CREATE_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [SQL Server], creating
- CLR user-defined types [SQL Server]
- user-defined table types [SQL Server]
- user-defined types [SQL Server], creating
- CREATE TYPE statement
- alias data types [SQL Server], creating
- data types [SQL Server], creating
ms.assetid: 2202236b-e09f-40a1-bbc7-b8cff7488905
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 145f60bcec81e8a29761a44146df025f66a21b80
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="create-type-transact-sql"></a>CREATE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crée un type de données alias ou un type défini par l'utilisateur dans la base de données active [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. L'implémentation d'un type de données d'alias est basé sur un type de système natif [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un type défini par l’utilisateur est implémenté via une classe d’un assembly dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR). Pour lier un type défini par l’utilisateur à son implémentation, l’assembly CLR qui contient l’implémentation du type doit d’abord être enregistré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md).  
  
 La possibilité d'exécuter un code CLR est désactivée par défaut dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez créer, modifier et supprimer des objets de base de données qui référencent des modules de code managé, mais ces références ne se n'exécuteront pas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sauf si le [Option clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) est activé à l’aide de [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
 
> [!NOTE]  
>  L’intégration du CLR .NET Framework dans SQL Server est décrite dans cette rubrique. Intégration du CLR ne s’applique pas à Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Disk-Based Type Syntax  
CREATE TYPE [ schema_name. ] type_name  
{   
    FROM base_type   
    [ ( precision [ , scale ] ) ]  
    [ NULL | NOT NULL ]   
  | EXTERNAL NAME assembly_name [ .class_name ]   
  | AS TABLE ( { <column_definition> | <computed_column_definition> }  
        [ <table_constraint> ] [ ,...n ] )    
} [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]   
    [ NULL | NOT NULL ]  
    [   
        DEFAULT constant_expression ]   
      | [ IDENTITY [ ( seed ,increment ) ]   
    ]  
    [ ROWGUIDCOL ] [ <column_constraint> [ ...n ] ]   
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
                [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH ( <index_option> [ ,...n ] )   
        ]  
  | CHECK ( logical_expression )   
}   
  
<computed_column_definition> ::=  
  
column_name AS computed_column_expression   
[ PERSISTED [ NOT NULL ] ]  
[   
    { PRIMARY KEY | UNIQUE }  
        [ CLUSTERED | NONCLUSTERED ]  
        [   
            WITH ( <index_option> [ ,...n ] )  
        ]  
    | CHECK ( logical_expression )   
]   
  
<table_constraint> ::=  
{   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
    ( column [ ASC | DESC ] [ ,...n ] )   
        [   
    WITH ( <index_option> [ ,...n ] )   
        ]  
    | CHECK ( logical_expression )   
}   
  
<index_option> ::=  
{  
    IGNORE_DUP_KEY = { ON | OFF }  
}  
```  
  
```  
-- Memory-Optimized Table Type Syntax  
CREATE TYPE [schema_name. ] type_name  
AS TABLE ( { <column_definition> }  
    |  [ <table_constraint> ] [ ,... n ]    
    | [ <table_index> ] [ ,... n ]    } )
    [ WITH ( <table_option> [ ,... n ] ) ]  
 [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]   [ NULL | NOT NULL ]    [  
      [ IDENTITY [ (1 , 1) ]  
    ]  
    [ <column_constraint> [ ... n ] ]    [ <column_index> ]  
  
<data type> ::=  
 [type_schema_name . ] type_name [ (precision [ , scale ]) ]  
  
<column_constraint> ::=  
{ PRIMARY KEY {   NONCLUSTERED HASH WITH (BUCKET_COUNT = bucket_count) 
                | NONCLUSTERED } }  
  
< table_constraint > ::=  
{ PRIMARY KEY { NONCLUSTERED HASH (column [ ,... n ] ) 
                   WITH (BUCKET_COUNT = bucket_count) 
               | NONCLUSTERED  (column [ ASC | DESC ] [ ,... n ] )  } }  
  
<column_index> ::=  
  INDEX index_name  
{ { [ NONCLUSTERED ] HASH WITH (BUCKET_COUNT = bucket_count) 
     | NONCLUSTERED } }  
  
< table_index > ::=  
  INDEX constraint_name  
{ { [ NONCLUSTERED ] HASH (column [ ,... n ] ) WITH (BUCKET_COUNT = bucket_count) 
 |  [NONCLUSTERED]  (column [ ASC | DESC ] [ ,... n ] )} }  
  
<table_option> ::=  
{  
    [MEMORY_OPTIMIZED = {ON | OFF}]  
}  
```  
  
## <a name="arguments"></a>Arguments  
 *schema_name*  
 Nom du schéma auquel appartient le type de données d'alias ou défini par l'utilisateur.  
  
 *TYPE_NAME*  
 Nom du type de données d'alias ou défini par l'utilisateur. Les noms de type doivent respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md).  
  
 *base_type*  
 Est le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur lequel est basé le type de données d’alias de type de données fourni. *base_type* est **sysname**, sans valeur par défaut et peut prendre l’une des valeurs suivantes :  
  
|||||  
|-|-|-|-|  
|**bigint**|**binaire (**  *n*  **)**|**bit**|**char (**  *n*  **)**|  
|**date**|**datetime**|**datetime2**|**datetimeoffset**|  
|**decimal**|**float**|**image**|**int**|  
|**money**|**NCHAR (**  *n*  **)**|**ntext**|**numeric**|  
|**nvarchar (**  *n*  &#124; **max)**|**real**|**smalldatetime**|**smallint**|  
|**smallmoney**|**sql_variant**|**text**|**time**|  
|**tinyint**|**uniqueidentifier**|**varbinary (**  *n*  &#124; **max)**|**varchar (**  *n*  &#124; **max)**|  
  
 *base_type* peut également être n’importe quel synonyme de type de données qui correspond à l’un de ces types de données système.  
  
 *precision*  
 Pour **décimal** ou **numérique**, est un entier non négatif qui indique le nombre total maximal de chiffres décimaux pouvant figurer à la fois à gauche et à droite de la virgule décimale. Pour plus d’informations, consultez [decimal et numeric &#40; Transact-SQL &#41; ](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *scale*  
 Pour **décimal** ou **numérique**, est un entier non négatif qui indique le nombre maximal de chiffres décimaux pouvant figurer à droite de la virgule décimale, et elle doit être inférieure ou égale à la précision. Pour plus d’informations, consultez [decimal et numeric &#40; Transact-SQL &#41; ](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 **NULL** | NON NULL  
 Précise si le type accepte les valeurs NULL. S'il n'est pas spécifié, la valeur par défaut est NULL.  
  
 *ASSEMBLY_NAME*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assembly qui fait référence à l’implémentation du type défini par l’utilisateur dans le common language runtime. *ASSEMBLY_NAME* doit correspondre à un assembly existant dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la base de données actuelle.  
  
> [!NOTE]  
>  EXTERNAL_NAME n'est pas disponible dans une base de données à relation contenant-contenu.  
  
 **[.** *CLASS_NAME***]**   
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie la classe au sein de l'assembly qui implémente le type défini par l'utilisateur. *CLASS_NAME* doit être un identificateur valid et doit exister en tant que classe dans l’assembly avec une visibilité de l’assembly. *CLASS_NAME* respecte la casse, quel que soit le classement de base de données et doit correspondre exactement le nom de classe dans l’assembly correspondant. Le nom de classe peut être un nom qualifié d’espace de noms entouré crochets (**[]**) si le langage de programmation qui est utilisé pour écrire la classe utilise le concept d’espaces de noms, tel que c#. Si *class_name* n’est pas spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suppose qu’il est identique *type_name*.  
  
 \<column_definition >  
 Définit les colonnes pour un type de table défini par l'utilisateur.  
  
 \<type de données >  
 Définit le type de données dans une colonne pour un type de table défini par l'utilisateur. Pour plus d’informations sur les types de données, consultez [Types de données &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-types-transact-sql.md). Pour plus d’informations sur les tables, consultez [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<column_constraint >  
 Définit les contraintes de colonnes pour un type de table défini par l'utilisateur. Les contraintes prises en charge incluent PRIMARY KEY, UNIQUE et CHECK. Pour plus d’informations sur les tables, consultez [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<computed_column_definition >  
 Définit une expression de colonne calculée en tant que colonne dans un type de table défini par l'utilisateur. Pour plus d’informations sur les tables, consultez [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<table_constraint >  
 Définit une contrainte de table sur un type de table défini par l'utilisateur. Les contraintes prises en charge incluent PRIMARY KEY, UNIQUE et CHECK.  
  
 \<index_option >  
 Spécifie la réponse aux erreurs de valeurs de clés dupliquées dans une opération d'insertion de plusieurs lignes dans un index cluster unique ou un index non cluster unique. Pour plus d’informations sur les options d’index, consultez [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
 INDEX  
 Vous devez spécifier les index de table et de colonne dans le cadre de l'instruction CREATE TABLE. CREATE INDEX et DROP INDEX ne sont pas pris en charge pour les tables optimisées en mémoire.  
  
 MEMORY_OPTIMIZED  
 **S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Indique si le type de table est optimisé en mémoire. Cette option est désactivée par défaut ; la table (type) n'est pas une table optimisée en mémoire (type). Les types de tables optimisées en mémoire sont des tables utilisateur optimisées en mémoire dont le schéma est rendu persistant sur disque similairement à d'autres tables utilisateur.  
  
 BUCKET_COUNT  
 **S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Indique le nombre de compartiments qui doivent être créés dans l'index de hachage. La valeur maximale de BUCKET_COUNT dans les index de hachage est de 1 073 741 824. Pour plus d’informations sur le nombre de compartiments, consultez [index des Tables mémoire optimisées](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md). *bucket_count* est un argument obligatoire.  
  
 HASH  
 **S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Indique qu'un index HASH est créé. Les index de hachage sont pris en charge uniquement sur les tables optimisées en mémoire.  
  
## <a name="remarks"></a>Notes  
 La classe de l’assembly qui est référencé dans *assembly_name*, ainsi que ses méthodes, doit satisfaire à la configuration requise pour l’implémentation d’un type défini par l’utilisateur dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur ces exigences, consultez [les Types](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
 Les autres considérations portent sur les points suivants :  
  
-   La classe peut avoir des méthodes surchargées, mais ces méthodes ne peuvent être appelées qu'à partir du code managé, et non à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Tous les membres statiques doivent être déclarées comme **const** ou **readonly** si *assembly_name* est SAFE ou EXTERNAL_ACCESS.  
  
 Au sein d'une base de données, il ne peut y avoir qu'un seul type défini par l'utilisateur enregistré par rapport à tout type spécifié qui a été téléchargé dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir du CLR. Si un type de données défini par l'utilisateur est créé sur un type CLR pour lequel le type défini par l'utilisateur existe déjà dans la base de données, CREATE TYPE échoue avec une erreur. Cette restriction est nécessaire pour éviter toute ambiguïté dans la résolution de type SQL si un type CLR peut être mappé à plusieurs types définis par l'utilisateur.  
  
 Si une méthode mutateur dans le type ne renvoie pas *void*, l’instruction CREATE TYPE ne s’exécute pas.  
  
 Pour modifier un type défini par l'utilisateur, vous devez supprimer le type à l'aide d'une instruction DROP TYPE, puis le créer de nouveau.  
  
 Contrairement aux types définis par l’utilisateur qui sont créés à l’aide de **sp_addtype**, le **public** rôle de base de données n’est pas accordée automatiquement l’autorisation REFERENCES sur les types qui sont créés à l’aide de CREATE TYPE. Cette autorisation doit être accordée séparément.  
  
 Dans les types de table défini par l’utilisateur, structurées types définis par l’utilisateur qui sont utilisés dans *column_name* \<type de données > font partie de l’étendue du schéma de base de données dans lequel le type de table est défini. Pour accéder aux types structurés définis par l'utilisateur dans une étendue différente dans la base de données, utilisez des noms en deux parties.  
  
 Dans les types de tables définis par l'utilisateur, la clé primaire sur les colonnes calculées doit être PERSISTED et NOT NULL.  
  
## <a name="memory-optimized-table-types"></a>Types de tables optimisées en mémoire  
 À partir de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], le traitement des données dans un type de table peut être effectué dans la mémoire principale, et non sur disque. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md). Pour obtenir des exemples de code montrant comment créer des types de table mémoire optimisée, consultez [création d’une Table optimisée en mémoire et une en mode natif procédure stockée compilée](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation CREATE TYPE dans la base de données actuelle et l’autorisation ALTER sur *schema_name*. Si *schema_name* n’est pas spécifié, les règles de résolution de noms par défaut pour la détermination du schéma de l’utilisateur actuel s’appliquent. Si *assembly_name* est spécifié, un utilisateur doit soit propriétaire de l’assembly ou avoir l’autorisation REFERENCES sur celui-ci.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-an-alias-type-based-on-the-varchar-data-type"></a>A. Création d'un type d'alias basé sur le type de données varchar  
 L'exemple suivant crée un type d'alias basé sur le type de données `varchar` fourni par le système.  
  
```  
CREATE TYPE SSN  
FROM varchar(11) NOT NULL ;  
```  
  
### <a name="b-creating-a-user-defined-type"></a>B. Création d'un type défini par l'utilisateur  
 L’exemple suivant crée un type `Utf8String` qui fait référence à la classe `utf8string` dans l’assembly `utf8string`. Avant de créer le type, l'assembly `utf8string` est enregistré dans la base de données locale. Remplacez la partie binaire de l'instruction CREATE ASSEMBLY par une description valide.  
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE ASSEMBLY utf8string  
AUTHORIZATION [dbi]   
FROM 0x4D... ;  
GO  
CREATE TYPE Utf8String   
EXTERNAL NAME utf8string.[Microsoft.Samples.SqlServer.utf8string] ;  
GO  
```  
  
### <a name="c-creating-a-user-defined-table-type"></a>C. Création d'un type de table défini par l'utilisateur  
 L'exemple suivant crée un type de table défini par l'utilisateur qui possède deux colonnes. Pour plus d’informations sur la façon de créer et utiliser des paramètres table, consultez [utiliser des paramètres table &#40; moteur de base de données &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
```  
CREATE TYPE LocationTableType AS TABLE   
    ( LocationName VARCHAR(50)  
    , CostRate INT );  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER un ASSEMBLY &#40; Transact-SQL &#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [TYPE de déplacement &#40; Transact-SQL &#41;](../../t-sql/statements/drop-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
