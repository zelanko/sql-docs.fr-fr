---
title: Tracer des données sur un axe secondaire (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e52bfb513d27225a6ae13593d2e6a196447c3d0d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63215674"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a>Tracer des données sur un axe secondaire (Générateur de rapports et SSRS)
  Le graphique a deux types d'axes : principal et secondaire. L'axe secondaire est utile lors de la comparaison de deux jeux de valeurs avec deux plages de données distinctes qui partagent une catégorie commune.  
  
 Par exemple, supposons que vous avez un graphique qui calcule vos revenus et. Impôts pour l’année 2008. Dans ce cas, la période 2008 est commune aux deux jeux de valeurs. Toutefois, lorsque les deux séries sont tracées sur le même axe des Y, nous ne pouvons pas établir de comparaison utile, car l'échelle de l'axe des Y est optimisée pour les plus grandes valeurs du dataset. Si nous affichons les revenus sur l'axe principal et les impôts sur l'axe secondaire, nous pouvons afficher chaque série sur son propre axe des Y avec sa propre échelle de valeurs. Les séries partagent encore un axe des abscisses commun.  
  
 Dans les cas où plus de deux séries doivent être comparées, envisagez une approche différente pour comparer et afficher plusieurs séries dans un graphique. Pour plus d’informations, consultez [Plusieurs séries sur un graphique &#40;Générateur de rapports et SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
 Un exemple de ce graphique est disponible sous forme d'exemple de rapport. Pour plus d'informations sur le téléchargement de cet exemple de rapport et d'autres rapports, consultez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Exemples de rapports du Générateur de rapports et du Concepteur de rapports](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a>Pour tracer une série sur l'axe secondaire  
  
1.  Cliquez avec le bouton droit sur la série dans le graphique ou sur un champ dans la zone **Valeurs** que vous souhaitez afficher sur l’axe secondaire, puis cliquez sur **Propriétés de la série**. La boîte de dialogue **Propriétés de la série** s'affiche.  
  
2.  Cliquez sur **Axes et zone de graphique**, et sélectionnez l'axe secondaire que vous voulez activer, l'axe des ordonnées ou l'axe des abscisses.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Spécifier un intervalle d’axe &#40;Générateur de rapports et SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
