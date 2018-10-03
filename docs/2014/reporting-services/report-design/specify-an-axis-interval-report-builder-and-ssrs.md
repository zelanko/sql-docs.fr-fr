---
title: Spécifier un intervalle d’axe (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: ae46712d-a5bf-44c0-9929-e30ccc1e7e33
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 8b86ef40b0a796c1d340a1d7ccadcc68fcdbed74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48151939"
---
# <a name="specify-an-axis-interval-report-builder-and-ssrs"></a>Spécifier un intervalle d'axe (Générateur de rapports et SSRS)
  L'intervalle d'axe définit le nombre d'étiquettes et de graduations associées sur un axe. Sur l'axe des ordonnées, les intervalles de l'axe fournissent une mesure cohérente des points de données sur le graphique. Toutefois, sur l'axe des abscisses, cette fonctionnalité peut entraîner l'affichage des catégories sans étiquettes d'axe. Vous pouvez spécifier le nombre d’intervalles souhaité dans la propriété Intervalle de l’axe. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] calcule le nombre d'intervalles au moment de l'exécution en fonction des données contenues dans le jeu de résultats. Pour plus d’informations sur le calcul des intervalles de l’axe, consultez [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  
  
 Cette rubrique n'est pas applicable pour les valeurs de date ou d'heure sur l'axe des abscisses. Par défaut, `DateTime` valeurs apparaissent comme des jours. Pour spécifier un intervalle de date ou d'heure différent, tel qu'un mois ou intervalle de temps, vous devez mettre en forme les étiquettes de l'axe et configurer l'axe pour afficher des instances de types `DateTime` au lieu de types `String`. En outre, vous devez définir la propriété Intervalle. Pour plus d’informations, consultez [Mettre en forme les étiquettes des axes en tant que dates ou devises &#40;Générateur de rapports et SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md).  
  
 Cette rubrique ne s'applique pas aux graphiques à secteurs, en anneau, en entonnoir ni en pyramide, qui n'ont pas d'axes.  
  
> [!NOTE]  
>  L'axe des abscisses est généralement l'axe horizontal, ou axe des X. Toutefois, pour les graphiques à barres, l'axe des abscisses est l'axe vertical, ou axe des Y.  
  
 Un exemple de graphique spécifiant des intervalles d'axe différents est disponible sous la forme d'un exemple de rapport. Pour plus d'informations sur le téléchargement de cet exemple de rapport et d'autres rapports, consultez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Exemples de rapports du Générateur de rapports et du Concepteur de rapports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-show-all-category-labels-on-the-x-axis"></a>Pour afficher toutes les étiquettes de catégories sur l'axe des abscisses  
  
1.  Cliquez avec le bouton droit sur l'axe des abscisses, puis cliquez sur **Propriétés de l'axe**. La boîte de dialogue **Propriétés de l'axe** s'ouvre.  
  
2.  Dans **Options de l’axe**, affectez la valeur `Interval` à **1**. Chaque étiquette de groupe de catégories est affichée. Si vous souhaitez afficher une étiquette de groupe de catégories sur deux sur l'axe des abscisses, tapez **2**.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  Lorsqu'un intervalle d'axe est défini, tout l'étiquetage automatique est désactivé. Si vous spécifiez une valeur pour l'intervalle d'axe, vous pouvez rencontrer un comportement d'étiquetage imprévisible en fonction du nombre de catégories sur l'axe des abscisses.  
  
### <a name="to-enable-a-variable-interval-calculation-on-an-axis"></a>Pour activer un calcul d'intervalle variable sur un axe  
  
1.  Cliquez avec le bouton droit sur l'axe de graphique à modifier, puis cliquez sur **Propriétés de l'axe**. La boîte de dialogue **Propriétés de l'axe** s'ouvre.  
  
2.  Dans **Options de l’axe**, affectez la valeur `Interval` à **automatique**. Le graphique affiche le nombre optimal d'étiquettes de catégories qui peuvent s'ajuster le long de l'axe.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Mise en forme des Points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Trier des données dans une région de données &#40;Générateur de rapports et SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés de l’axe, Options de l’axe &#40;Générateur de rapports et SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)   
 [Spécifier une échelle logarithmique &#40;Générateur de rapports et SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md)   
 [Tracer des données sur un axe secondaire &#40;Générateur de rapports et SSRS&#41;](plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)  
  
  
