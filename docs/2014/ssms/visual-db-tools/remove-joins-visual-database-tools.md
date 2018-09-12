---
title: Supprimer des jointures (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a9bcc6fa9915635b2bc7c7bffb98e85a4f021de
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43809235"
---
# <a name="remove-joins-visual-database-tools"></a>Supprimer des jointures (Visual Database Tools)
  Si vous ne souhaitez pas que les tables soient liées par une jointure interne ou externe, vous pouvez supprimer celle-ci. Vous pouvez par exemple supprimer une jointure créée automatiquement entre deux tables par le [Concepteur de requêtes et de vues](visual-database-tools.md) .  
  
> [!NOTE]  
>  La suppression d'une jointure n'a aucune répercussion sur la relation sous-jacente existant dans la base de données.  
  
 Si deux tables jointes font partie de votre requête et que vous supprimez toutes les conditions de jointure entre elles, la requête obtenue devient le produit des deux tables, en d'autres termes une instruction CROSS JOIN.  
  
### <a name="to-remove-a-join"></a>Pour supprimer une jointure  
  
-   Dans le [volet Schéma](diagram-pane-visual-database-tools.md), sélectionnez la ligne de jointure à supprimer, puis appuyez sur la touche Suppr. Il est possible de sélectionner et supprimer plusieurs lignes de jointure à la fois.  
  
 Le Concepteur de requêtes et de vues supprime la ligne de jointure et modifie l’instruction dans le [volet SQL](sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Joindre automatiquement des Tables &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md)   
 [Joindre manuellement des Tables &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md)   
 [Interroger avec des jointures &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)  
  
  
