---
title: Regrouper des petits secteurs sur un graphique à secteurs (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 517f5c5dddd809ee71037a95d04109a005968132
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106221"
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a>Regrouper des petits secteurs sur un graphique à secteurs (Générateur de rapports et SSRS)
  Lorsqu'un graphique à secteurs présente de nombreux points de données, son aspect devient rapidement confus. Pour résoudre ce problème, vous pouvez afficher toutes les données inférieures à une certaine valeur dans un même secteur du graphique à secteurs.  
  
 Pour regrouper plusieurs petits secteurs en un, vous devez en premier lieu décider si le seuil de regroupement des petits secteurs est exprimé sous forme de pourcentage du graphique à secteurs ou sous forme de valeur fixe. Ensuite, définissez les propriétés CollectedThreshold et CollectedThresholdUsePercent. Définissez la propriété soit sur le pourcentage du graphique en-dessous duquel une valeur doit être regroupée, soit sur la valeur de données de seuil réel pour le regroupement. Affectez à la propriété `True` CollectedThresholdUsePercent la valeur pour utiliser `False` un pourcentage ou pour utiliser une valeur réelle.  
  
 Vous pouvez également regrouper des petits secteurs en un deuxième graphique à secteurs appelé à partir d'un secteur regroupé du premier graphique à secteurs. Le deuxième graphique à secteurs est alors tracé à droite du graphique à secteurs d'origine.  
  
 Le regroupement de plusieurs secteurs en un n'est pas possible pour les graphiques en entonnoir ou en pyramide.  
  
 Un exemple de ce graphique est disponible sous forme d'exemple de rapport. Pour plus d’informations sur le téléchargement de cet exemple de rapport [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]et d’autres, consultez [Générateur de rapports et concepteur de rapports des exemples de rapports](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
### <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a>Pour regrouper plusieurs petits secteurs en un sur un graphique à secteurs  
  
1.  Ouvrez le volet Propriétés.  
  
2.  Dans l'aire de conception, cliquez sur un secteur du graphique. Les propriétés de la série sont affichées dans le volet Propriétés.  
  
3.  Dans la section **Général** , développez le nœud **CustomAttributes** .  
  
4.  Définissez la propriété CollectedStyle sur **SingleSlice**.  
  
5.  Définissez la valeur de seuil de regroupement et le type de seuil. Vous trouverez ci-dessous quelques manières parmi les plus courantes de définir des seuils de regroupement.  
  
    -   **Par pourcentage.** Par exemple, pour regrouper en un secteur les secteurs de votre graphique inférieurs à 10 %, procédez comme suit :  
  
         Affectez à `True`la propriété CollectedThresholdUsePercent la valeur.  
  
         Définissez la propriété CollectedThreshold sur **10**.  
  
        > [!NOTE]  
        >  Si vous définissez CollectedStyle sur **valeur SingleSlice**, CollectedThreshold sur une valeur supérieure à **100**, et CollectedThresholdUsePercent est `True`, le graphique lèvera une exception, car il ne peut pas calculer un pourcentage. Pour résoudre ce problème, définissez la propriété CollectedThreshold sur une valeur inférieure à **100**.  
  
    -   **Par valeur des données.** Par exemple, pour regrouper en un secteur les secteurs de votre graphique inférieurs à 5000, procédez comme suit :  
  
         Affectez à `False`la propriété CollectedThresholdUsePercent la valeur.  
  
         Définissez la propriété CollectedThreshold sur **5000**.  
  
6.  Définissez la propriété CollectedLabel sur une chaîne représentant l’étiquette de texte à afficher dans le secteur regroupé.  
  
7.  (Facultatif) Définissez les propriétés CollectedSliceExploded, CollectedColor, CollectedLegendText et CollectedToolTip. Ces propriétés modifient l'apparence, la couleur, le texte de l'étiquette, le texte de la légende et l'aspect des info-bulles du secteur obtenu.  
  
### <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a>Pour regrouper des petits secteurs dans un deuxième graphique à secteurs secondaire  
  
1.  Suivez les étapes 1 à 3 ci-dessus.  
  
2.  Définissez la propriété CollectedStyle sur **CollectedPie**.  
  
3.  Définissez la propriété CollectedThresholdproperty sur une valeur représentant le seuil de regroupement des petits secteurs en un seul secteur. Lorsque la propriété CollectedStyle est définie sur **CollectedPie**, CollectedThresholdUsePercentproperty a toujours la valeur `True`, et le seuil collecté est toujours mesuré en pourcentage.  
  
4.  (Facultatif) Définissez les propriétés CollectedColor, CollectedLabel, CollectedLegendText et CollectedToolTip. Toutes les autres propriétés nommées « Collected » ne s'appliquent pas au regroupement de secteurs.  
  
> [!NOTE]  
>  Le graphique à secteurs secondaire étant calculé selon les petits secteurs, il s'affiche uniquement sous forme d'aperçu. Il n'apparaît pas dans l'aire de conception.  
  
> [!NOTE]  
>  Vous ne pouvez pas mettre en forme le graphique à secteurs secondaire. C'est pourquoi il est fortement recommandé de privilégier la première approche pour le regroupement de secteurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques à secteurs &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Afficher des étiquettes de points de données à l’extérieur d’un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Afficher des valeurs en pourcentage sur un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)   
 [Ajouter des effets 3D à un graphique &#40;Générateur de rapports et SSRS&#41;](chart-effects-add-3d-effects-report-builder.md)  
  
  
