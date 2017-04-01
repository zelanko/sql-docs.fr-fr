---
title: "Afficher des valeurs en pourcentage dans un graphique &#224; secteurs (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
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
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 6
---
# Afficher des valeurs en pourcentage dans un graphique &#224; secteurs (G&#233;n&#233;rateur de rapports et SSRS)
  Par défaut, des catégories sont indiquées dans la légende pour identifier chaque valeur. Si vous avez créé des étiquettes de catégories pour le graphique à secteurs, vous avez la possibilité d'afficher des pourcentages dans la légende.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour afficher des valeurs en pourcentage sous forme d'étiquettes sur un graphique à secteurs  
  
1.  Ajoutez un graphique à secteurs à votre rapport. Pour plus d’informations, voir [Ajouter un graphique à un rapport (Générateur de rapports et SSRS)](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le secteur, puis sélectionnez **Afficher les étiquettes de données**. Les étiquettes de données doivent apparaître dans chaque secteur du graphique.  
  
3.  Dans l’aire de conception, cliquez avec le bouton droit sur les étiquettes, puis sélectionnez **Propriétés de l’étiquette de la série**. La boîte de dialogue **Propriétés de l'étiquette de la série** s'affiche.  
  
4.  Tapez **#PERCENT** pour l’option **Données de l’étiquette**.  
  
5.  (Facultatif) Pour indiquer le nombre de décimales affichées sur l’étiquette, tapez « #PERCENT{P*n*} », où *n* correspond au nombre de décimales à afficher. Par exemple, pour ne pas afficher de décimale, tapez « #PERCENT{P0} ».  
  
### Pour afficher des valeurs en pourcentage dans la légende d'un graphique à secteurs  
  
1.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique à secteurs, puis sélectionnez **Propriétés de la série**. La boîte de dialogue **Propriétés de la série** s’affiche.  
  
2.  Dans **Légende**, tapez **#PERCENT** pour la propriété **Texte de légende personnalisé**.  
  
## Voir aussi  
 [Graphiques à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Mise en forme de la légende sur un graphique (Générateur de rapports et SSRS)](../../reporting-services/report-design/formatting-the-legend-on-a-chart-report-builder-and-ssrs.md)   
 [Afficher des étiquettes de points de données à l’extérieur d’un graphique à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Regrouper des petits secteurs sur un graphique à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  