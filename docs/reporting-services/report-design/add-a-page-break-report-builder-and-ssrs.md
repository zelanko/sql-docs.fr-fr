---
title: "Ajouter un saut de page (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
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
ms.assetid: 3846cd48-2787-47e9-b13b-7fc45a205f68
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# Ajouter un saut de page (G&#233;n&#233;rateur de rapports et SSRS)
  Vous pouvez ajouter un saut de page aux rectangles, régions de données ou groupes dans des régions de données pour contrôler la quantité d'informations sur chaque page. L'ajout de sauts de page peut améliorer les performances des rapports publiés, car seuls les éléments sur chaque page doivent être traités pendant que vous visualisez le rapport. Lorsque le rapport entier est une page unique, tous les éléments doivent être traités avant de pouvoir consulter le rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour ajouter un saut de page à une région de données  
  
1.  Dans l’aire de conception, cliquez avec le bouton droit sur la poignée d’angle de la région de données, puis cliquez sur **Propriétés du tableau matriciel**.  
  
2.  Sous l'onglet **Général** , sous **Options de saut de page**, sélectionnez l'une des options suivantes :  
  
    -   **Insérer un saut de page avant**. Sélectionnez cette option si vous souhaitez ajouter un saut de page avant le tableau.  
  
    -   **Insérer un saut de page après**. Sélectionnez cette option si vous souhaitez ajouter un saut de page après le tableau.  
  
    -   **Faire tenir le tableau sur une page si possible**. Sélectionnez cette option si vous souhaitez que les données restent sur une page.  
  
### Pour ajouter un saut de page à un rectangle  
  
1.  Sur l’aire de conception, cliquez avec le bouton droit sur le rectangle où vous souhaitez ajouter un saut de page, puis cliquez sur **Propriétés du rectangle**.  
  
2.  Sous l'onglet **Général** , sous **Options de saut de page**, sélectionnez l'une des options suivantes :  
  
    -   **Insérer un saut de page avant**. Sélectionnez cette option si vous souhaitez ajouter un saut de page avant le rectangle.  
  
    -   **Insérer un saut de page après**. Sélectionnez cette option si vous souhaitez ajouter un saut de page après le rectangle.  
  
    -   **Omettre la bordure sur le saut de page**. Sélectionnez cette option si vous ne souhaitez pas de bordure sur le saut de page.  
  
    -   **Conserver le contenu sur la même page, si possible**. Sélectionnez cette option lorsque vous souhaitez que le contenu à l'intérieur du rectangle reste sur une page.  
  
### Pour ajouter un saut de page à un groupe de lignes dans un tableau, une matrice ou une liste  
  
1.  Dans le volet Regroupement, cliquez avec le bouton droit sur un groupe de lignes, puis cliquez sur **Propriétés du groupe**.  
  
    > [!NOTE]  
    >  Les sauts de page définis sur les groupes de colonnes sont ignorés.  
  
2.  Sous l'onglet **Sauts de page** , sélectionnez **Entre chaque instance d'un groupe** pour ajouter un saut de page entre chaque instance d'un groupe dans le tableau.  
  
3.  Si vous le souhaitez, sélectionnez **Au début d'un groupe également** ou **À la fin d'un groupe également** pour spécifier qu'un saut de page soit ajouté au début ou à la fin d'un groupe dans le tableau.  
  
## Voir aussi  
 [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)  
  
  