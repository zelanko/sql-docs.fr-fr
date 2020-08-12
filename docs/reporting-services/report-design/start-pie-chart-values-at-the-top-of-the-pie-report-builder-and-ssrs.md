---
title: Démarrer des valeurs de graphique à secteurs en haut du graphique à secteurs (Générateur de rapports) | Microsoft Docs
description: Découvrez comment démarrer des valeurs de graphique à secteurs en haut du graphique au lieu de les faire démarrer à 90 degrés à partir du haut par défaut.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: dfdd7600a08a78baa0b70f2048423f1632ebe2db
ms.sourcegitcommit: 5b7457c9d5302f84cc3baeaedeb515e8e69a8616
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83689436"
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
  
  
