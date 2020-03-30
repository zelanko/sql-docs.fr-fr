---
title: Démarrer des valeurs de graphique à secteurs en haut du graphique à secteurs (Générateur de rapports) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3f23163da5fc4b23a364646be607167e663187fd
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "77080900"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>Démarrer des valeurs de graphique à secteurs en haut du graphique à secteurs (Générateur de rapports et SSRS)
Par défaut, dans les graphiques à secteurs des rapports paginés de [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , la première valeur du dataset démarre à 90 degrés du haut du graphique à secteurs. 

![report-builder-pie-chart-start-at-90](../../reporting-services/media/report-builder-pie-chart-start-at-90.png)

*Les valeurs du graphique démarrent à 90 degrés.*

Vous pouvez préférer avoir la première valeur en haut. 

![report-builder-pie-chart-start-at-top](../../reporting-services/media/report-builder-pie-chart-start-at-top.png)

*Les valeurs du graphique commencent en haut du graphique.*
  
## <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>Pour démarrer le graphique à secteurs en haut  
  
1.  Cliquez sur les secteurs.  
  
2.  Si le volet **Propriétés** n'est pas ouvert, cliquez sur **Propriétés** sous l'onglet **Affichage**.  
  
3.  Dans le volet **Propriétés** , sous **Attributs personnalisés**, remplacez la valeur de **PieStartAngle** définie sur **0** par **270**.  
  
4.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 La première valeur démarre à présent en haut du graphique à secteurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Graphiques à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  
