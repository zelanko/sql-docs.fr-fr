---
title: Graphiques en aires (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 245b236d-1d55-4744-b752-80bd133502aa
caps.latest.revision: 5
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 7e202fca2b7fbbf982ad1a28241f1ad4d6f985cd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039908"
---
# <a name="area-charts-report-builder-and-ssrs"></a>Graphiques en aires (Générateur de rapports et SSRS)
  Un graphique en aires affiche une série sous la forme d'un ensemble de points reliés par une courbe, la zone sous la courbe étant remplie. Pour plus d’informations sur la façon d’ajouter des données à un graphique en aires, consultez [graphiques &#40;le Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
 L'illustration suivante montre un exemple d'un graphique en aires empilées. Les données conviennent à une présentation en graphique en aires empilées car le graphique peut afficher des totaux pour toute la série ainsi que la contribution de chaque série au total.  
  
 ![Graphique en aires](../media/areachart.gif "Graphique en aires")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Variantes  
  
-   **Aires empilées**. Graphique en aires empilées où plusieurs séries sont empilées verticalement. Si votre graphique ne représente qu'une seule série, le graphique en aires empilées affichera la même chose qu'un graphique en aires.  
  
-   **Aires empilées %**. Graphique en aires où plusieurs séries sont empilées verticalement pour occuper l'intégralité de la zone de graphique. Si votre graphique ne représente qu'une seule série, le graphique en aires empilées affichera la même chose qu'un graphique en aires.  
  
-   **Aires lissées**. Graphique en aires où les points de données sont connectés par une ligne lissée au lieu d'une ligne normale. Utilisez un graphique en aires lissées au lieu d'un graphique en aires lorsque vous souhaitez afficher des tendances plutôt que les valeurs des points de données individuels.  
  
## <a name="data-considerations-for-area-charts"></a>Considérations relatives aux données pour les graphiques en aires  
  
-   Tout comme le graphique en courbes, un graphique en aires est un type de graphique qui affiche les données de façon contiguë. Pour cette raison, un graphique en aires est souvent utilisé pour représenter des données qui se produisent sur une période de temps continue.  
  
-   Un graphique en aires empilées pourcent est utile pour afficher des données proportionnelles qui se produisent dans le temps.  
  
-   Dans le cas d'une seule série, un graphique en aires empilées sera dessiné comme un graphique en aires.  
  
-   Dans un graphique en aires ordinaire, si les valeurs de plusieurs séries sont identiques, les aires peuvent se chevaucher, en masquant des valeurs de point de données importantes. Vous pouvez résoudre ce problème en changeant le type de graphique en un graphique en aires empilées, conçu pour afficher plusieurs séries sur un graphique en aires.  
  
-   Si votre graphique en aires empilées contient des intervalles, il est possible que votre dataset comprenne des valeurs vides, qui seront affichées sous la forme d'une section vide dans un graphique en aires empilées. Si votre dataset comprend des valeurs vides, pensez à insérer des points vides sur le graphique. L'ajout de points vides remplira les zones vides sur le graphique avec une couleur différente pour indiquer les valeurs null ou égales à zéro. Pour plus d’informations, consultez [ajouter des Points vides au graphique &#40;le Générateur de rapports et SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).  
  
-   Le comportement des types de graphiques en aires est similaire à celui des graphiques en courbes et des histogrammes. Si vous comparez plusieurs séries, pensez à utiliser un histogramme. Si vous analysez des tendances sur une période de temps, pensez à utiliser un graphique en courbes.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Types de graphiques &#40;Générateur de rapports et SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [Graphiques en courbes &#40;Générateur de rapports et SSRS&#41;](line-charts-report-builder-and-ssrs.md)   
 [Modifier un type de graphique &#40;Générateur de rapports et SSRS&#41;](change-a-chart-type-report-builder-and-ssrs.md)   
 [Les Points de données dans les graphiques vides et Null &#40;rapport Générateur et SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  