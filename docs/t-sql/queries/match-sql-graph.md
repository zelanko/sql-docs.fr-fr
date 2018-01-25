---
title: CORRESPONDANCE (graphique SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MATCH
- MATCH_TSQL
dev_langs: TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
ms.assetid: 
caps.latest.revision: "1"
author: shkale-msft
ms.author: shkale
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cbfa524cb9957ba557cfd239dae16a93aed919bf
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="match-transact-sql"></a>MATCH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

  Spécifie une condition de recherche pour un graphique. CORRESPONDANCE peut être utilisée uniquement avec graphique nœud bord tables et, dans l’instruction SELECT dans le cadre de la clause WHERE. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MATCH (<graph_search_pattern>)

<graph_search_pattern>::=
    {<node_alias> { 
                     { <-( <edge_alias> )- } 
                   | { -( <edge_alias> )-> }
                 <node_alias> 
                 } 
     }
     [ { AND } { ( <graph_search_pattern> ) } ]
     [ ,...n ]
  
<node_alias> ::=
    node_table_name | node_alias 

<edge_alias> ::=
    edge_table_name | edge_alias
```

## <a name="arguments"></a>Arguments  
*graph_search_pattern*  
Spécifie le modèle à rechercher ou chemin d’accès doit parcourir dans le graphique. Ce modèle utilise la syntaxe d’art ASCII pour parcourir un chemin d’accès dans le graphique. Le modèle s’opère à partir d’un nœud à un autre via un bord, dans la direction de la flèche fournie. Bord noms ou alias sont fournies à l’intérieur de parantheses. Noms des nœuds ou des alias apparaissent aux deux extrémités de la flèche. La flèche peut aller dans les deux sens dans le modèle.

*node_alias*  
Nom ou l’alias d’une table de nœud fournie dans la clause FROM.

*edge_alias*  
Nom ou l’alias d’une table du bord fournie dans la clause FROM.


## <a name="remarks"></a>Notes  
Les noms des nœuds à l’intérieur de correspondance peuvent être répétés.  En d’autres termes, un nœud peut être parcouru un nombre arbitraire de fois dans la même requête.  
Un nom de session ne peut pas être répété à l’intérieur de correspondance.  
Un bord peut pointer dans les deux sens, mais il doit avoir un sens explicite.  
OU et pas les opérateurs ne sont pas pris en charge dans le modèle de correspondance. CORRESPONDANCE peut être combinée avec d’autres expressions à l’aide d’et dans la clause WHERE. Toutefois, l’association avec d’autres expressions à l’aide d’ou ou pas ne prend pas en charge. 

## <a name="examples"></a>Exemples  
### <a name="a--find-a-friend"></a>A.  Rechercher un ami 
 L’exemple suivant crée une table de nœud de personne et le tableau de bord de vos amis, insère des données et utilise ensuite la correspondance pour rechercher les amis d’Alice, une personne dans le graphique.

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Insert into node table
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 INSERT INTO dbo.Person VALUES (3, 'Jacob');

-- Insert into edge table
INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');

INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'Jacob'), '10/15/2011');

INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'John'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'Jacob'), '10/15/2012');

-- use MATCH in SELECT to find friends of Alice
SELECT Person2.name AS FriendName
FROM Person Person1, friend, Person Person2
WHERE MATCH(Person1-(friend)->Person2)
AND Person1.name = 'Alice';

 ```

 ### <a name="b--find-friend-of-a-friend"></a>B.  Trouver la fonction friend d’une fonction friend
 L’exemple suivant tente de trouver la fonction friend d’une fonction friend d’Alice. 

 ```
SELECT Person3.name AS FriendName 
FROM Person Person1, friend, Person Person2, friend friend2, Person Person3
WHERE MATCH(Person1-(friend)->Person2-(friend2)->Person3)
AND Person1.name = 'Alice';

 ```

### <a name="c--more-match-patterns"></a>C.  Plus `MATCH` modèles
 Voici quelques-unes des plus dans lequel un modèle peut être spécifié à l’intérieur de correspondance.

 ```
 -- Find a friend
    SELECT Person2.name AS FriendName
    FROM Person Person1, friend, Person Person2
    WHERE MATCH(Person1-(friend)->Person2);
    
-- The pattern can also be expressed as below

    SELECT Person2.name AS FriendName
    FROM Person Person1, friend, Person Person2 
    WHERE MATCH(Person2<-(friend)-Person1);


-- Find 2 people who are both friends with same person
    SELECT Person1.name AS Friend1, Person2.name AS Friend2
    FROM Person Person1, friend friend1, Person Person2, 
         friend friend2, Person Person0
    WHERE MATCH(Person1-(friend1)->Person0<-(friend2)-Person2);
    
-- this pattern can also be expressed as below

    SELECT Person1.name AS Friend1, Person2.name AS Friend2
    FROM Person Person1, friend friend1, Person Person2, 
         friend friend2, Person Person0
    WHERE MATCH(Person1-(friend1)->Person0 AND Person2-(friend2)->Person0);
 ```
 

## <a name="see-also"></a>Voir aussi  
 [CRÉER une TABLE &#40; Graphique SQL &#41;](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (SQL Graph)](../../t-sql/statements/insert-sql-graph.md)]  
 [Graphique de traitement avec SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md)  
