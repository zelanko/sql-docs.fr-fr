---
title: Spécifier une échelle logarithmique (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
caps.latest.revision: 5
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5e40a78e8c0220c671f4bfa7157fb0f233ff8714
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153871"
---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a>Spécifier une échelle logarithmique (Générateur de rapports et SSRS)
  Si vos données sont proportionnelles d'un point de vue logarithmique, vous pouvez envisager d'utiliser une échelle logarithmique sur le graphique. Vous améliorerez ainsi l'apparence du graphique en facilitant la gestion des données. La plupart des échelles logarithmiques utilisent une base 10.  
  
 Cette fonctionnalité est uniquement disponible sur l'axe des ordonnées. L'axe des ordonnées est généralement l'axe vertical, ou axe des Y. Toutefois, dans les graphiques à barres, il s'agit de l'axe horizontal, ou axe des X.  
  
 Avec un axe logarithmique, toutes les autres propriétés concernant l'axe seront mises à l'échelle de façon logarithmique. Par exemple, si vous spécifiez une échelle logarithmique de base 10 sur votre axe, la définition d'un intervalle d'axe égal à 2 générera des intervalles de 10 à la puissance 2, soit 100. Cela signifie que vos valeurs d'axe indiqueront 1, 100, 10 000, au lieu du résultat par défaut 1, 10, 100, 1 000, 10 000.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-logarithmic-scale"></a>Pour spécifier une échelle logarithmique  
  
1.  Cliquez avec le bouton droit sur l’axe des ordonnées de votre graphique, puis cliquez sur **Propriétés de l’axe vertical**. La boîte de dialogue **Propriétés de l’axe vertical** s’affiche.  
  
2.  Dans **Options de l’axe**, sélectionnez **Utiliser l’échelle logarithmique**.  
  
3.  Dans la zone de texte **Base logarithmique** , tapez une valeur positive pour la base logarithmique. Si aucune valeur n'est spécifiée, la base logarithmique par défaut est 10.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Mettre en forme les étiquettes des axes en tant que dates ou devises &#40;Générateur de rapports et SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Graphiques &#40;rapport Générateur et SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  