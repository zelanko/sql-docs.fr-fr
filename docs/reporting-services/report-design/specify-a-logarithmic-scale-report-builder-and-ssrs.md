---
title: Spécifier une échelle logarithmique (Générateur de rapports) | Microsoft Docs
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 80ddb9e21a3bd61cf9f994cce3d5722ae5fcf3f6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "77080930"
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
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Mettre en forme les étiquettes des axes en tant que dates ou devises &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Graphiques (Générateur de rapports et SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
