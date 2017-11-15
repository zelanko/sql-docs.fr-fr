---
title: "Créer automatiquement des jointures réflexives (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 32bf78f4039967e3ecd9aa08084325edffc81104
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Créer automatiquement des jointures réflexives (Visual Database Tools)
Si une table possède une relation réflexive dans la base de données, vous pouvez la joindre à elle-même de façon automatique.  
  
### <a name="to-create-a-self-join-automatically"></a>Pour créer automatiquement une jointure réflexive  
  
1.  Ajoutez la table que vous souhaitez utiliser au [volet Schéma](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) .  
  
2.  Ajoutez de nouveau la même table, afin que le volet Schéma affiche deux fois la même table.  
  
    Le [Concepteur de requêtes et de vues](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) assigne un alias à la seconde instance en ajoutant un numéro séquentiel au nom de la table. Par ailleurs, il crée une ligne de jointure entre les deux rectangles qui représentent les deux façons différentes dont la table intervient dans la requête.  
  
## <a name="see-also"></a>Voir aussi  
[Interroger avec des jointures &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
