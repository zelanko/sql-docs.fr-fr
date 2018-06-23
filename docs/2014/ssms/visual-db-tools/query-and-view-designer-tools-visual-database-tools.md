---
title: Outils du Concepteur de requêtes et de vues (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vdt.querydesigner
- vdt.pane.diagram
- vdt.pane.grid
- vdt.dlgbox.querybuilder
- vdt.pane.sql
- vdt.pane.results
helpviewer_keywords:
- Query Designer [SQL Server], panes
- View Designer, panes
- Query Designer [SQL Server], components
- View Designer, components
ms.assetid: 12e4b5a5-b793-4b6c-a0e5-c450c49bf26f
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ec0aafb394d43fa55fa940ca5ce23cca798b3ef4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053202"
---
# <a name="query-and-view-designer-tools-visual-database-tools"></a>Outils du concepteur de requêtes et de vues (Visual Database Tools)
  Lors de la création d'une requête, d'une vue, d'une fonction inline ou d'une procédure stockée à une seule instruction, le concepteur que vous utilisez se compose de quatre volet : le volet Schéma, le volet Critères, le volet SQL et le volet Résultats.  
  
 ![Concepteur de requêtes](../../database-engine/media//vs-queryviewdsgpanes.gif "Concepteur de requêtes")  
  
-   Le volet Schéma affiche les tables ainsi que les autres objets table que vous interrogez. Chaque rectangle représente une table ou un objet table et affiche les colonnes de données disponibles. Les jointures sont indiquées par des traits reliant les rectangles. Pour plus d’informations, consultez [Volet Schéma &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
-   Le volet Critères contient un quadrillage similaire à celui d'une feuille de calcul, dans lequel vous pouvez spécifier des options, telles que les colonnes de données à afficher, les lignes à sélectionner, la façon de grouper les lignes, et ainsi de suite. Pour plus d’informations, consultez [Volet Critères &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md).  
  
-   Le volet SQL affiche l'instruction SQL de la requête ou de la vue. Vous pouvez modifier l'instruction SQL créée par le Concepteur ou entrer la vôtre. Cela s'avère particulièrement utile lorsque vous devez entrer des instructions SQL impossibles à créer avec les volets Schéma et Critères, telles que des requêtes Union. Pour plus d’informations, consultez [Volet SQL &#40;Visual Database Tools&#41;](sql-pane-visual-database-tools.md).  
  
-   Le volet Résultats montre une grille affichant les données extraites par la requête ou la vue. Dans le Concepteur de requêtes et de vues, le volet montre les résultats de la dernière requête SELECT exécutée. Pour modifier la base de données, vous pouvez changer des valeurs dans les cellules de la grille, ajouter des lignes ou en supprimer. Pour plus d’informations, consultez [Volet Résultats &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md).  
  
 Pour créer une requête ou une vue, utilisez un ou plusieurs de ces trois volets : pour spécifier une colonne à afficher, vous pouvez la choisir dans le volet Schéma, l'entrer dans le volet Critères ou l'inclure dans une instruction SQL dans le volet SQL.  
  
## <a name="displaying-and-hiding-panes"></a>Affichage et masquage des volets  
 Pour masquer ou afficher un volet, cliquez avec le bouton droit sur la surface de design, pointez sur **Volet**, puis cliquez sur le nom du volet. Si le Concepteur de requêtes et de vues est ouvert en mode Concepteur de requêtes, le volet **Résultats** n’est pas disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures de requêtes et les vues de conception &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Ouvrez le Concepteur de requêtes et vue &#40;Visual Database Tools&#41;](open-the-query-and-view-designer-visual-database-tools.md)   
 [Éditeur SQL &#40;Visual Database Tools&#41;](sql-editor-visual-database-tools.md)  
  
  