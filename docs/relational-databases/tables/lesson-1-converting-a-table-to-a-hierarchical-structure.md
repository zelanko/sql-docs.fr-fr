---
title: "Leçon 1 : Conversion d’une table en structure hiérarchique | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a6a17f0c1773063b30821a2458b8c408e85fb7e1
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Leçon 1 : Conversion d'une table en structure hiérarchique
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] Les clients qui ont des tables utilisant des jointures réflexives pour exprimer des relations hiérarchiques peuvent convertir leurs tables en structure hiérarchique, en suivant les procédures fournies dans cette leçon. Il est relativement facile d'effectuer une migration de cette représentation vers une autre à l'aide de **hierarchyid**. Après la migration, les utilisateurs disposeront d'une représentation hiérarchique compacte et facile à comprendre, qui peut être indexée de plusieurs façons pour que les requêtes soient efficaces.  
  
Cette leçon examine une table existante, crée une table contenant une colonne **hierarchyid** , remplit la table avec les données de la table source, puis illustre trois stratégies d'indexation. Cette leçon contient les rubriques suivantes :  
  
-   [Étude de la structure actuelle de la table Employee](../../relational-databases/tables/lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Remplissage d'une table avec des données hiérarchiques existantes](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Optimisation de la table NewOrg](../../relational-databases/tables/lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Résumé : Conversion d'une table en une structure hiérarchique](../../relational-databases/tables/lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Prerequisites  
Cette leçon requiert l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Étude de la structure actuelle de la table Employee](../../relational-databases/tables/lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 2 : création et gestion de données dans une table hiérarchique](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
  
