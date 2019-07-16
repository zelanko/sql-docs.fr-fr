---
title: Traitement des graphes avec SQL Server et de la base de données SQL Azure | Microsoft Docs
ms.custom: ''
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
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: eb84f1cc40a05078910d10a48de67f1ac3467fe3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68035902"
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>Traitement des graphes avec SQL Server et de la base de données SQL Azure
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre des fonctionnalités de base de données de graphique pour modéliser des relations plusieurs-à-plusieurs. Les relations de graphique sont intégrées à [!INCLUDE[tsql-md](../../includes/tsql-md.md)] et de bénéficier des avantages de l’utilisation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que le système de gestion de base de données fondamentaux.


## <a name="what-is-a-graph-database"></a>Qu’est une base de données de graphique ?  
Une base de données de graphes est une collection de nœuds (ou sommets) et d’arêtes (ou relations). Un nœud représente une entité (par exemple, une personne ou une organisation) et une arête représente une relation entre deux nœuds qu’elle connecte (par exemple, des mentions j’aime ou des amis). Les nœuds et les bords peuvent avoir des propriétés qui s’y rapportent. Voici quelques fonctionnalités qui rendent une base de données de graphe unique :  
-   Les arêtes ou relations sont des entités de première classe dans une base de données de graphe, auxquelles des attributs ou des propriétés peuvent être associés. 
-   Un simple arête peut connecter de manière flexible plusieurs nœuds dans une base de données de graphe.
-   Vous pouvez facilement exprimer des critères spéciaux et des requêtes de navigation sur plusieurs tronçons.
-   Vous pouvez facilement exprimer une fermeture transitive et des requêtes polymorphes.

## <a name="when-to-use-a-graph-database"></a>Quand utiliser une base de données de graphique

Il n’est rien qu’une base de données de graphe puisse accomplir qui ne puisse être accompli à l’aide d’une base de données relationnelle. Toutefois, une base de données de graphique peut faciliter express certain type de requêtes. En outre, avec les optimisations spécifiques, certaines requêtes peuvent performantes. Votre décision de choisir l’une plutôt que l’autre peut dépendre des facteurs suivants :  
-   Votre application a des données hiérarchiques. Le type de données HierarchyID peut être utilisé pour implémenter des hiérarchies, mais il présente certaines limitations. Par exemple, il ne vous permet pas stocker plusieurs parents pour un nœud.
-   Votre application a des relations plusieurs-à-plusieurs complexes ; avec l’évolution de l’application, des relations sont ajoutées.
-   Vous devez analyser des données et relations interconnectées.

## <a name="graph-features-introduced-in-includesssqlv14includessssqlv14-mdmd"></a>Fonctionnalités de graphique introduites dans [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 
Nous avons commencé à ajouter des extensions de graphe à SQL Server, pour faciliter le stockage et interrogation des données de graphique. Les fonctionnalités suivantes sont introduites dans la première version. 


### <a name="create-graph-objects"></a>Créer des objets graphiques
[!INCLUDE[tsql-md](../../includes/tsql-md.md)] extensions permettra aux utilisateurs de créer des tables de nœuds ou d’arêtes. Les nœuds et les bords peuvent avoir des propriétés qui leur sont associées. Depuis, nœuds et les bords sont stockées en tant que tables, toutes les opérations qui sont pris en charge sur les tables relationnelles sont pris en charge sur la table de nœuds ou d’arêtes. Voici un exemple :  

```   
CREATE TABLE Person (ID INTEGER PRIMARY KEY, Name VARCHAR(100), Age INT) AS NODE;
CREATE TABLE friends (StartDate date) AS EDGE;
```   

![tables de personne amis](../../relational-databases/graphs/media/person-friends-tables.png "nœud Person et amis des tables de périphérie")  
Nœuds et les bords sont stockés sous forme de tables  

### <a name="query-language-extensions"></a>Extensions de langage de requête  
Nouvelle `MATCH` clause est introduite pour prendre en charge les critères spéciaux et navigation sur plusieurs sauts par le biais du graphique. Le `MATCH` fonction utilise la syntaxe de style ASCII art pour les critères spéciaux. Exemple :  

```   
-- Find friends of John
SELECT Person2.Name 
FROM Person Person1, Friends, Person Person2
WHERE MATCH(Person1-(Friends)->Person2)
AND Person1.Name = 'John';
```   
 
### <a name="fully-integrated-in-includessnoversionincludesssnoversion-mdmd-engine"></a>Entièrement intégré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur 
Extensions graphiques entièrement intégrées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur. Utilisez le même moteur de stockage, les métadonnées, processeur de requêtes, etc. pour stocker et interroger des données de graphique. Requête sur le graphique et les données relationnelles dans une requête unique. Combinant des fonctionnalités de graphique avec d’autres [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologies telles que columnstore, haute disponibilité, R services, etc. Base de données de graphique SQL prend également en charge toutes les les sécurité et conformité fonctionnalités disponibles avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
 
### <a name="tooling-and-ecosystem"></a>Outils et l’écosystème

Tirer parti des outils existants et l’écosystème qui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre. Outils tels que la sauvegarde et restauration, importer et exporter, fonctionnent BCP prêts à l’emploi. Autres outils ou des services tels que SSIS, SSRS ou Power BI fonctionnera avec les tables de graphique, la façon de travailler avec des tables relationnelles.

## <a name="edge-constraints"></a>Contraintes d’arête
Une contrainte d’arête est définie sur une table d’arêtes de graphe et une paire d’une ou plusieurs tables de nœud qui a un type de session donné peut se connecter. Cela offre aux utilisateurs un meilleur contrôle sur leur schéma de graphique. À l’aide de contraintes d’arête, les utilisateurs peuvent limiter le type de nœuds de qu'un bord donné est autorisé à se connecter. 

Pour en savoir plus sur la façon de créer et utiliser les contraintes d’arête, consultez [les contraintes d’arête](../../relational-databases/tables/graph-edge-constraints.md)

## <a name="merge-dml"></a>Fusion DML 
Le [fusion](../../t-sql/statements/merge-transact-sql.md) instruction effectue la requête insert, update ou supprimer des opérations sur une table cible selon les résultats d’une jointure avec une table source. Par exemple, vous pouvez synchroniser deux tables en insérant, de la mise à jour ou de suppression de lignes dans une table cible selon les différences entre la table cible et la table source. À l’aide des prédicats de correspondance dans une instruction MERGE est maintenant pris en charge sur Azure SQL Database et SQL Server vNext. Autrement dit, il est désormais possible de fusionner vos données de graphique actuelle (tables de nœuds ou d’arêtes) avec de nouvelles données à l’aide des correspondance de prédicats pour spécifier les relations de graphique dans une seule instruction, au lieu des instructions INSERT/UPDATE/DELETE distinctes.

Pour en savoir plus sur l’utilisation de la correspondance dans la fusion DML, consultez [instruction MERGE](../../t-sql/statements/merge-transact-sql.md)

## <a name="shortest-path"></a>Chemin d’accès le plus court
Le [SHORTEST_PATH](./sql-graph-shortest-path.md) fonction recherche le chemin le plus court entre les 2 nœuds dans un graphique ou à partir d’un nœud donné à tous les autres nœuds dans le graphique. Chemin d’accès le plus court peut également servir pour rechercher une fermeture transitive ou pour les traversées de longueur arbitraire dans le graphique. 

 ## <a name="next-steps"></a>Étapes suivantes  
Lire le [base de données SQL Graph - Architecture](./sql-graph-architecture.md)
   

