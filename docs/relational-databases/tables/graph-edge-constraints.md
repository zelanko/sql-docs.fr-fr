---
title: Contraintes d’arête de graphe | Microsoft Docs
ms.custom: ''
ms.date: 09/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d8c2549196021754dc5ad343a38604eba6651f5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833867"
---
# <a name="edge-constraints"></a>Contraintes d’arête
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Les contraintes d’arête peuvent être utilisées pour appliquer l’intégrité des données et une sémantique spécifique sur les tables d’arêtes dans une base de données de graphe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
  
Cet article contient les sections suivantes.  
  
[Contraintes d’arête](../../relational-databases/tables/graph-edge-constraints.md#Connection)  

[Contraintes d’arête](../../relational-databases/tables/graph-edge-constraints.md#Connection)  
  
[Tâches associées](../../relational-databases/tables/graph-edge-constraints.md#Tasks)  
  
##  <a name="Connection"></a> Contraintes d’arête
 Dans la première version des fonctionnalités de graphe, les tables d’arêtes n’appliquaient rien pour les points de terminaison de l’arête. Autrement dit, une arête dans une base de données de graphe pouvait connecter n’importe quel nœud à n’importe quel autre nœud, quel que soit leur type. 

 Cette version introduit des contraintes d’arête, qui permettent aux utilisateurs d’ajouter des contraintes à leurs tables d’arêtes, appliquant ainsi une sémantique spécifique et préservant l’intégrité des données. Lorsqu’une nouvelle arête est ajoutée à une table d’arêtes avec des contraintes d’arête, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] fait en sorte que les nœuds que l’arête essaie de connecter existent dans les tables de nœuds appropriées. Il est également garanti qu’un nœud ne peut pas être supprimé, s’il est encore référencé par une arête. 

 ### <a name="edge-constraint-clauses"></a>Clauses de contrainte d’arête
 Chaque contrainte d’arête se compose d’une ou plusieurs clauses de contrainte d’arête. Une clause de contrainte d’arête est la paire de nœuds FROM et TO que l’arête donnée pouvait connecter. 

 Considérez que vous avez les nœuds `Product` et `Customer` dans votre graphe et que vous utilisez l’arête `Bought` pour connecter ces nœuds. La clause de contrainte d’arête spécifie la paire de nœuds FROM et TO, et la direction de l’arête. Dans ce cas, la clause de contrainte d’arête sera `Customer` TO `Product`. Autrement dit, l’insertion d’une arête `Bought` allant d’un `Customer` à `Product` sera autorisée. Les tentatives d’insertion d’une arête allant de `Product` à `Customer` échouent. 
  
- Une clause de contrainte d’arête contient une paire de tables de nœuds FROM et TO sur laquelle la contrainte d’arête est appliquée. 
  
- Les utilisateurs peuvent spécifier plusieurs clauses de contrainte d’arête par contrainte d’arête, lesquelles seront appliquées en tant que disjonction.

- Si plusieurs contraintes d’arête sont créées sur une table d’arêtes unique, les arêtes doivent satisfaire TOUTES les contraintes à autoriser.
  
### <a name="indexes-on-edge-constraints"></a>Index sur les contraintes d’arête
 La création d’une contrainte d’arête ne crée pas automatiquement un index correspondant sur les colonnes `$from_id` et `$to_id` dans la table d’arêtes. La création manuelle d’un index sur une paire `$from_id`, `$to_id` est recommandée si vous avez des requêtes de recherche de points ou une charge de travail OLTP. 

##  <a name="Tasks"></a> Tâches associées  
 Le tableau suivant répertorie les tâches courantes associées aux contraintes d’arête.  
  
|Tâche|Article|  
|----------|-----------|  
|Explique comment créer des contraintes d’arête.|[Créer des contraintes d’arête](../../relational-databases/tables/create-edge-constraints.md)|  
|Explique comment supprimer une contrainte d’arête.|[Supprimer une contrainte d’arête](../../relational-databases/tables/delete-edge-constraint.md)|  
|Explique comment modifier une contrainte d’arête.|[Modifier une contrainte d’arête](../../relational-databases/tables/modify-edge-constraint.md)|  
|Explique comment afficher les propriétés d’une contrainte d’arête.|[Afficher les propriétés d’une contrainte d’arête](../../relational-databases/tables/view-edge-constraint-properties.md)|  
