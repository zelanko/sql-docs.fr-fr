---
title: "Masquer des &#233;l&#233;ments de l&#233;gende dans le graphique (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Masquer des &#233;l&#233;ments de l&#233;gende dans le graphique (G&#233;n&#233;rateur de rapports et SSRS)
Par défaut, toute série ajoutée à un graphique dans un rapport paginé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui n’est pas à base de formes est ajoutée en tant qu’élément à la légende. Pour les graphiques à secteurs, en anneau, en entonnoir et en pyramide, toute série ajoutée au graphique ajoutera des points de données individuels à la légende.  
  
 Vous pouvez masquer tout élément de la légende. Lorsque vous masquez un élément de légende, celui-ci continuera à figurer dans le graphique. Cela peut s'avérer utile dans les cas où vous ne souhaiteriez pas afficher plus d'informations sur une série ajoutée au graphique. Par exemple, si vous avez ajouté une série calculée comme une moyenne mobile au graphique, vous pouvez masquer cette entrée dans la légende de manière à afficher davantage d'informations sur la série d'origine uniquement.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Pour masquer un élément dans la légende  
  
1.  Cliquez avec le bouton droit sur la série que vous souhaitez masquer et sélectionnez **Propriétés de la série**.  
  
2.  Cliquez sur **Légende**. Sélectionnez l'option **Ne pas afficher cette série dans une légende** .  
  
    > [!NOTE]  
    >  Vous ne pouvez pas masquer une série d'un groupe et pas des autres. Si vous avez ajouté un champ à la zone **Groupes de séries** , toutes les séries qui appartiennent à ce groupe seront masquées.  
  
## Voir aussi  
 [Mise en forme de la légende sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-the-legend-on-a-chart-report-builder-and-ssrs.md)   
 [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Modifier le texte d’un élément de légende &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/change-the-text-of-a-legend-item-report-builder-and-ssrs.md)   
 [Ajouter une moyenne mobile à un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés de la légende, Général &#40;Générateur de rapports et SSRS&#41;](../Topic/Legend%20Properties%20Dialog%20Box,%20General%20\(Report%20Builder%20and%20SSRS\).md)  
  
  