---
title: Modifier le texte d’un élément de légende (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e34f0a34030dab62a876a41043dc4c4f4c86f0c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106313"
---
# <a name="change-the-text-of-a-legend-item-report-builder-and-ssrs"></a>Modifier le texte d'un élément de légende (Générateur de rapports et SSRS)
  Lorsqu'un champ est placé dans la zone Valeurs du graphique, un élément de légende contenant le nom de ce champ est automatiquement généré. Chaque élément de légende est relié à une série individuelle sur le graphique, à l’exception des graphiques à base de formes, pour lesquels la légende est reliée à des points de données individuels et non à des séries individuelles.  
  
 Sur les graphiques à base de formes, vous pouvez modifier le texte d'un élément de légende pour afficher davantage d'informations sur des points de données individuels. Par exemple, si vous souhaitez afficher les valeurs des points de données sous forme de pourcentages dans la légende, vous pouvez utiliser un mot clé tel que `#PERCENT`). Vous pouvez ajouter des codes de format .NET Framework en plus des mots clés pour appliquer des formats de nombre et de date. Pour plus d’informations sur les mots clés, consultez [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
 ![Graphique pointu](../media/sharpchart.png "Graphique pointu")  
  
 Sur les graphiques qui ne sont pas à base de formes, vous pouvez modifier le texte d'un élément de légende. Par exemple, si votre nom de série est « Série1 », vous pouvez être amené à modifier le texte de manière à le rendre plus descriptif (« Ventes pour 2008 », par exemple).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a>Pour modifier le texte qui apparaît dans la légende sur un graphique à base de formes  
  
1.  Cliquez avec le bouton droit sur une série ou sur un champ de la zone **Valeurs** et sélectionnez **Propriétés de la série**.  
  
2.  Cliquez sur **Légende** et tapez un mot clé dans la zone **Texte de légende personnalisé** .  
  
 Le tableau suivant donne des exemples de mots clés spécifiques aux graphiques à utiliser avec la propriété **Texte de légende personnalisé** . Pour plus d’informations sur les mots clés, consultez [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
|Mot clé|Description|Exemple de texte apparaissant dans la légende|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|Affiche le pourcentage de la valeur totale à une décimale après la virgule.|85.0%|  
|`#VALY`|Affiche la valeur numérique réelle du champ de données.|17000|  
|`#VALY{C2}`|Affiche la valeur numérique réelle du champ de données sous forme de devise avec deux décimales après la virgule.|$17000.00|  
|`#AXISLABEL (#PERCENT{P0})`|Affiche la représentation textuelle du champ de catégorie, suivie du pourcentage affiché par chaque catégorie sur le graphique.|Michael Blythe (85 %)|  
  
> [!NOTE]  
>  Le mot clé #AXISLABEL ne peut être évalué qu’au moment de l’exécution quand aucun champ n’est spécifié dans la zone **Groupes de séries** .  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a>Pour modifier le texte qui apparaît dans la légende sur un graphique qui n'est pas à base de formes  
  
1.  Cliquez avec le bouton droit sur une série ou sur un champ de la zone **Valeurs** et sélectionnez **Propriétés de la série**.  
  
2.  Cliquez sur **Légende** et tapez une étiquette de légende dans la zone **Texte de légende personnalisé** . La série est actualisée en même temps que le texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme de la légende sur un graphique &#40;Générateur de rapports et SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [Mise en forme des couleurs des séries sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Masquer des éléments de légende sur le graphique &#40;Générateur de rapports et SSRS&#41;](chart-legend-hide-items-report-builder.md)  
  
  
