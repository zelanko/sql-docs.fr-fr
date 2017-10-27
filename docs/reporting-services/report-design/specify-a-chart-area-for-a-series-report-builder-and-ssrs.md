---
title: "Spécifier une zone de graphique pour une série (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- "10157"
- sql13.rtp.rptdesigner.chartareaproperties.alignment.f1
ms.assetid: dc3c365b-c263-402a-bf6f-c2a7081db073
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d88358516e05214b230ec57b6243168ef9aac048
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="specify-a-chart-area-for-a-series-report-builder-and-ssrs"></a>Spécifier une zone de graphique pour une série (Générateur de rapports et SSRS)
  Dans les rapports paginés [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , le *graphique* est le conteneur de niveau supérieur qui inclut la bordure externe, le titre du graphique et la légende. Par défaut, le graphique contient une seule *zone de graphique*. La zone de graphique n'est pas visible à la surface du graphique, mais vous pouvez la considérer comme un conteneur qui comprend uniquement les étiquettes d'axe, le titre de l'axe et la zone de traçage d'une ou plusieurs série(s). L’illustration suivante montre l’utilisation de plusieurs zones de graphique dans un même graphique.  
  
 ![Affiche un diagramme d’une zone de graphique](../../reporting-services/report-design/media/chartareasdiagram.gif "montre le schéma d’une zone de graphique")  
  
 Par défaut, toutes les séries sont ajoutées à la zone de graphique par défaut. Lorsque vous utilisez des graphiques en aires, des histogrammes, des graphiques en courbes ou à nuages de points, vous pouvez afficher n'importe quelle combinaison de ces séries sur la même zone de graphique. Plusieurs séries dans une même zone de graphique réduit la lisibilité du graphique. Il est donc recommandé de séparer les différents types de graphique en différentes zones. L'utilisation de plusieurs zones de graphique améliore la lisibilité et facilite les comparaisons. Par exemple, les graphiques boursiers de type volume-prix présentent souvent des plages de valeurs différentes, mais des comparaisons peuvent être faites entre les données de prix et de volume sur une même période.  
  
 Une série de graphiques à barres, polaires ou à base de formes peut être combinée uniquement avec des graphiques de type identique dans une même zone de graphique. Si vous utilisez un graphique polaire ou à base de formes, pensez à utiliser une région de données de graphique distincte pour chaque champ que vous souhaitez afficher.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-associate-a-series-with-a-new-chart-area"></a>Pour associer une série à une nouvelle zone de graphique  
  
1.  Cliquez avec le bouton droit sur le graphique et sélectionnez **Ajouter une nouvelle zone graphique**. Une nouvelle zone de graphique vide apparaît sur le graphique.  
  
2.  Cliquez avec le bouton droit sur la série dans le graphique, ou sur une série ou un champ de données dans la zone appropriée du volet Données du graphique, puis cliquez sur **Propriétés de la série**.  
  
3.  Dans **Axes et zone de graphique**, sélectionnez la zone de graphique dans laquelle vous souhaitez afficher la série.  
  
4.  (Facultatif) Alignez les zones de graphique verticalement. Pour ce faire, cliquez avec le bouton droit sur le graphique et sélectionnez **Propriétés de la zone de graphique**. Dans **Alignement**, sélectionnez une autre autre zone de graphique avec laquelle vous souhaitez aligner la zone de graphique sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Plusieurs séries sur un graphique &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md)   
 [Mise en forme des Points de données sur un graphique &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Définir les couleurs d’un graphique à l’aide d’une Palette &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)   
 [Les graphiques polaires &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/polar-charts-report-builder-and-ssrs.md)   
 [Graphiques de la forme &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/shape-charts-report-builder-and-ssrs.md)   
 [Les graphiques en secteurs &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  

