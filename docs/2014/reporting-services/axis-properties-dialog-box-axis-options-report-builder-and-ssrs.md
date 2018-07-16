---
title: Boîte de dialogue Propriétés de l’axe, Options de l’axe (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.axisproperties.axisoptions.f1
- "10138"
ms.assetid: b276e210-7a12-48ae-971b-7dabae51df11
caps.latest.revision: 10
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c2b769fd686ba2bd32611b073cfe08a71e224d89
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315449"
---
# <a name="axis-properties-dialog-box-axis-options-report-builder-and-ssrs"></a>Boîte de dialogue Propriétés de l'axe, Options de l'axe (Générateur de rapports et SSRS)
  Sélectionnez **Options de l’axe** sur le **Horizontal** ou **propriétés de l’axe vertical** boîte de dialogue pour définir l’apparence de l’axe spécifié du graphique. Dans les versions précédentes de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], le graphique affichait par défaut toutes les étiquettes sur l'axe des abscisses. En revanche, dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008, le graphique ignore les étiquettes pour produire une image plus lisible et éviter les collisions d'étiquette. Pour plus d’informations, consultez [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Options  
 **Activer les séparations d’échelle**  
 Sélectionnez cette option pour permettre au graphique de dessiner un séparateur d'échelle lorsque cela est nécessaire. Lorsque cette option est activée, le graphique calculera automatiquement si la différence est suffisante entre les points hauts et bas du dataset pour dessiner un séparateur d'échelle.  
  
 **Inverser la direction**  
 Sélectionnez cette option pour inverser le sens du graphique. Par exemple, par défaut, un histogramme affiche l'axe des Y à gauche du graphique, et les catégories de gauche à droite. Lorsque cette option est sélectionnée, l'histogramme affiche l'axe des Y à droite du graphique, et les catégories de droite à gauche.  
  
 **Utiliser la couleur d’entrelacement**  
 Sélectionnez cette option pour ajouter des franges au graphique, puis sélectionnez une couleur ou tapez une expression. Les franges sont des bandes ombrées sur la zone de graphique qui affichent une alternance de zones claires et sombres entre les lignes du quadrillage. Ces franges sont utiles pour mettre en surbrillance les séquencés répétées sur un axe.  
  
 **Toujours inclure le zéro**  
 Sélectionnez cette option pour toujours inclure le zéro sur l'échelle d'axe. Si cette option n'est pas activée, le graphique n'indiquera pas la valeur zéro sur l'axe. L'indication des valeurs zéro est utile lorsque le dataset comprend des valeurs négatives ou égales à zéro.  
  
 **Axe scalaire**  
 Sélectionnez cette option pour afficher un ensemble de valeurs d'axe sur une échelle continue. Par exemple, si le dataset contient des données pour janvier, mars et novembre, un axe non scalaire affiche uniquement ces mois, alors qu'un axe scalaire affiche tous les mois de l'année.  
  
 **Utiliser l’échelle logarithmique**  
 Sélectionnez cette option pour indiquer que l'échelle de l'axe est logarithmique. Cette option est uniquement disponible sur l'axe des Y si l'axe contient des valeurs numériques positives.  
  
 Dans la zone, tapez la base logarithmique à utiliser lorsque l'axe est défini pour utiliser une échelle logarithmique. Par défaut, le graphique utilise une base 10 pour l'échelle logarithmique d'un axe. Cette option est uniquement disponible sur l'axe des Y si l'axe est numérique.  
  
 **Minimum**  
 Tapez une expression ou une valeur pour la valeur minimale de l'axe des x. En l'absence d'indication, la valeur minimale est déterminée par les données retournées par le dataset.  
  
 **Maximum**  
 Tapez une expression ou une valeur pour la valeur maximale de l'axe des x. En l'absence d'indication, la valeur maximale est déterminée par les données retournées par le dataset.  
  
 **Intervalle**  
 Tapez une expression ou une valeur pour l'intervalle entre les étiquettes d'axe. Par exemple, tapez 1 pour afficher chaque étiquette de catégorie sur l'axe. Tapez 2 pour afficher toutes les autres étiquettes de catégorie. Si ce paramètre n'est pas spécifié, les étiquettes sont calculées automatiquement à partir des valeurs du dataset.  
  
 **Type d’intervalle**  
 Tapez une expression ou une valeur pour le type d'intervalle de l'intervalle spécifié. Par exemple, pour définir un intervalle de deux jours, spécifiez **2** comme intervalle et choisissez **Jours** comme type d’intervalle.  
  
 **Marges latérales**  
 Tapez une expression ou sélectionnez une valeur pour ajouter ou supprimer une marge entre les éléments de graphique et les côtés du graphique. Si cette option est définie sur **Auto**, des marges latérales sont ajoutées.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](report-design/charts-report-builder-and-ssrs.md)   
 [Mise en forme des couleurs des séries sur un graphique &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Spécifier un intervalle d’axe &#40;Générateur de rapports et SSRS&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md)   
 [Mettre en forme les étiquettes des axes en tant que dates ou devises &#40;Générateur de rapports et SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Tracer des données sur un axe secondaire &#40;Générateur de rapports et SSRS&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)   
 [Graphiques sparkline et barres de données &#40;Générateur de rapports et SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)   
 [Ajouter ou supprimer des marges dans un graphique &#40;Générateur de rapports et SSRS&#41;](report-design/add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)  
  
  
