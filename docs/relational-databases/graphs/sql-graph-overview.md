---
title: Traitement des graphes avec SQL Server et de la base de données SQL Azure | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2017
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dcabc19d3c83cd1ed4c9ee7b8047759e2550863e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62502487"
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>Traitement des graphes avec SQL Server et de la base de données SQL Azure
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre des fonctionnalités de base de données de graphique pour modéliser des relations plusieurs-à-plusieurs. Les relations de graphique sont intégrées à [!INCLUDE[tsql-md](../../includes/tsql-md.md)] et de bénéficier des avantages de l’utilisation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que le système de gestion de base de données fondamentaux.


## <a name="what-is-a-graph-database"></a>Qu’est une base de données de graphique ?  
Une base de données de graphes est une collection de nœuds (ou sommets) et d’arêtes (ou relations). Un nœud représente une entité (par exemple, une personne ou organisation) et une arête représente une relation entre les deux nœuds qu’elle connecte (par exemple, les mentions J’aime ou les amis). Les nœuds et les bords peuvent avoir des propriétés qui s’y rapportent. Voici quelques fonctionnalités qui rendent une base de données de graphique unique :  
-   Bords ou les relations sont des entités de première classes dans une base de données de graphique et peuvent avoir attributs ou les propriétés associées. 
-   Un contour unique peut connecter plusieurs nœuds dans une base de données de graphique de manière flexible.
-   Vous pouvez facilement exprimer critères spéciaux et les requêtes de navigation sur plusieurs sauts.
-   Vous pouvez facilement exprimer fermeture transitive et requêtes polymorphes.

## <a name="when-to-use-a-graph-database"></a>Quand utiliser une base de données de graphique

Rien n’est qu'une base de données de graphique peut atteindre, qui ne peut pas être obtenue à l’aide d’une base de données relationnelle. Toutefois, une base de données de graphique peut faciliter express certain type de requêtes. En outre, avec les optimisations spécifiques, certaines requêtes peuvent performantes. Votre décision en choisir un plutôt que l’autre peut reposer sur des facteurs suivants :  
-   Votre application a des données hiérarchiques. Le type de données HierarchyID peut être utilisé pour implémenter des hiérarchies, mais il présente certaines limitations. Par exemple, il ne vous permet pas stocker plusieurs parents pour un nœud.
-   Votre application a des relations plusieurs-à-plusieurs complexes ; avec l’évolution de l’application, des relations sont ajoutées.
-   Vous avez besoin d’analyser les relations et données interconnectées.

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

 ## <a name="next-steps"></a>Étapes suivantes  
Lire le [base de données SQL Graph - Architecture](./sql-graph-architecture.md)
   

