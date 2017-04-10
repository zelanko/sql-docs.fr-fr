---
title: "Modifier la hauteur de ligne ou la largeur de colonne (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
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
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Modifier la hauteur de ligne ou la largeur de colonne (G&#233;n&#233;rateur de rapports et SSRS)
  Lorsque vous définissez la hauteur d'une ligne, vous spécifiez sa hauteur maximale dans le rapport rendu. Toutefois, par défaut, les zones de texte de la ligne sont définies de manière à s'étendre verticalement pour accueillir toutes les données requises au moment de l'exécution, ce qui peut entraîner le développement d'une ligne au-delà de la hauteur spécifiée. Pour définir une hauteur de ligne fixe, vous devez modifier les propriétés des zones de texte afin qu'elles ne se développent pas automatiquement.  
  
 Lorsque vous définissez la largeur d'une colonne,vous spécifiez sa largeur maximale dans le rapport rendu. Les colonnes ne s'ajustent pas horizontalement de manière automatique en fonction du texte à afficher.  
  
 Si une cellule d'une ligne ou d'une colonne contient un rectangle ou une région de données, la hauteur et la largeur minimales de la cellule sont déterminées par la hauteur et largeur de l'élément contenu. Pour plus d’informations, consultez [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour modifier la hauteur de ligne en déplaçant les poignées de ligne  
  
1.  Dans la vue Conception, cliquez n'importe où dans la région de données de tableau matriciel pour la sélectionner. Des poignées de ligne grises s'affichent sur la bordure extérieure de la région de données de tableau matriciel.  
  
2.  Avec la souris, pointez sur le bord de la poignée de ligne que vous souhaitez développer. Une double flèche apparaît.  
  
3.  Cliquez pour saisir le bord de la ligne et le déplacer vers le haut ou vers le bas afin d'ajuster la hauteur de la ligne  
  
### Pour modifier la hauteur de ligne en définissant les propriétés de cellule  
  
1.  Dans la vue Conception, cliquez sur une cellule dans la ligne de table.  
  
     ![Cellule sélectionnée dans une table](../../reporting-services/report-design/media/table-selectcell.png "Cellule sélectionnée dans une table")  
  
2.  Dans le volet **Propriétés** qui s’affiche, modifiez la propriété **Hauteur**, puis cliquez n’importe où en dehors du volet **Propriétés**.  
  
     ![Volet Propriétés pour la cellule de table sélectionnée](../../reporting-services/report-design/media/cell-propertiespane.png "Volet Propriétés pour la cellule de table sélectionnée")  
  
### Pour empêcher le développement vertical automatique d'une ligne  
  
1.  Dans la vue Conception, cliquez n'importe où dans la région de données de tableau matriciel pour la sélectionner. Des poignées de ligne grises s'affichent sur la bordure extérieure de la région de données de tableau matriciel.  
  
2.  Cliquez sur la poignée de la ligne pour sélectionner la ligne.  
  
3.  Dans le volet Propriétés, affectez à CanGrow la valeur **False**.  
  
    > [!NOTE]  
    >  Si le volet Propriétés n’est pas visible, dans le menu **Affichage**, cliquez sur **Propriétés**.  
  
### Pour modifier la largeur de colonne  
  
1.  Dans la vue Conception, cliquez n'importe où dans la région de données de tableau matriciel pour la sélectionner. Des poignées de colonne grises s’affichent sur la bordure extérieure de la région de données de tableau matriciel.  
  
2.  Avec la souris, pointez sur le bord de la poignée de colonne que vous souhaitez développer. Une double flèche apparaît.  
  
3.  Cliquez pour saisir le bord de la colonne et le déplacer vers la gauche ou vers la droite afin d'ajuster la largeur de la colonne.  
  
## Voir aussi  
 [Région de données de tableau matriciel (Générateur de rapports et SSRS)](https://msdn.microsoft.com/library/dd220587.aspx)   
 [Cellules, lignes et colonnes de région de données de tableau matriciel (Générateur de rapports et SSRS)](https://msdn.microsoft.com/library/dd220511.aspx)   
 [Tables (Générateur de rapports et SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Matrices (Générateur de rapports et SSRS)](https://msdn.microsoft.com/library/dd207149.aspx)   
 [Listes (Générateur de rapports et SSRS)](https://msdn.microsoft.com/library/dd239330.aspx)   
 [Tables, matrices et listes (Générateur de rapports et SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  