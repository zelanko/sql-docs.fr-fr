---
title: "Afficher les num&#233;ros de page ou d&#39;autres propri&#233;t&#233;s de rapport (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
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
ms.assetid: c7d95245-4709-4d04-acb4-59bf71e60d97
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# Afficher les num&#233;ros de page ou d&#39;autres propri&#233;t&#233;s de rapport (G&#233;n&#233;rateur de rapports et SSRS)
  Vous pouvez facilement ajouter des numéros de page, un titre de rapport, un nom de fichier, et d'autres propriétés de rapport aux en-têtes ou pieds de page de votre rapport. Ces propriétés sont stockées en tant que champs dans le dossier Champs prédéfinis du volet Données du rapport.  
  
-   Durée d’exécution  
  
-   Numéro de page  
  
-   Dossier Rapport  
  
-   Nom du rapport  
  
-   URL du serveur de rapports  
  
-   Nombre total de pages  
  
-   ID d'utilisateur  
  
-   Langage  
  
 Pour un numéro de page, vous pouvez ajouter le mot « Page » avant le numéro. Vous pouvez également indiquer le nombre total de pages.  
  
> [!NOTE]  
>  Le fait d'ajouter le nombre total de pages au pied de page peut ralentir les performances lors de l'exécution ou de l'affichage de votre rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour ajouter un numéro de page ou d'autres propriétés de rapport  
  
1.  Dans le volet Données du rapport, développez le dossier Champs prédéfinis.  
  
    > [!NOTE]  
    >  Si le volet des données de rapport n’est pas visible, cochez **Données du rapport** sous l’onglet Affichage.  
  
2.  Faites glisser le champ **Numéro de page** du volet des données de rapport vers l’en-tête ou le pied de page du rapport.  
  
    > [!NOTE]  
    >  Le pied de page est ajouté automatiquement au rapport. Pour ajouter un en-tête de page, sous l’onglet **Insérer**, cliquez sur **En-tête**, puis sur **Ajouter un en-tête**.  
    >   
    >  Une zone de texte qui contient l'expression simple [&PageNumber] est ajoutée.  
  
### Pour ajouter le mot « Page » avant le numéro de page  
  
1.  Cliquez avec le bouton droit sur la zone de texte qui contient [&PageNumber] et cliquez sur **Expressions**.  
  
     La zone de texte **Définir l’expression pour : valeur** contient l’expression =Globals!PageNumber.  
  
2.  Placez le curseur après le signe =, puis tapez **"Page " &**.  
  
     L'expression est maintenant ="Page "&Globals!PageNumber  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Pour ajouter le nombre total de pages après le numéro de page  
  
1.  Cliquez avec le bouton droit sur la zone de texte comportant l’expression et cliquez sur **Expressions**.  
  
2.  Tapez **&" sur "&** à la fin de l’expression.  
  
3.  Dans le volet Catégorie, développez **Champs prédéfinis** et double-cliquez sur **TotalPages**.  
  
     L'expression est maintenant ="Page "&Globals!PageNumber &" de "&Globals!TotalPages  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)   
 [Mettre en forme du texte dans une zone de texte &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
  