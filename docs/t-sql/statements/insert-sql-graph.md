---
title: INSERT (graphique SQL) | Documents Microsoft
description: "Insérer la syntaxe pour les tableaux de bord ou le nœud SQL graphique."
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], SQL graph
- SQL graph, INSERT statement
ms.assetid: 
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e694d89efef130d2abcd5cd6424e2be576ef09de
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="insert-sql-graph"></a>INSERT (graphique SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Ajoute une ou plusieurs lignes à un `node` ou `edge` table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 

> [!NOTE]   
>  Pour des instructions Transact-SQL standard, consultez [insérer un tableau (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md).
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="insert-into-node-table-syntax"></a>INSÉRER dans la syntaxe de Table de nœud 
La syntaxe pour l’insertion dans une table de nœud est identique à celui d’une table normale. 

```  
[ WITH <common_table_expression> [ ,...n ] ]  
INSERT   
{  
        [ TOP ( expression ) [ PERCENT ] ]   
        [ INTO ]   
        { <object> | rowset_function_limited   
          [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
        }  
    {  
        [ (column_list) ] | [(<edge_table_column_list>)]  
        [ <OUTPUT Clause> ]  
        { VALUES ( { DEFAULT | NULL | expression } [ ,...n ] ) [ ,...n     ]   
        | derived_table   
        | execute_statement  
        | <dml_table_source>  
        | DEFAULT VALUES   
        }  
    }  
}  
[;]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
      | database_name .[ schema_name ] .   
      | schema_name .   
    ]  
    node_table_name  | edge_table_name
}  
  
<dml_table_source> ::=  
    SELECT <select_list>  
    FROM ( <dml_statement_with_output_clause> )   
      [AS] table_alias [ ( column_alias [ ,...n ] ) ]  
    [ WHERE <on_or_where_search_condition> ]  
        [ OPTION ( <query_hint> [ ,...n ] ) ]  

<on_or_where_search_condition> ::=
    {  <search_condition_with_match> | <search_condition> }

<search_condition_with_match> ::=
    { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) }
    [ AND { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<search_condition> ::=
    { [ NOT ] <predicate> | ( <search_condition> ) }
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<graph_predicate> ::=
    MATCH( <graph_search_pattern> [ AND <graph_search_pattern> ] [ , ...n] )

<graph_search_pattern>::=
    <node_alias> { { <-( <edge_alias> )- | -( <edge_alias> )-> } <node_alias> }

<edge_table_column_list> ::=
    ($from_id, $to_id, [column_list])

```  
  
 
## <a name="arguments"></a>Arguments  
 Ce document décrit les arguments se rapportant à un graphique SQL. Pour une liste complète et une description des arguments pris en charge dans l’instruction INSERT, consultez [insérer un tableau (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)

 INTO  
 Mot clé facultatif qui peut être utilisé entre `INSERT` et la table cible.  
  
 *search_condition_with_match*   
 `MATCH`clause peut être utilisée dans une sous-requête lors de l’insertion dans un tableau de bord ou de nœud. Pour `MATCH` syntaxe des instructions, consultez [graphique correspondance (Transact-SQL)](../../t-sql/queries/match-sql-graph.md)

 *graph_search_pattern*   
 Modèle de recherche fournie pour `MATCH` clause dans le cadre du prédicat de graphique.

 *edge_table_column_list*   
 Les utilisateurs doivent fournir des valeurs pour `$from_id` et `$to_id` lors de l’insertion dans une session. Une erreur s’affichera si aucune valeur n’est pas fournie ou les valeurs NULL sont insérées dans ces colonnes. 
  

## <a name="remarks"></a>Notes  
L’insertion dans un nœud est identique à l’insertion dans une table relationnelle. Valeurs de la colonne de node_id $ sont générés automatiquement.

Lors de l’insertion dans un tableau de bord, les utilisateurs doivent fournir des valeurs pour `$from_id` et `$to_id` colonnes.   

L’insertion en bloc pour la table du nœud est reste identique à celui d’une table relationnelle.

Avant l’insertion en bloc dans une table du bord, les tables du nœud doivent être importés. Les valeurs pour `$from_id` et `$to_id` peut ensuite être extraites à partir de la `$node_id` colonne de la table des nœuds et inséré comme bords. 

  
### <a name="permissions"></a>Permissions  
 L'autorisation INSERT est obligatoire sur la table cible.  
  
 Insérer les autorisations par défaut aux membres du **sysadmin** rôle serveur fixe le **db_owner** et **db_datawriter** les rôles de base de données et le propriétaire de la table. Membres de la **sysadmin**, **db_owner**et le **db_securityadmin** rôles et le propriétaire de la table peuvent transférer des autorisations à d’autres utilisateurs.  
  
 Pour exécuter INSERT avec l’option BULK de la fonction OPENROWSET, vous devez être un membre de la **sysadmin** rôle serveur fixe ou de la **bulkadmin** rôle serveur fixe.  
  

## <a name="examples"></a>Exemples  
  
#### <a name="a--insert-into-node-table"></a>A.  Insérer dans la table de nœud  
 L’exemple suivant crée une table de nœud de personne et insère les 2 lignes dans cette table.

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 
 -- Insert records for Alice and John
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 ```
  
#### <a name="b--insert-into-edge-table"></a>B.  Insérer dans la table du bord  
 L’exemple suivant crée un tableau de bord friend et insère un bord dans la table.

 ```
 -- Create friend edge table
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Create a friend edge, that connect Alice and John
 INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');
 ```

  
## <a name="see-also"></a>Voir aussi  
 [Insérer une TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/insert-transact-sql.md)   
 [Graphique de traitement avec SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md)  



