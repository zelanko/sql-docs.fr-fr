---
title: Créer automatiquement des jointures réflexives (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d541ce3229ee01c2fb213eafb1e8c7f55a4b984a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196549"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Créer automatiquement des jointures réflexives (Visual Database Tools)
  Si une table possède une relation réflexive dans la base de données, vous pouvez la joindre à elle-même de façon automatique.  
  
### <a name="to-create-a-self-join-automatically"></a>Pour créer automatiquement une jointure réflexive  
  
1.  Ajoutez la table que vous souhaitez utiliser au [volet Schéma](visual-database-tools.md) .  
  
2.  Ajoutez de nouveau la même table, afin que le volet Schéma affiche deux fois la même table.  
  
     Le [Concepteur de requêtes et de vues](query-and-view-designer-tools-visual-database-tools.md) assigne un alias à la seconde instance en ajoutant un numéro séquentiel au nom de la table. Par ailleurs, il crée une ligne de jointure entre les deux rectangles qui représentent les deux façons différentes dont la table intervient dans la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Interroger avec des jointures &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)  
  
  
