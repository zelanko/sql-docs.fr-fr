---
title: Mise en forme d’un graphique (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10214"
- sql12.rtp.rptdesigner.calculatedseriesproperties.fill.f1
- sql12.rtp.rptdesigner.serieslabelproperties.fill.f1
- sql12.rtp.rptdesigner.legendproperties.fill.f1
- "10149"
- sql12.rtp.rptdesigner.seriesproperties.shadow.f1
- sql12.rtp.rptdesigner.seriesproperties.markers.f1
- "10255"
- sql12.rtp.rptdesigner.charttitleproperties.fill.f1
- "10154"
- "10170"
- "10173"
- sql12.rtp.rptdesigner.seriesproperties.fill.f1
- "10169"
- "10158"
- sql12.rtp.rptdesigner.chartareaproperties.fill.f1
- sql12.rtp.rptdesigner.charttitleproperties.shadow.f1
- "10246"
- "10150"
- sql12.rtp.rptdesigner.calculatedseriesproperties.borders.f1
- sql12.rtp.rptdesigner.chartproperties.fill.f1
- "10159"
- sql12.rtp.rptdesigner.majorgridlineproperties.gridlineoptions.f1
- "10160"
- sql12.rtp.rptdesigner.serieslabelproperties.font.f1
- "10182"
- "10163"
- "10164"
- "10253"
- "10216"
- "10171"
- "10257"
- sql12.rtp.rptdesigner.chartareaproperties.border.f1
- sql12.rtp.rptdesigner.calculatedseriesproperties.shadow.f1
- sql12.rtp.rptdesigner.chartproperties.border.f1
- sql12.rtp.rptdesigner.minorgridlineproperties.gridlineoptions.f1
- sql12.rtp.rptdesigner.chartareaproperties.shadow.f1
- sql12.rtp.rptdesigner.charttitleproperties.borders.f1
- sql12.rtp.rptdesigner.charttitleproperties.font.f1
- "10247"
ms.assetid: d3984300-c766-42f8-b7c4-863123d67c99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af164d4db9b6439f0634d113652b95939827b0f5
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66105857"
---
# <a name="formatting-a-chart-report-builder-and-ssrs"></a>Mise en forme d'un graphique (Générateur de rapports et SSRS)
  Après avoir défini les données et l'aspect de votre graphique, vous pouvez ajouter une mise en forme pour améliorer l'apparence globale et mettre en évidence les principaux points de données. Les options de mise en forme les plus courantes peuvent être modifiées dans la boîte de dialogue Propriétés qui apparaît lorsque vous cliquez avec le bouton droit sur un élément de graphique pour afficher son menu contextuel. Chaque élément de graphique possède sa propre boîte de dialogue. Pour plus d’informations sur les éléments des graphiques, consultez [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
 Toutes les propriétés qui sont en rapport avec le graphique figurent dans le volet Propriétés, mais un grand nombre de ces propriétés peuvent également être définies dans une boîte de dialogue. Si vous mettez en forme la série, vous pouvez spécifier des propriétés spécifiques à la série en utilisant des attributs personnalisés, qui se trouvent uniquement dans la catégorie de propriétés **CustomAttributes** , dans le volet Propriétés.  
  
 Pour mettre en forme efficacement le graphique en un minimum d'étapes, modifiez le style de bordure, la palette et style de dessin par défaut. Ces trois fonctionnalités produisent la modification la plus visible sur le graphique. Les styles de dessin s'appliquent uniquement aux histogrammes, graphiques à barres, graphiques en anneau et graphiques à secteurs.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mise en forme des couleurs des séries sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)  
 Explique comment les couleurs sont définies à l'aide d'une palette, comment vous pouvez définir votre propre palette de couleurs et comment définir des couleurs selon une expression.  
  
 [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)  
 Explique comment afficher un quadrillage, des graduations et des titres, et comment mettre en forme des nombres et des dates sur l'échelle des axes.  
  
 [Mise en forme de la légende sur un graphique &#40;Générateur de rapports et SSRS&#41;](chart-legend-formatting-report-builder.md)  
 Explique comment reclasser et mettre en forme des éléments dans la légende de graphique.  
  
 [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
 Explique comment placer des étiquettes de points de données et mettre en forme des marqueurs de points de données pour chaque série sur le graphique.  
  
 [Effets 3D, de biseau et autres dans un graphique &#40;Générateur de rapports et SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md)  
 Décrit différents effets 3D que vous pouvez appliquer à un graphique.  
  
 [Ajouter un cadre de bordure à un graphique &#40;Générateur de rapports et SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)  
 Explique comment ajouter un cadre de bordure à un graphique.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Ajouter un cadre de bordure à un graphique &#40;Générateur de rapports et SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)   
 [Définir les couleurs d’un graphique à l’aide d’une palette &#40;Générateur de rapports et SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)   
 [Ajouter des styles de biseau, de relief et de texture à un graphique &#40;Générateur de rapports et SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
