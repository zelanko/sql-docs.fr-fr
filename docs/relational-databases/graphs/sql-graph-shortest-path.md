---
title: Chemin d’accès le plus court (graphe SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- SHORTEST PATH
- SHORTEST_PATH
dev_langs:
- TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ef8f38acbf621a9c73a0d85bca579c8b7c87aa13
ms.sourcegitcommit: 9d3ece500fa0e4a9f4fefc88df4af1db9431c619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67463542"
---
# <a name="shortestpath-transact-sql"></a>SHORTEST_PATH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver2015-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Spécifie une condition de recherche pour un graphique, qui est recherchés de manière récursive ou de façon répétée. SHORTEST_PATH permet à l’intérieur de correspondance avec les tables de nœuds et edge graph, dans l’instruction SELECT. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="shortest-path"></a>Chemin d’accès le plus court
La fonction SHORTEST_PATH vous permet de rechercher :    
* Un chemin d’accès le plus court entre deux nœuds données/entités
* Chemins d’accès le plus court source unique.
* Chemin d’accès le plus court à partir de plusieurs nœuds de la source à plusieurs nœuds cibles.

Il prend un modèle de longueur arbitraire en tant qu’entrée et retourne un chemin d’accès le plus court qui existe entre deux nœuds. Cette fonction peut uniquement être utilisée à l’intérieur de correspondance. La fonction ne retourne qu’un seul chemin le plus court entre deux nœuds donnés. S’il existe, deux ou plusieurs chemins d’accès le plus court de la même longueur entre toute paire de nœuds source et de destination, la fonction retourne qu’un seul chemin d’accès qui a été trouvé le premier pendant le parcours. Notez que, un modèle de longueur arbitraire peut uniquement être spécifié à l’intérieur d’une fonction SHORTEST_PATH. 

Reportez-vous à la [correspondance (graphe SQL)](../../t-sql/queries/match-sql-graph.md) pour la syntaxe. 

## <a name="for-path"></a>POUR LE CHEMIN D’ACCÈS
Chemin d’accès doit être utilisée avec n’importe quel nom de table de nœuds ou d’arêtes dans la clause FROM, qui participera à un modèle de longueur arbitraire. POUR le chemin d’accès indique au moteur que la table de nœuds ou d’arêtes retournera une collection ordonnée représentant la liste de nœuds ou d’arêtes trouvées avec le chemin d’accès parcouru. Les attributs à partir de ces tables ne peut pas être projetés directement dans la clause SELECT. Pour prévoir des attributs à partir de ces tables, fonctions d’agrégation chemin d’accès du graphique doit être utilisé.  

## <a name="arbitrary-length-pattern"></a>Modèle de longueur arbitraire
Ce modèle inclut les nœuds et les bords qui doivent être parcourus à plusieurs reprises jusqu'à ce que le nœud souhaité soit atteint ou jusqu'à ce que le nombre maximal d’itérations tel que spécifié dans le modèle est remplie. Chaque fois que la requête est exécutée, le résultat de l’exécution de ce modèle sera une collection ordonnée des nœuds et des bords parcourus le long du tracé à partir du nœud de démarrage pour le nœud de fin. Il s’agit d’un modèle de syntaxe d’expression régulière style et les quantificateurs deux modèle suivantes sont prises en charge :

* **‘+’** : Répétez le modèle 1 ou plusieurs fois. Terminer dès qu’un chemin d’accès le plus court est trouvé.
* **{1, n}** : Répétez le modèle 1 à « n » fois. Terminer dès qu’une plus courte est trouvée.

## <a name="lastnode"></a>LAST_NODE
LAST_NODE() fonction permet le chaînage des deux modèles de traversée de longueur arbitraire. Il peut être utilisé dans les scénarios où :    
* Plusieurs modèles de chemin le plus court sont utilisés dans une requête et un modèle commence au niveau du dernier nœud du modèle précédent.
* Fusion de deux modèles de chemin d’accès le plus court à la même LAST_NODE().

## <a name="graph-path-order"></a>Ordre de chemin d’accès de graphique
Commande de chemin d’accès graphique fait référence à l’ordre des données dans le chemin de sortie. L’ordre de chemin d’accès de sortie commence toujours à la partie non récursive du modèle suivi par les nœuds/bords qui s’affichent dans la partie récursive. L’ordre dans lequel le graphique est parcouru pendant l’optimisation/exécution de la requête n’a rien à faire avec l’ordre d’impression dans la sortie. De même, la direction de la flèche dans le modèle récursive également n’affecte pas l’ordre de chemin d’accès du graphique. 

## <a name="graph-path-aggregate-functions"></a>Fonctions d’agrégation graphique chemin d’accès
Étant donné que les bords et les nœuds impliqués dans le modèle de longueur arbitraire retour une collection (des nœuds et le bord parcourus dans ce chemin d’accès), les utilisateurs ne peut pas projeter les attributs directement à l’aide de la syntaxe tablename.attributename conventionnel. Requêtes où c’est obligatoire pour les valeurs d’attribut de projet dans les tables de nœuds ou d’arêtes intermédiaires, dans le chemin d’accès parcouru, utilisez suivant des fonctions d’agrégation graphique chemin d’accès : STRING_AGG, LAST_VALUE, SUM, AVG, MIN, MAX et COUNT. La syntaxe générale pour utiliser ces fonctions d’agrégation dans la clause SELECT est :

```
<GRAPH_PATH_AGGREGATE_FUNCTION>(<expression> , <separator>)  <order_clause>

    <order_clause> ::=
        { WITHIN GROUP (GRAPH PATH) }

    <GRAPH_PATH_AGGREGATE_FUNCTION> ::=
          STRING_AGG
        | LAST_VALUE
        | SUM
        | COUNT
        | AVG
        | MIN
        | MAX

```

### <a name="stringagg"></a>STRING_AGG
La fonction STRING_AGG prend une expression et le séparateur en tant qu’entrée et retourne une chaîne. Les utilisateurs peuvent utiliser cette fonction dans la clause SELECT aux attributs de projet à partir des nœuds intermédiaires ou des bords dans le chemin d’accès parcouru. 

### <a name="lastvalue"></a>LAST_VALUE
Au projet d’attributs à partir du dernier nœud de chemin d’accès parcouru, fonction d’agrégation LAST_VALUE peuvent être utilisés. C’est une erreur pour fournir des alias de table edge en tant qu’entrée à cette fonction, uniquement les noms de table de nœud ou alias peuvent être utilisés.

**Nœud de la dernière**: Le dernier nœud fait référence au nœud qui apparaît en dernier dans le chemin d’accès parcouru, quelle que soit la direction de la flèche dans le prédicat de correspondance. Par exemple : `MATCH(SHORTEST_PATH(n(-(e)->p)+) )`. Ici, le dernier nœud dans le chemin d’accès sera le dernier nœud P visité. 

En revanche, dernier nœud est le dernier nœud nième dans le chemin d’accès du graphique de sortie pour ce modèle : `MATCH(SHORTEST_PATH((n<-(e)-)+p))`    

### <a name="sum"></a>SUM
Cette fonction retourne la somme des valeurs d’attribut de nœud/edge fourni ou une expression qui est apparu dans le chemin d’accès traversé.

### <a name="count"></a>COUNT
Cette fonction retourne le nombre de valeurs non null de l’attribut de nœud/edge souhaité dans le chemin d’accès. La fonction COUNT prend en charge le ' *' opérateur avec un alias de table de nœuds ou d’arêtes. Sans l’alias de table nœuds ou d’arêtes, l’utilisation de * est ambigu et provoque une erreur.

    {  COUNT( <expression> | <node_or_edge_alias>.* )  <order_clause>  }


### <a name="avg"></a>AVG
Retourne la moyenne des valeurs d’attribut de nœud/edge fourni ou une expression qui est apparu dans le chemin d’accès traversé.

### <a name="min"></a>MIN
Retourne la valeur minimale à partir de l’expression est apparue dans le chemin d’accès traversé ou les valeurs d’attribut de nœud/edge fourni.

### <a name="max"></a>MAX
Retourne la valeur maximale de l’expression est apparue dans le chemin d’accès traversé ou les valeurs d’attribut de nœud/edge fourni.

## <a name="remarks"></a>Notes  
shortest_path fonction peut uniquement être utilisée à l’intérieur de correspondance.     
LAST_NODE est uniquement pris en charge dans shortest_path.     
Recherche de chemin le plus court pondérée, tous les chemins d’accès ou tous les chemins d’accès le plus court n’est pas pris en charge.         
Dans certains cas, les mauvais plans peuvent être générés pour les requêtes avec un plus grand nombre de sauts, ce qui entraîne des temps d’exécution de requête plus élevées. À l’aide d’un indicateur de jointure de hachage peut aider.    


## <a name="examples"></a>Exemples 
Pour les requêtes de l’exemple illustrés ici, nous allons ot utilisent le nœud et des tableaux de bord créés dans [exemple de graphe SQL](./sql-graph-sample.md)

### <a name="a--find-shortest-path-between-2-people"></a>A.  Rechercher le chemin le plus court entre les 2 personnes
 Dans l’exemple suivant, nous trouver chemin le plus court entre Jacob et Alice. Nous aurons besoin le nœud Person et edge FriendOf créé à partir de l’exemple de script graphique. 

 ```
SELECT PersonName, Friends
FROM (  
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        LAST_VALUE(Person2.name) WITHIN GROUP (GRAPH PATH) AS LastNode
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
    AND Person1.name = 'Jacob'
) AS Q
WHERE Q.LastNode = 'Alice'
 ```

 ### <a name="b--find-shortest-path-from-a-given-node-to-all-other-nodes-in-the-graph"></a>B.  Rechercher le chemin le plus court à partir d’un nœud donné à tous les autres nœuds dans le graphique. 
 L’exemple suivant recherche toutes les personnes qui Jacob est connecté à dans le graphique et le chemin d’accès le plus court à partir de Jacob à toutes les personnes. 

 ```
SELECT
    Person1.name AS PersonName, 
    STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends
FROM
    Person AS Person1,
    friendOf FOR PATH AS fo,
    Person FOR PATH  AS Person2
WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
AND Person1.name = 'Jacob'
 ```

### <a name="c--count-the-number-of-hopslevels-traversed-to-go-from-one-person-to-another-in-the-graph"></a>C.  Compter le nombre de sauts/niveaux parcourue pour accéder à partir d’une personne à l’autre dans le graphique.
 L’exemple suivant recherche le chemin d’accès le plus court entre Jacob et Alice et imprime le nombre de sauts que nécessaire pour passer de Jacob à Alice. 

 ```
 SELECT PersonName, Friends, levels
FROM (  
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        LAST_VALUE(Person2.name) WITHIN GROUP (GRAPH PATH) AS LastNode,
        COUNT(Person2.name) WITHIN GROUP (GRAPH PATH) AS levels
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
    AND Person1.name = 'Jacob'
) AS Q
WHERE Q.LastNode = 'Alice'
 ```

### <a name="d-find-people-1-3-hops-away-from-a-given-person"></a>D. Rechercher des personnes en dehors d’une personne donnée, les sauts de 1 à 3
L’exemple suivant recherche le chemin d’accès le plus court entre Jacob et toutes les personnes auquel il est connecté dans les graphique 1-3 tronçons de lui. 

```
SELECT
    Person1.name AS PersonName, 
    STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends
FROM
    Person AS Person1,
    friendOf FOR PATH AS fo,
    Person FOR PATH  AS Person2
WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2){1,3}))
AND Person1.name = 'Jacob'
```

### <a name="e-find-people-exactly-2-hops-away-from-a-given-person"></a>E. Rechercher des personnes sauts exactement 2 en dehors d’une personne donnée
L’exemple suivant recherche le chemin d’accès le plus court entre Jacob et les personnes qui sont exactement 2 tronçons de lui dans le graphique. 

```
SELECT PersonName, Friends
FROM (
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        COUNT(Person2.name) WITHIN GROUP (GRAPH PATH) AS levels
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2){1,3}))
    AND Person1.name = 'Jacob'
) Q
WHERE Q.levels = 2
```

## <a name="see-also"></a>Voir aussi  
 [CORRESPONDANCE (graphe SQL)](../../t-sql/queries/match-sql-graph.md)    
 [CREATE TABLE &#40;SQL Graph&#41;](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (SQL Graph)](../../t-sql/statements/insert-sql-graph.md)]  
 [Traitement des graphes avec SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md)     
 
