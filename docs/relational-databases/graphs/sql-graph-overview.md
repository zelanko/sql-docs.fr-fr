---
title: Traitement de graphe
titleSuffix: SQL Server and Azure SQL Database
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, overview
ms.assetid: ''
author: shkale-msft
ms.author: shkale
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3ca26af4738de25937b71e0c97c6272414a0957a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74096084"
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>Traitement de graphiques avec SQL Server et Azure SQL Database
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]offre des fonctionnalités de base de données de graphiques pour modéliser des relations plusieurs-à-plusieurs. Les relations de graphique sont intégrées [!INCLUDE[tsql-md](../../includes/tsql-md.md)] dans et bénéficient des avantages de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’utilisation de en tant que système de gestion de base de données de base.


## <a name="what-is-a-graph-database"></a>Qu’est-ce qu’une base de données Graph ?  
Une base de données de graphes est une collection de nœuds (ou sommets) et d’arêtes (ou relations). Un nœud représente une entité (par exemple, une personne ou une organisation) et une arête représente une relation entre deux nœuds qu’elle connecte (par exemple, des mentions j’aime ou des amis). Les nœuds et les bords peuvent avoir des propriétés qui leur sont associées. Voici quelques fonctionnalités qui rendent une base de données de graphe unique :  
-   Les arêtes ou relations sont des entités de première classe dans une base de données de graphe, auxquelles des attributs ou des propriétés peuvent être associés. 
-   Un simple arête peut connecter de manière flexible plusieurs nœuds dans une base de données de graphe.
-   Vous pouvez facilement exprimer des critères spéciaux et des requêtes de navigation sur plusieurs tronçons.
-   Vous pouvez facilement exprimer une fermeture transitive et des requêtes polymorphes.

## <a name="when-to-use-a-graph-database"></a>Quand utiliser une base de données de graphiques

Il n’est rien qu’une base de données de graphe puisse accomplir qui ne puisse être accompli à l’aide d’une base de données relationnelle. Toutefois, une base de données de graphiques peut faciliter l’expression de certains types de requêtes. En outre, avec des optimisations spécifiques, certaines requêtes peuvent être plus performantes. Votre décision de choisir l’une plutôt que l’autre peut dépendre des facteurs suivants :  
-   Votre application a des données hiérarchiques. Le type de données HierarchyID peut être utilisé pour implémenter des hiérarchies, mais il présente certaines limites. Par exemple, il ne vous permet pas de stocker plusieurs parents pour un nœud.
-   Votre application a des relations plusieurs-à-plusieurs complexes. à mesure que l’application évolue, de nouvelles relations sont ajoutées.
-   Vous devez analyser des données et relations interconnectées.

## <a name="graph-features-introduced-in-includesssqlv14includessssqlv14-mdmd"></a>Fonctionnalités graphiques introduites dans[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 
Nous commençons à ajouter des extensions graphiques à SQL Server, pour faciliter le stockage et l’interrogation des données graphiques. Les fonctionnalités suivantes sont introduites dans la première version. 


### <a name="create-graph-objects"></a>Créer des objets graphiques
[!INCLUDE[tsql-md](../../includes/tsql-md.md)]les extensions permettent aux utilisateurs de créer des tables de nœuds ou d’arêtes. Des propriétés peuvent être associées aux nœuds et aux bords. Étant donné que les nœuds et les bords sont stockés sous forme de tables, toutes les opérations qui sont prises en charge sur les tables relationnelles sont prises en charge sur une table de nœuds ou d’arêtes. Voici un exemple :   

```   
CREATE TABLE Person (ID INTEGER PRIMARY KEY, Name VARCHAR(100), Age INT) AS NODE;
CREATE TABLE friends (StartDate date) AS EDGE;
```   

![person-Friends-tables](../../relational-databases/graphs/media/person-friends-tables.png "Nœud Person et tables de bord des amis")  
Les nœuds et les bords sont stockés sous forme de tables  

### <a name="query-language-extensions"></a>Extensions du langage de requête  
La `MATCH` nouvelle clause est introduite pour prendre en charge les critères spéciaux et la navigation sur plusieurs tronçons dans le graphique. La `MATCH` fonction utilise la syntaxe de style d’art ASCII pour les critères spéciaux. Par exemple :  

```   
-- Find friends of John
SELECT Person2.Name 
FROM Person Person1, Friends, Person Person2
WHERE MATCH(Person1-(Friends)->Person2)
AND Person1.Name = 'John';
```   
 
### <a name="fully-integrated-in-includessnoversionincludesssnoversion-mdmd-engine"></a>Entièrement intégré au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur 
Les extensions Graph sont entièrement intégrées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le moteur. Utilisez le même moteur de stockage, les mêmes métadonnées, le même processeur de requêtes, etc. pour stocker et interroger les données de graphique. Interroger des données graphiques et relationnelles dans une seule requête. Combiner les fonctionnalités graphiques avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’autres technologies telles que COLUMNSTORE, ha, R services, etc. La base de données SQL Graph prend également en charge toutes les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de sécurité et de conformité disponibles avec.
 
### <a name="tooling-and-ecosystem"></a>Outils et écosystème

Tirez parti des outils et de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écosystème existants qui offrent. Les outils tels que la sauvegarde et la restauration, l’importation et l’exportation, BCP fonctionnent tout simplement dès à présent. D’autres outils ou services tels que SSIS, SSRS ou Power BI fonctionnent avec les tables graphiques, de la même façon qu’ils fonctionnent avec les tables relationnelles.

## <a name="edge-constraints"></a>Contraintes d’arête
Une contrainte Edge est définie sur une table des bords du graphique et est une paire de tables de nœud qu’un type de périphérie donné peut connecter. Cela donne aux utilisateurs un meilleur contrôle sur leur schéma graphique. Avec l’aide des contraintes de périphérie, les utilisateurs peuvent limiter le type de nœuds auxquels un bord donné est autorisé à se connecter. 

Pour en savoir plus sur la création et l’utilisation de contraintes Edge, consultez [contraintes Edge](../../relational-databases/tables/graph-edge-constraints.md)

## <a name="merge-dml"></a>Fusion DML 
L’instruction [Merge](../../t-sql/statements/merge-transact-sql.md) effectue des opérations d’insertion, de mise à jour ou de suppression sur une table cible en fonction des résultats d’une jointure avec une table source. Par exemple, vous pouvez synchroniser deux tables en insérant, mettant à jour ou supprimant des lignes dans une table cible en fonction des différences entre la table cible et la table source. L’utilisation de prédicats de correspondance dans une instruction MERGE est désormais prise en charge sur Azure SQL Database et SQL Server vNext. Autrement dit, il est désormais possible de fusionner vos données de graphe actuelles (tables de nœuds ou d’arêtes) avec de nouvelles données à l’aide des prédicats de correspondance pour spécifier les relations de graphique dans une instruction unique, au lieu d’instructions d’insertion/mise à jour/suppression distinctes.

Pour en savoir plus sur la façon dont la correspondance peut être utilisée dans la fusion DML, consultez l' [instruction MERGE](../../t-sql/statements/merge-transact-sql.md)

## <a name="shortest-path"></a>Chemin d’accès le plus rapide
La fonction [SHORTEST_PATH](./sql-graph-shortest-path.md) trouve le chemin le plus rapide entre les 2 nœuds d’un graphique ou à partir d’un nœud donné vers tous les autres nœuds du graphique. Le chemin le plus rapide peut également être utilisé pour rechercher une fermeture transitive ou pour des parcours de longueur arbitraires dans le graphique. 

 ## <a name="next-steps"></a>Étapes suivantes  
Lire la [base de données SQL Graph-architecture](./sql-graph-architecture.md)
   

