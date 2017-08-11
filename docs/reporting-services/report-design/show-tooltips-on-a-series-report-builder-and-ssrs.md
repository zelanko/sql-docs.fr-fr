---
title: "Afficher les info-bulles dans une série (Générateur de rapports et SSRS) | Documents Microsoft"
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
ms.assetid: 4c9606ff-e1c3-4cf7-a4e7-bb16f1a9e8ab
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5e963b234c5c3babb4dd2302afca2ca06ac249b1
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="show-tooltips-on-a-series-report-builder-and-ssrs"></a>Afficher des info-bulles dans une série (Générateur de rapports et SSRS)
  Vous pouvez ajouter une info-bulle à chaque point de données sur la série d’un graphique pour afficher des informations en rapport avec le point de données, par exemple le nom du groupe, la valeur du point de données ou le pourcentage du point de données par rapport au total de la série. Quand les utilisateurs placent le pointeur sur le point de données dans un rapport paginé rendu, ils voient ces informations.  
  
 Vous ne pouvez pas ajouter d'info-bulle à une série calculée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-a-tooltip-on-each-data-point"></a>Pour spécifier une info-bulle sur chaque point de données  
  
1.  Cliquez avec le bouton droit sur la série ou sur le champ de la zone **Valeurs** et cliquez sur **Propriétés de la série**.  
  
2.  Cliquez sur **Données de la série** puis, pour la propriété **ToolTip** , tapez une chaîne ou une expression. Vous pouvez utiliser n'importe quel mot clé spécifique au graphique pour représenter un autre élément sur le graphique. Pour plus d’informations, consultez [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Modifier le texte d’un élément de légende &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/chart-legend-change-item-text-report-builder.md)   
 [Mise en forme des couleurs des séries sur un graphique &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Ajouter une Action d’extraction sur un rapport &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
