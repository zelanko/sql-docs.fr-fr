---
title: "Ajouter du code HTML &#224; un rapport (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
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
ms.assetid: 30bd631a-f774-48e7-a13a-b6c2eb54d9bb
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Ajouter du code HTML &#224; un rapport (G&#233;n&#233;rateur de rapports et SSRS)
  À l'aide d'un espace réservé, vous pouvez importer des éléments HTML depuis un champ dans votre dataset pour les utiliser dans le rapport. Par défaut, un espace réservé contient du texte brut. Par conséquent vous devrez modifier le type de balisage de l'espace réservé en HTML. Pour plus d’informations, consultez [Importation de données HTML dans un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/importing-html-into-a-report-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour ajouter des éléments HTML d'un champ de votre dataset dans une zone de texte  
  
1.  Sous l’onglet **Insérer**, cliquez sur **Liste**. Cliquez sur l'aire de conception, puis faites glisser la souris pour créer une zone de la taille voulue.  
  
     La boîte de dialogue **Propriétés du dataset** s'ouvre. Vous pouvez utiliser un dataset partagé ou un dataset incorporé dans votre rapport. Pour plus d’informations, cliquez sur [Boîte de dialogue Propriétés du dataset, Requête &#40;Générateur de rapports&#41;](../../reporting-services/report-data/dataset-properties-dialog-box-query-report-builder.md) ou [Boîte de dialogue Propriétés du dataset, Requête](../Topic/Dataset%20Properties%20Dialog%20Box,%20Query.md).  
  
2.  Sous l'onglet **Insérer** , cliquez sur **Zone de texte**. Cliquez dans la liste, puis faites glisser la souris pour créer une zone de la taille voulue.  
  
3.  Faites glisser un champ HTML de votre dataset dans la zone de texte. Un espace réservé est créé pour votre champ.  
  
4.  Cliquez avec le bouton droit sur l’espace réservé, puis cliquez sur **Propriétés de l’espace réservé**.  
  
5.  Sous l’onglet **Général**, vérifiez que la zone **Valeur** contient une expression qui évalue le champ que vous avez déposé à l’étape 3.  
  
6.  Cliquez sur **HTML - Interpréter les balises HTML comme des styles**. Cette opération permet d'évaluer le champ en tant que texte HTML.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Mise en forme des nombres et des dates &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Mise en forme des lignes, couleurs et images &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-lines-colors-and-images-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés de l’espace réservé, Général &#40;Générateur de rapports et SSRS&#41;](../Topic/Placeholder%20Properties%20Dialog%20Box,%20General%20\(Report%20Builder%20and%20SSRS\).md)  
  
  