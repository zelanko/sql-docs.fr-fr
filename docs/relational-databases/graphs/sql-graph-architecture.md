---
title: Architecture de graphe SQL | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, architecture
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ed234a487d5c382400b3a839820a4509c8b880f2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026825"
---
# <a name="sql-graph-architecture"></a>Graphique de l’Architecture SQL  
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Découvrez l’architecture de graphe SQL. Le fait de connaître les principes de base rend plus facile à comprendre les autres articles de graphe SQL.
 
## <a name="sql-graph-database"></a>Base de données de graphique SQL
Les utilisateurs peuvent créer un graphique par base de données. Un graphique est une collection de tables de nœuds et d’arêtes. Les tables de nœuds ou d’arêtes peuvent être créés sous n’importe quel schéma dans la base de données, mais elles appartiennent à un graphique de logique. Une table de nœuds est la collection de type similaire de nœuds. Par exemple, une table de nœuds Person conserve tous les nœuds de personne appartenant à un graphique. De même, un tableau de bord est une collection d’un type similaire de bords. Par exemple, une table d’arêtes Friends conserve tous les bords qui se connectent une personne à une autre personne. Dans la mesure où les nœuds et les bords sont stockés dans les tables, la plupart des opérations prises en charge sur les tables normales est pris en charge sur les tables de nœuds ou d’arêtes. 
 
 
![SQL-graph-architecture](../../relational-databases/graphs/media/sql-graph-architecture.png "architecture de base de données de graphique Sql")   

Figure 1 : Architecture de base de données de graphe SQL
 
## <a name="node-table"></a>Table de nœuds
Une table de nœuds représente une entité dans un schéma de graphique. Chaque fois qu’une table de nœuds est créée, ainsi que les colonnes définies par l’utilisateur, implicite `$node_id` colonne est créée, qui identifie de façon unique un nœud donné dans la base de données. Les valeurs dans `$node_id` sont générées automatiquement et sont une combinaison de `object_id` de cette table de nœud et une valeur bigint généré en interne. Toutefois, lorsque la `$node_id` colonne est sélectionnée, une valeur calculée sous la forme d’une chaîne JSON s’affiche. En outre, `$node_id` est une pseudo-colonne, qui est mappé à un nom interne avec une chaîne hexadécimale qu’il contient. Lorsque vous sélectionnez `$node_id` à partir de la table, le nom de colonne s’affiche en tant que `$node_id_<hex_string>`. À l’aide des noms de colonnes pseudo-aléatoire dans les requêtes est la méthode recommandée de l’interrogation interne `$node_id` colonne et à l’aide du nom interne avec une chaîne hexadécimale doivent être évitées.

Il est recommandé que les utilisateurs créer une contrainte unique ou un index sur la `$node_id` colonne au moment de la création de table de nœud, mais si une n’est pas créée, une valeur par défaut des index non cluster unique est créé automatiquement. Toutefois, n’importe quel index sur une colonne de pseudo graphique est créé sur les colonnes sous-jacentes internes. Autrement dit, un index créé sur le `$node_id` colonne, apparaîtra sur interne `graph_id_<hex_string>` colonne.   


## <a name="edge-table"></a>Tableau de bord
Un tableau de bord représente une relation dans un graphique. Bords sont toujours dirigées et connecter les deux nœuds. Un tableau de bord permet aux utilisateurs de modéliser des relations plusieurs-à-plusieurs dans le graphique. Un tableau de bord peut, ou peut-être pas tous les attributs définis par l’utilisateur qu’il contient. Chaque fois qu’un tableau de bord est créé, ainsi que les attributs définis par l’utilisateur, les trois colonnes implicites sont créés dans le tableau de bord :

|Nom de colonne    |Description  |
|---   |---  |
|`$edge_id`   |Identifie de façon unique un bord donné dans la base de données. Il n’est généré et la valeur est une combinaison d’object_id de la table d’arêtes et une valeur bigint généré en interne. Toutefois, lorsque la `$edge_id` colonne est sélectionnée, une valeur calculée sous la forme d’une chaîne JSON s’affiche. `$edge_id` est une pseudo-colonne, qui est mappé à un nom interne avec une chaîne hexadécimale qu’il contient. Lorsque vous sélectionnez `$edge_id` à partir de la table, le nom de colonne s’affiche en tant que `$edge_id_\<hex_string>`. À l’aide des noms de colonnes pseudo-aléatoire dans les requêtes est la méthode recommandée de l’interrogation interne `$edge_id` colonne et à l’aide du nom interne avec une chaîne hexadécimale doivent être évitées. |
|`$from_id`   |Stocke le `$node_id` du nœud, à partir de l’origine de la périphérie.  |
|`$to_id`   |Stocke le `$node_id` du nœud, à laquelle se termine le bord. |

Les nœuds auxquels un bord donné peut se connecter est régie par les données insérées dans la `$from_id` et `$to_id` colonnes. Dans la première version, il n’est pas possible de définir des contraintes sur la table du bord, afin de le restreindre de se connecter à n’importe quel type de deux nœuds. Autrement dit, une arête peut se connecter les deux nœuds dans le graphique, quels que soient leurs types.

Similaire à la `$node_id` colonne, il est recommandé que les utilisateurs créent un index unique ou une contrainte sur la `$edge_id` colonne au moment de la création de la table du bord, mais si une n’est pas créée, une valeur par défaut des index non cluster unique est automatiquement créé sur Cette colonne. Toutefois, n’importe quel index sur une colonne de pseudo graphique est créé sur les colonnes sous-jacentes internes. Autrement dit, un index créé sur le `$edge_id` colonne, apparaîtra sur interne `graph_id_<hex_string>` colonne. Il est également recommandé pour les scénarios OLTP, que les utilisateurs créent un index sur (`$from_id`, `$to_id`) colonnes, pour les recherches plus rapides dans la direction du bord.  

Figure 2 montre comment les tables de nœuds et d’arêtes sont stockées dans la base de données. 

![tables de personne amis](../../relational-databases/graphs/media/person-friends-tables.png "nœud Person et amis des tables de périphérie")   

Figure 2 : Représentation sous forme de table nœuds et d’arêtes



## <a name="metadata"></a>Métadonnées
Utilisez ces vues de métadonnées pour voir les attributs d’une table de nœuds ou d’arêtes.
 
### <a name="systables"></a>sys.tables
Les nouveaux, suivants type bit, les colonnes seront ajoutées à SYS. TABLES. Si `is_node` est défini sur 1, ce qui indique que la table est une table de nœuds et si `is_edge` est défini sur 1, ce qui indique que la table est une table d’arêtes.
 
|Nom de la colonne |Type de données |Description |
|--- |---|--- |
|is_node |bit |1 = il s’agit d’une table de nœuds |
|is_edge |bit |1 = il s’agit d’une table d’arêtes |
 
### <a name="syscolumns"></a>sys.columns
Le `sys.columns` vue contient des colonnes supplémentaires `graph_type` et `graph_type_desc`, qui indiquent le type de la colonne dans les tables de nœuds et d’arêtes.
 
|Nom de la colonne |Type de données |Description |
|--- |---|--- |
|graph_type |INT |Colonne interne avec un ensemble de valeurs. Les valeurs sont comprises entre 1-8 pour les colonnes de graphique et de valeur NULL pour d’autres.  |
|graph_type_desc |nvarchar(60)  |colonne interne avec un ensemble de valeurs |
 
Le tableau suivant répertorie les valeurs valides pour `graph_type` colonne

|Valeur de colonne  |Description  |
|---   |---   |
|1  |GRAPH_ID  |
|2  |GRAPH_ID_COMPUTED  |
|3  |GRAPH_FROM_ID  |
|4  |GRAPH_FROM_OBJ_ID  |
|5  |GRAPH_FROM_ID_COMPUTED  |
|6  |GRAPH_TO_ID  |
|7  |GRAPH_TO_OBJ_ID  |
|8  |GRAPH_TO_ID_COMPUTED  |


`sys.columns` stocke également des informations sur les colonnes implicites créées dans les tables de nœuds ou d’arêtes. Informations suivantes peuvent être récupérées à partir de sys.columns, toutefois, les utilisateurs ne peuvent pas sélectionner ces colonnes à partir d’une table de nœuds ou d’arêtes. 

Colonnes implicites dans une table de nœuds

|Nom de la colonne    |Type de données  |is_hidden  |Commentaire  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |interne `graph_id` colonne  |
|$node_id_\<hex_string> |NVARCHAR   |0  |Nœud externe `node_id` colonne  |

Colonnes implicites dans un tableau de bord

|Nom de la colonne    |Type de données  |is_hidden  |Commentaire  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |interne `graph_id` colonne  |
|$edge_id_\<hex_string> |NVARCHAR   |0  |externe `edge_id` colonne  |
|from_obj_id_\<hex_string>  |INT    |1  |interne à partir du nœud `object_id`  |
|from_id_\<hex_string>  |bigint |1  |interne à partir du nœud `graph_id`  |
|$from_id_\<hex_string> |NVARCHAR   |0  |externe à partir du nœud `node_id`  |
|to_obj_id_\<hex_string>    |INT    |1  |interne au nœud `object_id`  |
|to_id_\<hex_string>    |bigint |1  |interne au nœud `graph_id`  |
|$to_id_\<hex_string>   |NVARCHAR   |0  |externe au nœud `node_id`  |
 
### <a name="system-functions"></a>Fonctions système
Les fonctions intégrées suivantes sont ajoutées. Ces fonctionnalités aideront les utilisateurs extraire des informations à partir des colonnes générées. Notez que, ces méthodes ne validera pas l’entrée de l’utilisateur. Si l’utilisateur spécifie un non valide `sys.node_id` la méthode extraire la partie appropriée et renvoyez-le. Par exemple, OBJECT_ID_FROM_NODE_ID prendra un `$node_id` comme entrée et retourne l’object_id de la table, ce nœud appartient. 
 
|Intégré   |Description  |
|---  |---  |
|OBJECT_ID_FROM_NODE_ID |Extraire l’object_id à partir d’un `node_id`  |
|GRAPH_ID_FROM_NODE_ID  |Extraire le graph_id à partir d’un `node_id`  |
|NODE_ID_FROM_PARTS |Construire un node_id à partir d’un `object_id` et un `graph_id`  |
|OBJECT_ID_FROM_EDGE_ID |Extraire `object_id` à partir de `edge_id`  |
|GRAPH_ID_FROM_EDGE_ID  |Extraire l’identité à partir de `edge_id`  |
|EDGE_ID_FROM_PARTS |Construire `edge_id` de `object_id` et identité  |



## <a name="transact-sql-reference"></a>Informations de référence sur Transact-SQL 
Découvrez le [!INCLUDE[tsql-md](../../includes/tsql-md.md)] extensions introduites dans SQL Server et de la base de données SQL Azure, qui activer la création et l’interrogation des objets graphiques. Les extensions de langage de requête vous aider à la requête et parcourent le graphique à l’aide de la syntaxe d’art ASCII.
 
### <a name="data-definition-language-ddl-statements"></a>Instructions de langage de définition (DDL) de données

|Tâche   |Article connexe  |Remarques
|---  |---  |---  |
|CREATE TABLE |[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-sql-graph.md)|`CREATE TABLE` est désormais étendue pour prendre en charge la création d’une table en tant que nœud ou AS EDGE. Notez que le tableau de bord peut ou ne peut pas avoir tous les attributs définis par l’utilisateur.  |
|ALTER TABLE    |[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)|Les tables de nœuds et d’arêtes peuvent être modifiées de la même façon qu’une table relationnelle, en utilisant le `ALTER TABLE`. Les utilisateurs peuvent ajouter ou modifier les colonnes définies par l’utilisateur, les index ou contraintes. Toutefois, comme la modification des colonnes graphiques internes, `$node_id` ou `$edge_id`, entraîne une erreur.  |
|CREATE INDEX   |[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  |Les utilisateurs peuvent créer des index sur les pseudo colonnes et les colonnes définies par l’utilisateur dans les tables de nœuds et d’arêtes. Tous les types d’index sont pris en charge, y compris les index columnstore en cluster et non-cluster.  |
|CRÉER DES CONTRAINTES D’ARÊTE    |[EDGE CONSTRAINTS &#40;Transact-SQL&#41;](../../relational-databases/tables/graph-edge-constraints.md)  |Les utilisateurs peuvent maintenant créer les contraintes d’arête sur des tableaux de bord pour appliquer la sémantique spécifique et également de maintenir l’intégrité des données  |
|DROP TABLE |[DROP TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-table-transact-sql.md)  |Les tables de nœuds et d’arêtes peuvent être supprimés de la même façon qu’une table relationnelle, en utilisant le `DROP TABLE`. Toutefois, dans cette version, il n’existe aucune contrainte pour s’assurer qu’aucun bords ne pointent vers un nœud supprimé et suppression en cascade des bords, après la suppression d’un nœud ou d’une table de nœud n’est pas pris en charge. Il est recommandé que si une table de nœud est supprimée, les utilisateurs déposer des bords connectés aux nœuds de cette table de nœud manuellement pour maintenir l’intégrité du graphique.  |


### <a name="data-manipulation-language-dml-statements"></a>Instructions de langage de manipulation de données

|Tâche   |Article connexe  |Remarques
|---  |---  |---  |
|INSERT |[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-sql-graph.md)|Insertion dans une table de nœud n’est pas différent de l’insertion dans une table relationnelle. Les valeurs de `$node_id` colonne est générée automatiquement. Tentative d’insertion d’une valeur dans `$node_id` ou `$edge_id` colonne entraîne une erreur. Les utilisateurs doivent fournir des valeurs pour `$from_id` et `$to_id` colonnes lors de l’insertion dans une table d’arêtes. `$from_id` et `$to_id` sont le `$node_id` valeurs des nœuds qui se connecte un bord donné.  |
|Suppression | [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)|Données à partir des tables de nœuds ou d’arêtes peuvent être supprimées dans la même façon, car elle est supprimée à partir de tables relationnelles. Toutefois, dans cette version, il n’existe aucune contrainte pour s’assurer qu’aucun bords ne pointent vers un nœud supprimé et suppression en cascade des bords, après la suppression d’un nœud n’est pas pris en charge. Il est recommandé que chaque fois qu’un nœud est supprimé, tous les bords qui se connectés à ce nœud sont également supprimés, pour préserver l’intégrité du graphique.  |
|UPDATE |[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  |Valeurs des colonnes définies par l’utilisateur peuvent être mis à jour à l’aide de l’instruction de mise à jour. La mise à jour les colonnes de graphique interne, `$node_id`, `$edge_id`, `$from_id` et `$to_id` n’est pas autorisée.  |
|MERGE |[MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  |`MERGE` instruction est prise en charge sur une table de nœuds ou d’arêtes.  |


### <a name="query-statements"></a>Instructions de requête

|Tâche   |Article connexe  |Remarques
|---  |---  |---  |
|SELECT |[SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)|Nœuds et les bords sont stockées en interne en tant que tables, par conséquent, la plupart des opérations prises en charge sur une table dans SQL Server ou de la base de données SQL Azure est pris en charge sur les tables de nœuds et d’arêtes  |
|MATCH  | [MATCH &#40;Transact-SQL&#41;](../../t-sql/queries/match-sql-graph.md)|CORRESPONDANCE intégré est introduit pour prendre en charge les critères spéciaux et traversée par le biais du graphique.  |



## <a name="limitations-and-known-issues"></a>Limitations et problèmes connus  
Il existe certaines limitations sur les tables de nœuds et d’arêtes dans cette version :
* Les tables temporaires locales ou globales ne peut pas être des tables de nœuds ou d’arêtes.
* Types de tables et des variables de table ne peut pas être déclarées comme une table de nœuds ou d’arêtes. 
* Impossible de créer des tables de nœuds et d’arêtes comme tables temporelles avec version gérée par le système.   
* Les tables de nœuds et d’arêtes ne peut pas être des tables optimisées en mémoire.  
* Les utilisateurs ne peuvent pas mettre à jour le `$from_id` et `$to_id` colonnes d’un bord à l’aide d’instruction de mise à jour. Pour mettre à jour les nœuds qui se connecte un bord, les utilisateurs devront insérer le nouveau bord pointant vers les nouveaux nœuds et supprimer des précédent.
* Entre la base de données les requêtes sur les objets graphiques ne sont pas pris en charge. 


## <a name="next-steps"></a>Étapes suivantes
Pour vous familiariser avec la nouvelle syntaxe, consultez [SQL Database de graphique - exemple](./sql-graph-sample.md)
 

