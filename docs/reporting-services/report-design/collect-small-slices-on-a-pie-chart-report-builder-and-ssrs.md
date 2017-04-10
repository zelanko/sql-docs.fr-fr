---
title: "Regrouper des petits secteurs sur un graphique &#224; secteurs (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
caps.latest.revision: 10
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Regrouper des petits secteurs sur un graphique &#224; secteurs (G&#233;n&#233;rateur de rapports et SSRS)
  Lorsqu'un graphique à secteurs présente de nombreux points de données, son aspect devient rapidement confus. Pour résoudre ce problème, vous pouvez afficher toutes les données inférieures à une certaine valeur dans un même secteur du graphique à secteurs.  
  
 Pour regrouper plusieurs petits secteurs en un, vous devez en premier lieu décider si le seuil de regroupement des petits secteurs est exprimé sous forme de pourcentage du graphique à secteurs ou sous forme de valeur fixe. Ensuite, définissez les propriétés CollectedThreshold et CollectedThresholdUsePercent. Définissez la propriété soit sur le pourcentage du graphique en-dessous duquel une valeur doit être regroupée, soit sur la valeur de données de seuil réel pour le regroupement. Définissez la propriété CollectedThresholdUsePercent sur **True** pour utiliser un pourcentage ou sur **False** pour utiliser une valeur réelle.  
  
 Vous pouvez également regrouper des petits secteurs en un deuxième graphique à secteurs appelé à partir d'un secteur regroupé du premier graphique à secteurs. Le deuxième graphique à secteurs est alors tracé à droite du graphique à secteurs d'origine.  
  
 Le regroupement de plusieurs secteurs en un n'est pas possible pour les graphiques en entonnoir ou en pyramide.  
  
 Un exemple de ce graphique est disponible sous forme d'exemple de rapport. Pour plus d'informations sur le téléchargement de cet exemple de rapport et d'autres rapports, consultez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Exemples de rapports du Générateur de rapports et du Concepteur de rapports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
### Pour regrouper plusieurs petits secteurs en un sur un graphique à secteurs  
  
1.  Ouvrez le volet Propriétés.  
  
2.  Dans l'aire de conception, cliquez sur un secteur du graphique. Les propriétés de la série sont affichées dans le volet Propriétés.  
  
3.  Dans la section **Général** , développez le nœud **CustomAttributes** .  
  
4.  Définissez la propriété CollectedStyle sur **SingleSlice**.  
  
5.  Définissez la valeur de seuil de regroupement et le type de seuil. Vous trouverez ci-dessous quelques manières parmi les plus courantes de définir des seuils de regroupement.  
  
    -   **Par pourcentage.** Par exemple, pour regrouper en un secteur les secteurs de votre graphique inférieurs à 10 %, procédez comme suit :  
  
         Définissez la propriété CollectedThresholdUsePercent sur **True**.  
  
         Définissez la propriété CollectedThreshold sur **10**.  
  
        > [!NOTE]  
        >  Si vous définissez la propriété CollectedStyle sur **SingleSlice**, la propriété CollectedThreshold sur une valeur supérieure à **100**, et la propriété CollectedThresholdUsePercent sur **True**, le graphique lève une exception, car il ne peut pas calculer de pourcentage. Pour résoudre ce problème, définissez la propriété CollectedThreshold sur une valeur inférieure à **100**.  
  
    -   **Par valeur des données.** Par exemple, pour regrouper en un secteur les secteurs de votre graphique inférieurs à 5000, procédez comme suit :  
  
         Définissez la propriété CollectedThresholdUsePercent sur **False**.  
  
         Définissez la propriété CollectedThreshold sur **5000**.  
  
6.  Définissez la propriété CollectedLabel sur une chaîne représentant l’étiquette de texte à afficher dans le secteur regroupé.  
  
7.  (Facultatif) Définissez les propriétés CollectedSliceExploded, CollectedColor, CollectedLegendText et CollectedToolTip. Ces propriétés modifient l'apparence, la couleur, le texte de l'étiquette, le texte de la légende et l'aspect des info-bulles du secteur obtenu.  
  
### Pour regrouper des petits secteurs dans un deuxième graphique à secteurs secondaire  
  
1.  Suivez les étapes 1 à 3 ci-dessus.  
  
2.  Définissez la propriété CollectedStyle sur **CollectedPie**.  
  
3.  Définissez la propriété CollectedThresholdproperty sur une valeur représentant le seuil de regroupement des petits secteurs en un seul secteur. Lorsque la propriété CollectedStyle est définie sur **CollectedPie**, la propriété CollectedThresholdUsePercentproperty est toujours définie sur **True**, et le seuil de regroupement est toujours exprimé en pourcentage.  
  
4.  (Facultatif) Définissez les propriétés CollectedColor, CollectedLabel, CollectedLegendText et CollectedToolTip. Toutes les autres propriétés nommées « Collected » ne s'appliquent pas au regroupement de secteurs.  
  
> [!NOTE]  
>  Le graphique à secteurs secondaire étant calculé selon les petits secteurs, il s'affiche uniquement sous forme d'aperçu. Il n'apparaît pas dans l'aire de conception.  
  
> [!NOTE]  
>  Vous ne pouvez pas mettre en forme le graphique à secteurs secondaire. C'est pourquoi il est fortement recommandé de privilégier la première approche pour le regroupement de secteurs.  
  
## Voir aussi  
 [Graphiques à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Mise en forme des points de données sur un graphique (Générateur de rapports et SSRS)](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Afficher des étiquettes de points de données à l’extérieur d’un graphique à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Afficher des valeurs en pourcentage dans un graphique à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)   
 [Ajouter des effets 3D à un graphique (Générateur de rapports et SSRS)](../../reporting-services/report-design/add-3d-effects-to-a-chart-report-builder-and-ssrs.md)  
  
  