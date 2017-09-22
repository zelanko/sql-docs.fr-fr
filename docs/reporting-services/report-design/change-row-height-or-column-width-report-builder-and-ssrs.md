---
title: "Modifier la hauteur de ligne ou de la largeur de colonne (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: c13295c229dc4450b9661c25f86d7eacf669787d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="change-row-height-or-column-width-report-builder-and-ssrs"></a>Modifier la hauteur de ligne ou la largeur de colonne (Générateur de rapports et SSRS)
  Lorsque vous définissez la hauteur d'une ligne, vous spécifiez sa hauteur maximale dans le rapport rendu. Toutefois, par défaut, les zones de texte de la ligne sont définies de manière à s'étendre verticalement pour accueillir toutes les données requises au moment de l'exécution, ce qui peut entraîner le développement d'une ligne au-delà de la hauteur spécifiée. Pour définir une hauteur de ligne fixe, vous devez modifier les propriétés des zones de texte afin qu'elles ne se développent pas automatiquement.  
  
 Lorsque vous définissez la largeur d'une colonne,vous spécifiez sa largeur maximale dans le rapport rendu. Les colonnes ne s'ajustent pas horizontalement de manière automatique en fonction du texte à afficher.  
  
 Si une cellule d'une ligne ou d'une colonne contient un rectangle ou une région de données, la hauteur et la largeur minimales de la cellule sont déterminées par la hauteur et largeur de l'élément contenu. Pour plus d’informations, consultez [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-row-height-by-moving-row-handles"></a>Pour modifier la hauteur de ligne en déplaçant les poignées de ligne  
  
1.  Dans la vue Conception, cliquez n'importe où dans la région de données de tableau matriciel pour la sélectionner. Des poignées de ligne grises s'affichent sur la bordure extérieure de la région de données de tableau matriciel.  
  
2.  Avec la souris, pointez sur le bord de la poignée de ligne que vous souhaitez développer. Une double flèche apparaît.  
  
3.  Cliquez pour saisir le bord de la ligne et le déplacer vers le haut ou vers le bas afin d'ajuster la hauteur de la ligne  
  
### <a name="to-change-row-height-by-setting-cell-properties"></a>Pour modifier la hauteur de ligne en définissant les propriétés de cellule  
  
1.  Dans la vue Conception, cliquez sur une cellule dans la ligne de table.  
  
     ![Sélectionné la cellule dans une Table](../../reporting-services/report-design/media/table-selectcell.png "sélectionné la cellule dans une Table")  
  
2.  Dans le volet **Propriétés** qui s’affiche, modifiez la propriété **Hauteur** , puis cliquez n’importe où en dehors du volet **Propriétés** .  
  
     ![Volet Propriétés de cellule de tableau sélectionnée](../../reporting-services/report-design/media/cell-propertiespane.png "volet Propriétés de cellule de la table sélectionnée")  
  
### <a name="to-prevent-a-row-from-automatically-expanding-vertically"></a>Pour empêcher le développement vertical automatique d'une ligne  
  
1.  Dans la vue Conception, cliquez n'importe où dans la région de données de tableau matriciel pour la sélectionner. Des poignées de ligne grises s'affichent sur la bordure extérieure de la région de données de tableau matriciel.  
  
2.  Cliquez sur la poignée de la ligne pour sélectionner la ligne.  
  
3.  Dans le volet Propriétés, affectez à CanGrow la valeur **False**.  
  
    > [!NOTE]  
    >  Si le volet Propriétés n’est pas visible, dans le menu **Affichage** , cliquez sur **Propriétés**.  
  
### <a name="to-change-column-width"></a>Pour modifier la largeur de colonne  
  
1.  Dans la vue Conception, cliquez n'importe où dans la région de données de tableau matriciel pour la sélectionner. Des poignées de colonne grises s’affichent sur la bordure extérieure de la région de données de tableau matriciel.  
  
2.  Avec la souris, pointez sur le bord de la poignée de colonne que vous souhaitez développer. Une double flèche apparaît.  
  
3.  Cliquez pour saisir le bord de la colonne et le déplacer vers la gauche ou vers la droite afin d'ajuster la largeur de la colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Région de données de tableau matriciel (Générateur de rapports et SSRS)](/sql-docs/docs/reporting-services/report-design/tablix-data-region-report-builder-and-ssrs)   
 [Les cellules de région de données de tableau matriciel, lignes et colonnes (Générateur de rapports) et SSRS](/sql-docs/docs/reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs)   
 [Tables (Générateur de rapports et SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Matrices (Générateur de rapports et SSRS)](/sql-docs/docs/reporting-services/report-design/create-a-matrix-report-builder-and-ssrs)   
 [Listes (Générateur de rapports et SSRS)](/sql-docs/docs/reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs)   
 [Tables, Matrices et listes (Générateur de rapports et SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
