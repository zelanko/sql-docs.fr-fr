---
title: "CRÉER la TABLE (entrepôt de données SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 07/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ea21c73c-40e8-4c54-83d4-46ca36b2cf73
caps.latest.revision: 59
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 11df71495b55ca72074c6ab928caaf6474bb2576
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-azure-sql-data-warehouse"></a>CRÉER la TABLE (entrepôt de données SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Crée une nouvelle table dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
 
Pour comprendre comment les utiliser et les tables, consultez [Tables SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-overview/).

Remarque : Des Discussions sur SQL Data Warehouse dans cet article s’appliquent à SQL Data Warehouse et Parallel Data Warehouse sauf indication contraire. 
 
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

<a name="Syntax"></a>   
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Create a new table. 
CREATE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name   
    ( 
      { column_name <data_type>  [ <column_options> ] } [ ,...n ]   
    )  
    [ WITH [ <table_option> [ ,...n ] ) ]  
[;]  
   
<column_options> ::=
    [ COLLATE Windows_collation_name ]  
    [ NULL | NOT NULL ] -- default is NULL  
    [ [ CONSTRAINT constraint_name ] DEFAULT constant_expression  ]
  
<table_option> ::= 
    {   
        CLUSTERED COLUMNSTORE INDEX --default for SQL Data Warehouse 
      | HEAP --default for Parallel Data Warehouse   
      | CLUSTERED INDEX ( { index_column_name [ ASC | DESC ] } [ ,...n ] ) -- default is ASC 
    }  
    { 
        DISTRIBUTION = HASH ( distribution_column_name ) 
      | DISTRIBUTION = ROUND_ROBIN -- default for SQL Data Warehouse
      | DISTRIBUTION = REPLICATE -- default for Parallel Data Warehouse
    }   
    | PARTITION ( partition_column_name RANGE [ LEFT | RIGHT ] -- default is LEFT  
        FOR VALUES ( [ boundary_value [,...n] ] ) )  
  
<data type> ::=   
      datetimeoffset [ ( n ) ]  
    | datetime2 [ ( n ) ]  
    | datetime  
    | smalldatetime  
    | date  
    | time [ ( n ) ]  
    | float [ ( n ) ]  
    | real [ ( n ) ]  
    | decimal [ ( precision [ , scale ] ) ]   
    | numeric [ ( precision [ , scale ] ) ]   
    | money  
    | smallmoney  
    | bigint  
    | int   
    | smallint  
    | tinyint  
    | bit  
    | nvarchar [ ( n | max ) ]  -- max applies only to SQL Data Warehouse 
    | nchar [ ( n ) ]  
    | varchar [ ( n | max )  ] -- max applies only to SQL Data Warehouse  
    | char [ ( n ) ]  
    | varbinary [ ( n | max ) ] -- max applies only to SQL Data Warehouse  
    | binary [ ( n ) ]  
    | uniqueidentifier  
```  

<a name="Arguments"></a>   
## <a name="arguments"></a>Arguments  
 *database_name*  
 Le nom de la base de données qui contiendra la nouvelle table. La valeur par défaut est la base de données active.  
  
 *schema_name*  
 Le schéma pour la table. Spécification de *schéma* est facultatif. S’il est vierge, le schéma par défaut sera utilisé.  
  
 *table_name*  
 Le nom de la nouvelle table. Pour créer une table temporaire locale, faites précéder le nom de table avec #.  Pour obtenir des explications et des conseils sur les tables temporaires, consultez [des tables temporaires dans Azure SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-temporary/). 
 
 *nom_colonne*  
 Le nom d’une colonne de table.
   
### <a name="ColumnOptions"></a>Options de colonne

 `COLLATE`*Windows_collation_name*  
 Spécifie le classement de l’expression. Le classement doit être un des classements Windows pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des classements Windows pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [nom de classement Windows (Transact-SQL)](http://msdn.microsoft.com/library/ms188046\(v=sql11\)/).  
  
 `NULL` | `NOT NULL`  
 Spécifie si `NULL` valeurs sont autorisées dans la colonne. La valeur par défaut est `NULL`.  
  
 [ `CONSTRAINT` *constraint_name* ] `DEFAULT` *expression_constante*  
 Spécifie la valeur de colonne par défaut.  
  
 | Argument | Explication |
 | -------- | ----------- |
 | *constraint_name* | Nom facultatif de la contrainte. Le nom de la contrainte est unique dans la base de données. Le nom peut être réutilisé dans d’autres bases de données. |
 | *expression_constante* | La valeur par défaut pour la colonne. L’expression doit être une valeur littérale ou une constante. Par exemple, ces expressions constantes sont autorisées : `'CA'`, `4`. Ils ne sont pas autorisés : `2+3`, `CURRENT_TIMESTAMP`. |
  

### <a name="TableOptions"></a>Options de structure de table
Pour obtenir des conseils sur le choix du type de table, consultez [indexer des tables dans Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-tables-index/).
  
 `CLUSTERED COLUMNSTORE INDEX`  
Stocke le tableau sous la forme d’un index cluster columnstore. L’index cluster columnstore s’applique à toutes les données de la table. Ceci est la valeur par défaut pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].   
 
 `HEAP`   
  Stocke le tableau sous la forme d’un segment de mémoire. Ceci est la valeur par défaut pour [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 `CLUSTERED INDEX`( *index_column_name* [,...*n* ] )  
 Stocke le tableau sous la forme d’un index cluster avec une ou plusieurs colonnes clés. Stocke les données en ligne. Utilisez *index_column_name* pour spécifier le nom d’une ou plusieurs colonnes clés dans l’index.  Pour plus d’informations, consultez les Tables Rowstore dans les remarques d’ordre général.
 
 `LOCATION = USER_DB`   
 Cette option est déconseillée. Il est syntaxiquement acceptée, mais n’est plus nécessaire et n’affecte plus comportement.   
  
### <a name="TableDistributionOptions"></a>Options de distribution de table
Pour comprendre comment choisir la meilleure méthode de distribution et d’utiliser des tables distribuées, consultez [distribution de tables Azure SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-distribute/).

`DISTRIBUTION = HASH`( *distribution_column_name* )   
Attribue à chaque ligne à une distribution par le hachage de la valeur stockée dans *distribution_column_name*. L’algorithme est déterministe, ce qui signifie qu’il hache toujours la même valeur pour la même distribution.  La colonne de distribution doit être définie comme NOT NULL depuis toutes les lignes est de valeur NULL est affectée à la distribution même.

`DISTRIBUTION = ROUND_ROBIN`   
Distribue uniformément les lignes entre toutes les distributions de manière alternée. Ceci est la valeur par défaut pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].

`DISTRIBUTION = REPLICATE`    
Stocke une copie de la table sur chaque nœud de calcul. Pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] la table est stockée sur une base de données de distribution sur chaque nœud de calcul. Pour [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], la table est stockée dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] groupe de fichiers qui s’étend sur le nœud de calcul. Ceci est la valeur par défaut pour [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
### <a name="TablePartitionOptions"></a>Options de partition de table
Pour obtenir des conseils sur l’utilisation de partitions de table, consultez [partitionner des tables dans SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-partition/).

 `PARTITION`( *partition_column_name* `RANGE` [ `LEFT`  |  `RIGHT` ] `FOR VALUES` ([ *boundary_value* [,...*n*] ] ))   
Crée un ou plusieurs partitions de table. Il s’agit des tranches de table horizontale qui vous permettent d’effectuer des opérations sur des sous-ensembles de lignes que la table soit stockée comme un segment de mémoire, un index cluster ou un index cluster columnstore. Contrairement à la colonne de distribution, les partitions de table ne déterminent pas la distribution dans lequel chaque ligne est stockée. Au lieu de cela, les partitions de table déterminent comment les lignes sont regroupées et stockées au sein de chaque point de distribution.  
 
| Argument | Explication |
| -------- | ----------- |
|*partition_column_name*| Spécifie la colonne qui [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] utilisera pour partitionner les lignes. Cette colonne peut être n’importe quel type de données. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Trie les valeurs de colonne de partition dans l’ordre croissant. Le classement de faible à élevé s’étende de `LEFT` à `RIGHT` pour la `RANGE` spécification. |  
| `RANGE LEFT` | Spécifie que la valeur limite appartient à la partition sur la gauche (valeurs inférieure). La valeur par défaut est LEFT. |
| `RANGE RIGHT` | Spécifie que la valeur limite appartient à la partition sur la droite (valeurs plus élevées). | 
| `FOR VALUES`( *boundary_value* [,...*n*] ) | Spécifie les valeurs limites pour la partition. *boundary_value* est une expression constante. Il ne peut pas être NULL. Il doit correspondre ou être implicitement convertible en type de données de *partition_column_name*. Elle ne peut pas être tronquée pendant une conversion implicite afin que la taille et l’échelle de la valeur ne correspondent pas le type de données *partition_column_name*<br></br><br></br>Si vous spécifiez la `PARTITION` clause, mais ne spécifiez pas une valeur limite, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] créera une table partitionnée avec une partition. Le cas échéant, vous un fractionnement de la table en deux partitions ultérieurement.<br></br><br></br>Si vous spécifiez une valeur limite, la table résultante a deux partitions ; une des valeurs inférieures à la valeur limite et un pour les valeurs supérieures à la valeur limite. Notez que si vous déplacez une partition dans une table non partitionnée, la table non partitionnée recevra les données, mais n’auront pas les limites de partition dans ses métadonnées.| 
 
 Consultez [créer une table partitionnée](#PartitionedTable) dans la section Exemples.

### <a name="DataTypes"></a>Types de données
[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]prend en charge les plus couramment utilisées des types de données. Vous trouverez ci-dessous la liste des types de données pris en charge, ainsi que leurs détails et les octets de stockage. Pour mieux comprendre les types de données et comment les utiliser, consultez [ des types de données pour les tables dans SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-data-types).

Pour un tableau des conversions de types de données, consultez la section des Conversions implicites de [CAST et CONVERT (Transact-SQL)](http://msdn.microsoft.com/library/ms187928/).

`datetimeoffset` [ ( *n* ) ]  
 La valeur par défaut  *n*  est 7.  
  
 `datetime2` [ ( *n* ) ]  
Identique à `datetime`, sauf que vous pouvez spécifier le nombre de fractions de secondes. La valeur par défaut  *n*  est `7`.  
  
|*n*valeur|Précision|Échelle|  
|--:|--:|-:|  
|`0`|19|0|  
|`1`|21|1|  
|`2`|22|2|  
|`3`|23|3|  
|`4`|24|4|  
|`5`|25|5|  
|`6`|26|6|  
|`7`|27|7|  
  
 `datetime`  
 Stocke la date et l’heure du jour, avec des caractères de 19 à 23 selon le calendrier grégorien. La date peut contenir année, mois et jour. L’heure contient les heures, minutes, secondes. En option, vous pouvez afficher trois chiffres pour les fractions de seconde. La taille de stockage est de 8 octets.  
  
 `smalldatetime`  
 Stocke une date et une heure. Taille de stockage est de 4 octets.  
  
 `date`  
 Stocke une date en utilisant un maximum de 10 caractères pour l’année, mois et jour selon le calendrier grégorien. La taille de stockage est 3 octets. Date est stockée sous forme d’entier.  
  
 `time` [ ( *n* ) ]  
 La valeur par défaut  *n*  est `7`.  
  
 `float` [ ( *n* ) ]  
 Type de données numériques approximatives pour une utilisation avec les données à virgule flottante numérique. Données à virgule flottante sont approximative, ce qui signifie que toutes les valeurs dans la plage de type de données peuvent être représentées exactement. *n*Spécifie le nombre de bits utilisés pour stocker la mantisse du `float` en notation scientifique. Par conséquent,  *n*  détermine la taille de la précision et de stockage. Si  *n*  est spécifié, il doit être une valeur comprise entre `1` et `53`. La valeur par défaut  *n*  est `53`.  
  
| *n*valeur | Précision | Taille de stockage |  
| --------: | --------: | -----------: |  
| 1-24   | 7 chiffres  | 4 octets      |  
| 25-53  | 15 chiffres | 8 octets      |  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]traite  *n*  comme l’une des deux valeurs possibles. Si `1` <=   *n*   <=  `24`,  *n*  est traité comme `24`. Si `25`  <=   *n*   <=  `53`,  *n*  est traité comme `53`.  
  
 Le [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] `float` type de données est conforme à la norme ISO pour toutes les valeurs de  *n*  de `1` via `53`. Le synonyme de double précision est `float(53)`.  
  
 `real` [ ( *n* ) ]  
 La définition de réel est identique à virgule flottante. Le synonyme ISO de `real` est `float(24)`.  
  
 `decimal`[( *précision* [ *, échelle* ])] | `numeric` [( *précision* [ *, échelle* ])]  
 Magasins de précision et échelle fixes.  
  
 *precision*  
 Nombre total maximal de chiffres décimaux pouvant figurer à la fois à gauche et à droite de la virgule décimale. La précision doit être comprise entre `1` et la précision maximale de `38`. La précision par défaut est `18`.  
  
 *scale*  
 Nombre maximal de chiffres décimaux à droite de la virgule. *Mise à l’échelle* doit être une valeur à partir de `0` via *précision*. Vous ne pouvez spécifier *échelle* si *précision* est spécifié. L’échelle par défaut est `0`; par conséquent, `0`  <=  *échelle* <= *précision*. Les tailles de stockage maximales varient en fonction de la précision.  
  
| Précision | Taille de stockage (octets)  |  
| ---------: |-------------: |  
|  1-9       |             5 |  
| 10-19      |             9 |  
| 20-28      |            13 |  
| 29-38      |            17 |  
  
 `money` | `smallmoney`  
 Types de données qui représentent les valeurs de devise.  
  
| Type de données | Taille de stockage (octets) |  
| --------- | ------------: |  
| `money`|8|  
| `smallmoney` |4|  
  
 `bigint` | `int` | `smallint` | `tinyint`  
 Types de données représentant des valeurs numériques exactes qui utilisent des entiers. Le stockage est indiqué dans le tableau suivant.  
  
| Type de données | Taille de stockage (octets) |  
| --------- | ------------: |  
| `bigint`|8|  
| `int` |4|  
| `smallint` |2|  
| `tinyint` |1|  
  
 `bit`  
 Type de données integer qui peut prendre la valeur de `1`, `0`, ou ' NULL. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]optimiser le stockage des colonnes de bits. S’il existe des colonnes bit 8 dans une table, les colonnes sont stockées dans 1 octet. S’il y a de colonnes de 9 à 16 bits, les colonnes sont stockés sous forme de 2 octets et ainsi de suite.  
  
 `nvarchar`[(  *n*   |  `max` )]-- `max` s’applique uniquement aux [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
 Données de type caractères Unicode de longueur variable. *n*peut être une valeur comprise entre 1 et 4000. `max` indique que la taille de stockage maximale occupée est de 2^31-1 octets (2 Go). Taille en octets du stockage est deux fois le nombre de caractères entrés plus 2 octets. Les données saisies peuvent avoir une longueur de 0 caractère.  
  
 `nchar` [ ( *n* ) ]  
 Données de caractères Unicode de longueur fixe avec une longueur de  *n*  caractères. *n*doit être une valeur à partir de `1` via `4000`. La taille de stockage est le double  *n*  octets.  
  
 `varchar`[(  *n*    |  `max` )]-- `max` s’applique uniquement aux [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].   
 Données de caractères non-Unicode de longueur variable, avec une longueur de  *n*  octets. *n*doit être une valeur à partir de `1` à `8000`. `max`Indique que la taille de stockage maximale est de 2 ^ 31-1 octets (2 Go). La taille de stockage est la longueur réelle des données entrées + 2 octets.  
  
 `char` [ ( *n* ) ]  
 Données de caractères non-Unicode de longueur fixe, avec une longueur de  *n*  octets. *n*doit être une valeur à partir de `1` à `8000`. La taille de stockage est  *n*  octets. La valeur par défaut pour  *n*  est `1`.  
  
 `varbinary`[(  *n*    |  `max` )]-- `max` s’applique uniquement aux [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
 Données binaires de longueur variable. *n*peut être une valeur à partir de `1` à `8000`. `max` indique que la taille de stockage maximale occupée est de 2^31-1 octets (2 Go). La taille de stockage est la longueur réelle des données entrées + 2 octets. La valeur par défaut  *n*  est 7.  
  
 `binary` [ ( *n* ) ]  
 Données binaires de longueur fixe avec une longueur de  *n*  octets. *n*peut être une valeur à partir de `1` à `8000`. La taille de stockage est  *n*  octets. La valeur par défaut  *n*  est `7`.  
  
 `uniqueidentifier`  
 GUID sur 16 octets.  
   
<a name="Permissions"></a>  
## <a name="permissions"></a>Permissions  
 Création d’une table requiert l’autorisation dans le `db_ddladmin` rôle de base de données fixe ou :
 - `CREATE TABLE`autorisation sur la base de données
 - `ALTER SCHEMA`autorisation sur le schéma qui contient la table. 

Création d’une table partitionnée nécessite l’autorisation dans le `db_ddladmin` rôle de base de données fixe ou

- `ALTER ANY DATASPACE`autorisation
  
 La connexion qui crée une table temporaire locale reçoit `CONTROL`, `INSERT`, `SELECT`, et `UPDATE` autorisations sur la table.  
 
<a name="GeneralRemarks"></a>  
## <a name="general-remarks"></a>Remarques d'ordre général  
 
Pour les limites minimale et maximale, consultez [limites de capacité de l’entrepôt de données SQL](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-service-capacity-limits/). 
 
### <a name="determining-the-number-of-table-partitions"></a>Déterminer le nombre de partitions de table
Chaque table définie par l’utilisateur est divisée en plusieurs tables plus petites qui sont stockées dans des emplacements distincts appelés distributions. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]utilise les 60 distributions. Dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], le nombre de distributions varie selon le nombre de nœuds de calcul.
 
Chaque point de distribution contient toutes les partitions de table. Par exemple, s’il existe des 60 distributions et quatre partitions de table, il y aura 320 partitions. Si la table est un index columnstore en cluster, il y aura qu’un seul index columnstore par partition, ce qui signifie que vous aurez 320 columnstore index.

Nous vous recommandons d’utiliser moins de partitions de table pour vous assurer de chaque index columnstore a suffisamment de lignes pour tirer parti des avantages des index columnstore. Pour obtenir des instructions, consultez [partitionner des tables dans SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-tables-partition/) et [indexer des tables dans l’entrepôt de données SQL](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-tables-index/)  

  
 ### <a name="rowstore-table-heap-or-clustered-index"></a>Table Rowstore (segment de mémoire ou index ordonné en clusters)  
 Une table rowstore est une table stockée dans l’ordre de la ligne par ligne. Il est un segment de mémoire ou un index ordonné en clusters. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]crée toutes les tables rowstore avec la compression de page ; ce n’est pas configurable par l’utilisateur.   
 
 ### <a name="columnstore-table-columnstore-index"></a>Table de ColumnStore (columnstore index)
Une table columnstore est une table stockée dans l’ordre de colonne par colonne. L’index columnstore est une technologie qui gère les données stockées dans une table columnstore.  L’index cluster columnstore n’affecte pas la façon dont les données sont distribuées ; elle affecte la façon dont les données sont stockées dans chaque point de distribution.

Pour modifier une table rowstore en une table columnstore, supprimez tous les index existants sur la table et créer un index cluster columnstore. Pour obtenir un exemple, consultez [CREATE COLUMNSTORE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-columnstore-index-transact-sql.md).

Pour plus d’informations, consultez ces articles :
- [Fonctionnalité de contrôle de version du résumé d’index ColumnStore](https://msdn.microsoft.com/library/dn934994/)
- [Indexer des tables dans l’entrepôt de données SQL](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-tables-index/)
- [Guide des index columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md) 
 
<a name="LimitationsRestrictions"></a>  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Vous ne pouvez pas définir une contrainte DEFAULT sur une colonne de distribution.  
  
 ### <a name="partitions"></a>Partitions
 Lorsque vous utilisez des partitions, la colonne de partition ne peut pas avoir un classement Unicode uniquement. Par exemple, l’instruction suivante échoue.  
  
 `CREATE TABLE t1 ( c1 varchar(20) COLLATE Divehi_90_CI_AS_KS_WS) WITH (PARTITION (c1 RANGE FOR VALUES (N'')))`  
 
 Si *boundary_value* est une valeur littérale qui doit être convertie implicitement en type de données dans *partition_column_name*, une incohérence se produit. La valeur littérale est affichée par le [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] vues système, mais la valeur convertie est utilisée pour [!INCLUDE[tsql](../../includes/tsql-md.md)] operations. 
 
  
 ### <a name="temporary-tables"></a>tables temporaires ;
 Les tables temporaires globales qui commencent avec ## ne sont pas pris en charge.  
  
 Les tables temporaires locales ont les limitations et restrictions suivantes :  
  
-   Ils sont visibles uniquement à la session active. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Supprime les automatiquement à la fin de la session. Pour supprimer les explicitlt, utilisez l’instruction DROP TABLE.   
-   Ils ne peuvent pas être renommés. 
-   Ils ne peuvent pas avoir des partitions ou des vues.  
-   Impossible de modifier leurs autorisations. `GRANT`, `DENY`, et `REVOKE` instructions ne peuvent pas être utilisées avec les tables temporaires locales.   
-   Commandes de la console de base de données sont bloquées pour les tables temporaires.   
-   Si plus d’une table temporaire locale est utilisée dans un lot, chacun doit avoir un nom unique. Si plusieurs sessions sont en cours d’exécution le même lot et création de la même table temporaire locale, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] en interne ajoute un suffixe numérique au nom de table temporaire locale pour maintenir un nom unique pour chaque table temporaire locale.  
    
<a name="LockingBehavior"></a>   
## <a name="locking-behavior"></a>Comportement de verrouillage  
 Accepte un verrou exclusif sur la table. Acquiert un verrou partagé sur les objets de base de données, le schéma et SCHEMARESOLUTION.  
 

<a name="ExamplesColumn"></a>   
## <a name="examples-for-columns"></a>Exemples pour les colonnes

### <a name="ColumnCollation"></a> A. Spécifiez un classement de colonne 
 Dans l’exemple suivant, la table `MyTable` est créée avec deux classements de colonne différente. Par défaut, la colonne, `mycolumn1`, a le classement par défaut Latin1_General_100_CI_AS_KS_WS. La colonne, `mycolumn2` possède un classement Frisian_100_CS_AS.  
  
```  
CREATE TABLE MyTable   
  (  
    mycolumnnn1 nvarchar,  
    mycolumn2 nvarchar COLLATE Frisian_100_CS_AS )  
WITH ( CLUSTERED COLUMNSTORE INDEX )  
;  
  
```  
  
### <a name="DefaultConstraint"></a> B. Spécifiez une contrainte par défaut pour une colonne  
 L’exemple suivant montre la syntaxe permettant de spécifier une valeur par défaut pour une colonne. La colonne colA a une contrainte par défaut nommé constraint_colA et la valeur par défaut 0.  
  
```  
  
CREATE TABLE MyTable   
  (  
    colA int CONSTRAINT constraint_colA DEFAULT 0,  
    colB nvarchar COLLATE Frisian_100_CS_AS   
  )  
WITH ( CLUSTERED COLUMNSTORE INDEX )  
;  
```  

<a name="ExamplesTemporaryTables"></a> 
## <a name="examples-for-temporary-tables"></a>Exemples de tables temporaires

### <a name="TemporaryTable"></a> C. Créer une table temporaire locale  
 La commande suivante crée une table temporaire locale nommée #myTable. La table est spécifiée avec un nom en 3 parties. Le nom de table temporaire commence par #.   
  
```  
CREATE TABLE AdventureWorks.dbo.#myTable   
  (  
   id int NOT NULL,  
   lastName varchar(20),  
   zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = HASH (id),  
    CLUSTERED COLUMNSTORE INDEX   
  )  
;  
```

<a name="ExTableStructure"></a>  
## <a name="examples-for-table-structure"></a>Exemples de structure de la table

### <a name="ClusteredColumnstoreIndex"></a> D. Créer une table avec un index cluster columnstore  
 L’exemple suivant crée une table distribuée avec un index cluster columnstore. Chaque point de distribution est stocké sous forme de columnstore.  
  
 L’index cluster columnstore n’affecte pas la façon dont les données sont distribuées ; données sont toujours distribuées par ligne. L’index columnstore cluster affecte la façon dont les données sont stockées au sein de chaque point de distribution.  
  
```  
  
CREATE TABLE MyTable   
  (  
    colA int CONSTRAINT constraint_colA DEFAULT 0,  
    colB nvarchar COLLATE Frisian_100_CS_AS   
  )  
WITH   
  (   
    DISTRIBUTION = HASH ( colB ),  
    CLUSTERED COLUMNSTORE INDEX   
  )  
;  
```  
 
<a name="ExTableDistribution"></a> 
## <a name="examples-for-table-distribution"></a>Exemples pour la distribution de la table

### <a name="RoundRobin"></a> E. Créer une table ROUND_ROBIN  
 L’exemple suivant crée une table ROUND_ROBIN avec trois colonnes et sans partitions. Les données sont réparties sur toutes les distributions. La table est créée avec un INDEX COLUMNSTORE en cluster, ce qui donne une meilleure compression de données de performances et qu’un index ordonné en clusters de segment de mémoire ou rowstore.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH ( CLUSTERED COLUMNSTORE INDEX );  
```  
  
### <a name="HashDistributed"></a> F. Créer une table de hachage distribué  
 L’exemple suivant crée la même table que l’exemple précédent. Toutefois, pour cette table, les lignes sont distribuées (sur le `id` colonne) à la place de façon aléatoire réparties comme une table ROUND_ROBIN. La table est créée avec un INDEX COLUMNSTORE en cluster, ce qui donne une meilleure compression de données de performances et qu’un index ordonné en clusters de segment de mémoire ou rowstore.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = HASH (id),   
    CLUSTERED COLUMNSTORE INDEX  
  );  
```  
  
### <a name="Replicated"></a>G. Créer une table répliquée  
 L’exemple suivant crée une table répliquée est similaire aux exemples précédents. Les tables répliquées sont copiées entièrement sur chaque nœud de calcul. Avec cette copie sur chaque nœud de calcul, le déplacement des données sont réduit pour les requêtes. Cet exemple est créé avec un INDEX cluster, ce qui donne une meilleure compression de données à un segment de mémoire et ne peut pas contenir suffisamment de lignes pour obtenir une bonne compression d’INDEX cluster COLUMNSTORE.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode varchar(6)  
  )  
WITH  
  (   
    DISTRIBUTION = REPLICATE,   
    CLUSTERED INDEX (lastName)  
  );  
```  

<a name="ExTablePartitions"></a> 
## <a name="examples-for-table-partitions"></a>Exemples pour les partitions de table

###  <a name="PartitionedTable"></a>H. Créer une table partitionnée  
 L’exemple suivant crée la même table, comme indiqué dans l’exemple A, avec l’ajout de partitionnement par plage gauche sur la `id` colonne. Il spécifie quatre valeurs limites de partition, ce qui aboutit à cinq partitions.  
  
```  
CREATE TABLE myTable   
  (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode int)  
WITH   
  (   
  
    PARTITION ( id RANGE LEFT FOR VALUES (10, 20, 30, 40 )),  
    CLUSTERED COLUMNSTORE INDEX      
  )  
;  
```  
  
 Dans cet exemple, de tri des données dans les partitions suivantes :  
  
-   Partition 1 : col < = 10   
-   Partition 2:10 < col < = 20   
-   Partition 3:20 < col < = 30   
-   Partition 4:30 < col < = 40   
-   5:40 de partition < col  
  
 Si cette même table a été partitionnée RANGE RIGHT, au lieu de RANGE LEFT (par défaut), les données seront triée dans les partitions suivantes :  
  
-   Partition 1 : col < 10  
-   Partition 2:10 < = col < 20   
-   Partition 3:20 < = col < 30    
-   Partition 4:30 < = col < 40   
-   Partition 5:40 < = col  
  
### <a name="OnePartition"></a>I. Créer une table partitionnée avec une partition  
 L’exemple suivant crée une table partitionnée avec une partition. Il ne spécifie pas les valeurs limites, ce qui aboutit à une partition.  
  
```  
CREATE TABLE myTable (  
    id int NOT NULL,  
    lastName varchar(20),  
    zipCode int)  
WITH   
    (   
      PARTITION ( id RANGE LEFT FOR VALUES ( )),  
      CLUSTERED COLUMNSTORE INDEX  
    )  
;  
```  
  
### <a name="DatePartition"></a>J. Créer une table avec le partitionnement par date  
 L’exemple suivant crée une nouvelle table nommée `myTable`, avec le partitionnement sur un `date` colonne. À l’aide de droite de la plage et les dates pour les valeurs limites, il place un mois de données dans chaque partition.  
  
```  
CREATE TABLE myTable (  
    l_orderkey      bigint,       
    l_partkey       bigint,                                             
    l_suppkey       bigint,                                           
    l_linenumber    bigint,        
    l_quantity      decimal(15,2),  
    l_extendedprice decimal(15,2),  
    l_discount      decimal(15,2),  
    l_tax           decimal(15,2),  
    l_returnflag    char(1),  
    l_linestatus    char(1),  
    l_shipdate      date,  
    l_commitdate    date,  
    l_receiptdate   date,  
    l_shipinstruct  char(25),  
    l_shipmode      char(10),  
    l_comment       varchar(44))  
WITH   
  (   
    DISTRIBUTION = HASH (l_orderkey),  
    CLUSTERED COLUMNSTORE INDEX,  
    PARTITION ( l_shipdate  RANGE RIGHT FOR VALUES   
      (  
        '1992-01-01','1992-02-01','1992-03-01','1992-04-01','1992-05-01',
        '1992-06-01','1992-07-01','1992-08-01','1992-09-01','1992-10-01',
        '1992-11-01','1992-12-01','1993-01-01','1993-02-01','1993-03-01',
        '1993-04-01','1993-05-01','1993-06-01','1993-07-01','1993-08-01',
        '1993-09-01','1993-10-01','1993-11-01','1993-12-01','1994-01-01',
        '1994-02-01','1994-03-01','1994-04-01','1994-05-01','1994-06-01',
        '1994-07-01','1994-08-01','1994-09-01','1994-10-01','1994-11-01',
        '1994-12-01'  
      ))
  );  
```  
  
<a name="SeeAlso"></a>    
## <a name="see-also"></a>Voir aussi 
 
 [CREATE TABLE AS SELECT &#40; Entrepôt de données SQL Azure &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  

