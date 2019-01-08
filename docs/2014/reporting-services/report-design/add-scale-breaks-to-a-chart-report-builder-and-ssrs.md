---
title: Ajouter des séparations d’échelle à un graphique (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 85c1849cb2fb5fdfda78a147880d9c39003b8257
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358811"
---
# <a name="add-scale-breaks-to-a-chart-report-builder-and-ssrs"></a>Ajouter des séparations d'échelle à un graphique (Générateur de rapports et SSRS)
  Une séparation d'échelle est une ligne dessinée sur la zone de traçage d'un graphique pour indiquer une rupture dans la continuité entre les valeurs haute et basse d'un axe des ordonnées (en général, l'axe vertical ou axe des Y). Utilisez une séparation d'échelle pour afficher deux plages distinctes dans la même zone de graphique.  
  
 ![Graphique avec séparateur d’échelle](../media/rs-multipledatarangeschart-scalebreak.gif "Graphique avec séparateur d’échelle")  
  
> [!NOTE]  
>  Vous ne pouvez pas spécifier où placer une séparation d'échelle sur votre graphique. Le graphique utilise ses propres calculs en fonction des valeurs de votre dataset pour déterminer si l'écart entre les différentes plages de données est suffisant pour dessiner une séparation d'échelle sur l'axe des ordonnées (axe Y) au moment de l'exécution.  
  
 Un exemple de graphique avec séparations d’échelle est disponible sous forme d’exemple de rapport. Pour plus d'informations sur le téléchargement de cet exemple de rapport et d'autres rapports, consultez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Exemples de rapports du Générateur de rapports et du Concepteur de rapports](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-scale-breaks-on-the-chart"></a>Pour activer les séparations d'échelle sur le graphique  
  
1.  Cliquez avec le bouton droit sur l’axe vertical, puis cliquez sur **Propriétés de l’axe**. La boîte de dialogue **Propriétés de l’axe vertical** s’ouvre.  
  
2.  Cochez la case **Activer les séparateurs d’échelle** .  
  
### <a name="to-change-the-style-of-the-scale-break"></a>Pour modifier le style de la séparation d'échelle  
  
1.  Ouvrez le volet Propriétés.  
  
2.  Dans l'aire de conception, cliquez avec le bouton droit sur l'axe Y du graphique. Les propriétés de l'objet de l'axe Y (nommé Axe de graphique par défaut) sont affichées dans le volet Propriétés.  
  
3.  Dans la section **Échelle** , développez la propriété ScaleBreakStyle.  
  
4.  Modifier les valeurs de la propriété ScaleBreakStyle, telles que BreakLineType et Spacing. Pour plus d’informations sur les propriétés des séparations d’échelle, consultez, [Affichage d’une série avec plusieurs plages de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés de l’axe, Options de l’axe &#40;Générateur de rapports et SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)  
  
  
