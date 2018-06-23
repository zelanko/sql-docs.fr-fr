---
title: 'Leçon 1 : Conversion d’une table en structure hiérarchique | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c8259ba2dcf738b090b7e4cd1f829d89c8d1a3ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040835"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Leçon 1 : Conversion d'une table en structure hiérarchique
  Les clients qui ont des tables utilisant des jointures réflexives pour exprimer des relations hiérarchiques peuvent convertir leurs tables en structure hiérarchique en suivant les procédures fournies dans cette leçon. Il est relativement facile d'effectuer une migration de cette représentation vers une autre à l'aide de `hierarchyid`. Après la migration, les utilisateurs disposeront d'une représentation hiérarchique compacte et facile à comprendre, qui peut être indexée de plusieurs façons pour que les requêtes soient efficaces.  
  
 Cette leçon examine une table existante, crée une table contenant une colonne `hierarchyid`, remplit la table avec les données de la table source, puis illustre trois stratégies d'indexation. Cette leçon contient les rubriques suivantes :  
  
-   [Étude de la structure actuelle de la table Employee](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Remplissage d'une table avec des données hiérarchiques existantes](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Optimisation de la table NewOrg](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Résumé : Conversion d'une table en une structure hiérarchique](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Prérequis  
 Cette leçon requiert l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étude de la structure actuelle de la table Employee](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : création et gestion de données dans une table hiérarchique](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  