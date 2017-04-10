---
title: "Afficher des &#233;tiquettes de points de donn&#233;es &#224; l&#39;ext&#233;rieur d&#39;un graphique &#224; secteurs (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
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
ms.assetid: 959b7574-cf43-470b-b592-4944d8a9948f
caps.latest.revision: 6
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 6
---
# Afficher des &#233;tiquettes de points de donn&#233;es &#224; l&#39;ext&#233;rieur d&#39;un graphique &#224; secteurs (G&#233;n&#233;rateur de rapports et SSRS)
  Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], l'étiquetage de graphiques à secteurs est optimisé pour afficher des étiquettes uniquement sur plusieurs tranches de données. Les étiquettes peuvent se chevaucher si le graphique à secteurs contient trop de secteurs. Une solution consiste à afficher les étiquettes à l'extérieur du graphique à secteurs, ce qui peut libérer de l'espace pour de plus longues étiquettes de données. Si les étiquettes continuent de se chevaucher, vous pouvez créer davantage d'espace pour elles en activant l'affichage 3D. Le diamètre du graphique à secteurs est ainsi réduit, ce qui libère de l'espace autour du graphique.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour afficher des étiquettes de points de données à l'intérieur d'un graphique à secteurs  
  
1.  Ajoutez un graphique à secteurs à votre rapport. Pour plus d’informations, consultez [Ajouter un graphique à un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  Sur l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
### Pour afficher des étiquettes de points de données à l'extérieur d'un graphique à secteurs  
  
1.  Créez un graphique à secteurs et affichez les étiquettes de données.  
  
2.  Ouvrez le volet Propriétés.  
  
3.  Dans l’aire de conception, cliquez sur le graphique à secteurs lui-même pour afficher les propriétés de **Catégorie** dans le volet Propriétés.  
  
4.  Développez le nœud **CustomAttributes** . Une liste des attributs du graphique à secteurs s'affiche.  
  
5.  Affectez à la propriété **PieLabelStyle** la valeur **Extérieur**.  
  
6.  Affectez à la propriété **PieLineColor** la valeur **Noir**. La propriété PieLineColor définit les lignes de légende de chaque étiquette de point de données.  
  
### Pour empêcher les étiquettes qui se chevauchent de s'afficher à l'extérieur d'un graphique à secteurs  
  
1.  Créez un graphique à secteurs avec des étiquettes externes.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit à l’extérieur du graphique à secteurs, mais à l’intérieur des bordures du graphique, puis sélectionnez **Propriétés de la zone de graphique**. La boîte de dialogue **Propriétés de la zone de graphique** s’affiche.  
  
3.  Sous l’onglet **Options 3D**, sélectionnez **Afficher en 3D**.  
  
4.  Si vous souhaitez que le graphique dispose de davantage d’espace pour les étiquettes tout en s’affichant en deux dimensions, affectez aux propriétés **Rotation** et **Inclinaison** la valeur **0**.  
  
## Voir aussi  
 [Graphiques à secteurs &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Regrouper des petits secteurs sur un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)   
 [Afficher des valeurs en pourcentage dans un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  