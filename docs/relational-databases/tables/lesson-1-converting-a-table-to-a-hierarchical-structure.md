---
title: "Le&#231;on 1 : conversion d&#39;une table en une structure hi&#233;rarchique | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "HierarchyID"
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Le&#231;on 1 : conversion d&#39;une table en une structure hi&#233;rarchique
Les clients qui ont des tables utilisant des jointures réflexives pour exprimer des relations hiérarchiques peuvent convertir leurs tables en structure hiérarchique en suivant les procédures fournies dans cette leçon. Il est relativement facile d'effectuer une migration de cette représentation vers une autre à l'aide de **hierarchyid**. Après la migration, les utilisateurs disposeront d'une représentation hiérarchique compacte et facile à comprendre, qui peut être indexée de plusieurs façons pour que les requêtes soient efficaces.  
  
Cette leçon examine une table existante, crée une table contenant une colonne **hierarchyid** , remplit la table avec les données de la table source, puis illustre trois stratégies d'indexation. Cette leçon contient les rubriques suivantes :  
  
-   [Étude de la structure actuelle de la table Employee](../../relational-databases/tables/examining-the-current-structure-of-the-employee-table.md)  
  
-   [Remplissage d'une table avec des données hiérarchiques existantes](../../relational-databases/tables/populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Optimisation de la table NewOrg](../../relational-databases/tables/optimizing-the-neworg-table.md)  
  
-   [Résumé : Conversion d'une table en une structure hiérarchique](../../relational-databases/tables/summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## Conditions préalables  
Cette leçon requiert l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## Tâche suivante de la leçon  
[Étude de la structure actuelle de la table Employee](../../relational-databases/tables/examining-the-current-structure-of-the-employee-table.md)  
  
## Leçon suivante  
[Leçon 2 : Création et gestion de données dans une table hiérarchique](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
  
