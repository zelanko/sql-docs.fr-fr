---
title: "Spécifier une échelle logarithmique (Générateur de rapports et SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 57d0078658267adbfa5d7e02f742a61b9f7ae697
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a>Spécifier une échelle logarithmique (Générateur de rapports et SSRS)
  Si vos données sont proportionnelles d’un point de vue logarithmique, vous pouvez envisager d’utiliser une échelle logarithmique sur un graphique de rapport paginé [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] . Vous améliorerez ainsi l'apparence du graphique en facilitant la gestion des données. La plupart des échelles logarithmiques utilisent une base 10.  
  
 Cette fonctionnalité est uniquement disponible sur l'axe des ordonnées. L'axe des ordonnées est généralement l'axe vertical, ou axe des Y. Toutefois, dans les graphiques à barres, il s'agit de l'axe horizontal, ou axe des X.  
  
 Avec un axe logarithmique, toutes les autres propriétés concernant l'axe seront mises à l'échelle de façon logarithmique. Par exemple, si vous spécifiez une échelle logarithmique de base 10 sur votre axe, la définition d'un intervalle d'axe égal à 2 générera des intervalles de 10 à la puissance 2, soit 100. Cela signifie que vos valeurs d'axe indiqueront 1, 100, 10 000, au lieu du résultat par défaut 1, 10, 100, 1 000, 10 000.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-a-logarithmic-scale"></a>Pour spécifier une échelle logarithmique  
  
1.  Cliquez avec le bouton droit sur l’axe des ordonnées de votre graphique, puis cliquez sur **Propriétés de l’axe vertical**. La boîte de dialogue **Propriétés de l’axe vertical** s’affiche.  
  
2.  Dans **Options de l’axe**, sélectionnez **Utiliser l’échelle logarithmique**.  
  
3.  Dans la zone de texte **Base logarithmique** , tapez une valeur positive pour la base logarithmique. Si aucune valeur n'est spécifiée, la base logarithmique par défaut est 10.  
  
## <a name="see-also"></a> Voir aussi  
 [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Mettre en forme les étiquettes des axes en tant que dates ou devises &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Graphiques (Générateur de rapports et SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
