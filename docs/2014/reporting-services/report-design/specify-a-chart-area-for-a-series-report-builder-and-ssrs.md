---
title: Spécifier une zone de graphique pour une série (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10157"
- sql12.rtp.rptdesigner.chartareaproperties.alignment.f1
ms.assetid: dc3c365b-c263-402a-bf6f-c2a7081db073
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8578b33bb47a6bcf8c38ae091c4e959085c30b06
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59971245"
---
# <a name="specify-a-chart-area-for-a-series-report-builder-and-ssrs"></a>Spécifier une zone de graphique pour une série (Générateur de rapports et SSRS)
  Le graphique est le conteneur de niveau supérieur qui inclut la bordure externe, le titre du graphique et la légende. Par défaut, le graphique contient une zone de graphique par défaut. La zone de graphique n'est pas visible à la surface du graphique, mais vous pouvez la considérer comme un conteneur qui comprend uniquement les étiquettes d'axe, le titre de l'axe et la zone de traçage d'une ou plusieurs série(s). L'illustration suivante montre le concept de zones de graphique dans un unique graphique.  
  
 ![Affiche un diagramme d’une zone de graphique](../media/chartareasdiagram.gif "Affiche un diagramme d’une zone de graphique")  
  
 Par défaut, toutes les séries sont ajoutées à la zone de graphique par défaut. Lorsque vous utilisez des graphiques en aires, des histogrammes, des graphiques en courbes ou à nuages de points, vous pouvez afficher n'importe quelle combinaison de ces séries sur la même zone de graphique. Plusieurs séries dans une même zone de graphique réduit la lisibilité du graphique. Il est donc recommandé de séparer les différents types de graphique en différentes zones. L'utilisation de plusieurs zones de graphique améliore la lisibilité et facilite les comparaisons. Par exemple, les graphiques boursiers de type volume-prix présentent souvent des plages de valeurs différentes, mais des comparaisons peuvent être faites entre les données de prix et de volume sur une même période.  
  
 Une série de graphiques à barres, polaires ou à base de formes peut être combinée uniquement avec des graphiques de type identique dans une même zone de graphique. Si vous utilisez un graphique polaire ou à base de formes, pensez à utiliser une région de données de graphique distincte pour chaque champ que vous souhaitez afficher.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-series-with-a-new-chart-area"></a>Pour associer une série à une nouvelle zone de graphique  
  
1.  Cliquez avec le bouton droit sur le graphique et sélectionnez **Ajouter une nouvelle zone graphique**. Une nouvelle zone de graphique vide apparaît sur le graphique.  
  
2.  Cliquez avec le bouton droit sur la série dans le graphique, ou sur une série ou un champ de données dans la zone appropriée du volet Données du graphique, puis cliquez sur **Propriétés de la série**.  
  
3.  Dans **Axes et zone de graphique**, sélectionnez la zone de graphique dans laquelle vous souhaitez afficher la série.  
  
4.  (Facultatif) Alignez les zones de graphique verticalement. Pour ce faire, cliquez avec le bouton droit sur le graphique et sélectionnez **Propriétés de la zone de graphique**. Dans **Alignement**, sélectionnez une autre autre zone de graphique avec laquelle vous souhaitez aligner la zone de graphique sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Plusieurs séries sur un graphique &#40;Générateur de rapports et SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)   
 [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Définir les couleurs d’un graphique à l’aide d’une palette &#40;Générateur de rapports et SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)   
 [Graphiques polaires &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Graphiques à base de formes &#40;Générateur de rapports et SSRS&#41;](shape-charts-report-builder-and-ssrs.md)   
 [Graphiques à secteurs &#40;Générateur de rapports et SSRS&#41;](pie-charts-report-builder-and-ssrs.md)  
  
  
