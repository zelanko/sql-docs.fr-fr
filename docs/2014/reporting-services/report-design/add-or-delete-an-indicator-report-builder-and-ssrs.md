---
title: Insérer ou supprimer une indicateur (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 763d39ef4804a986fb190c3b5e9d8039a827bd63
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106580"
---
# <a name="add-or-delete-an-indicator-report-builder-and-ssrs"></a>Ajouter ou supprimer un indicateur (Générateur de rapports et SSRS)
  Les indicateurs sont des jauges minimales qui communiquent en un coup d'œil l'état d'une valeur de donnée unique. Pour plus d’informations les concernant, consultez [Indicateurs &#40;Générateur de rapports et SSRS&#41;](indicators-report-builder-and-ssrs.md).  
  
 Les indicateurs sont généralement placés dans des cellules d'une table ou d'une matrice, mais vous pouvez également les utiliser seuls, côte à côte avec des jauges ou incorporés dans des jauges.  
  
 Lorsque vous ajoutez un indicateur pour la première fois, il est configuré par défaut pour utiliser des pourcentages comme unités de mesure. Les plages de pourcentage sont réparties uniformément entre les membres du jeu d'indicateurs, et l'étendue de valeurs indiquée par l'indicateur correspond au parent de l'indicateur tel qu'une table ou une matrice.  
  
 Vous pouvez mettre à jour les valeurs et les états d'indicateurs. Pour plus d'informations, voir les rubriques suivantes :  
  
-   [Modifier les icônes d’indicateur et jeux d’indicateurs &#40;Générateur de rapports et SSRS&#41;](change-indicator-icons-and-indicator-sets-report-builder-and-ssrs.md)  
  
-   [Définir et configurer des unités de mesure &#40;Générateur de rapports et SSRS&#41;](set-and-configure-measurement-units-report-builder-and-ssrs.md)  
  
-   [Définir l’étendue de synchronisation &#40;Générateur de rapports et SSRS&#41;](set-synchronization-scope-report-builder-and-ssrs.md)  
  
 Étant donné qu’un indicateur est positionné à l’intérieur du panneau de jauge, vous devez sélectionner l’indicateur au lieu du panneau quand vous souhaitez configurer l’indicateur à l’aide de la boîte de dialogue **Propriétés des indicateurs** ou du volet **Propriétés** . L'image suivante illustre un indicateur sélectionné dans son panneau de jauge.  
  
 ![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")  
  
> [!NOTE]  
>  Selon la largeur de colonne et la longueur des valeurs de données, le texte des cellules de table ou de matrice peut être renvoyé à la ligne automatiquement et s'afficher sur plusieurs lignes. Lorsque cela se produit, l'icône d'indicateur peut s'étirer et changer de forme. Cela peut rendre l'icône d'indicateur moins lisible. Placez l'indicateur à l'intérieur d'un rectangle pour vous assurer que l'icône n'est pas étirée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-indicator-to-a-table-or-matrix"></a>Pour ajouter un indicateur à une table ou une matrice  
  
1.  Ouvrez un rapport existant ou créez un rapport qui contient une table et une matrice avec les données que vous souhaitez afficher. Pour plus d’informations, consultez [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md) ou [Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).  
  
2.  Insérez une colonne dans votre table ou matrice. Pour plus d’informations, consultez [Insérer ou supprimer une colonne &#40;Générateur de rapports et SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Le cas échéant, sous l’onglet **Insérer** , cliquez sur **Rectangle**, puis sur une cellule dans la nouvelle colonne.  
  
4.  Sous l’onglet **Insérer** , cliquez sur **Indicateur**, puis sur une cellule dans la nouvelle colonne.  
  
     Si vous avez ajouté un rectangle à une cellule, cliquez sur cette cellule.  
  
5.  Dans la boîte de dialogue **Sélectionner le style d’indicateur** , dans le volet gauche, cliquez sur le type d’indicateur de votre choix, puis sur le jeu d’indicateurs.  
  
6.  Cliquez sur **OK**.  
  
7.  Cliquez sur l'indicateur. Le volet **Données de la jauge** s’ouvre.  
  
8.  Dans la zone **Valeurs** , dans la liste déroulante **(Non spécifié)** , cliquez sur le champ dont vous souhaitez afficher les valeurs sous la forme d’un indicateur.  
  
     L'indicateur est configuré pour utiliser des valeurs par défaut. Par défaut, les indicateurs sont configurés pour utiliser des pourcentages comme unités de mesure et les plages de pourcentage sont réparties uniformément entre les membres de l'indicateur et la valeur que l'indicateur indique utilise l'étendue du groupe le plus proche.  
  
### <a name="to-delete-an-indicator-to-a-table-or-matrix"></a>Pour supprimer un indicateur dans une table ou une matrice  
  
1.  Cliquez avec le bouton droit sur l’indicateur à supprimer, puis sélectionnez **Supprimer**.  
  
    > [!NOTE]  
    >  Un indicateur peut être positionné à l'intérieur d'un panneau de jauge qui contient d'autres indicateurs ou jauges. Si les panneaux de jauge contiennent plusieurs éléments, veillez à cliquer sur l'indicateur pour le supprimer, et non sur le panneau de jauge. Si vous cliquez sur le panneau de jauge et le supprimez, le panneau de jauge et tous les éléments qu'il contient sont supprimés.  
  
2.  Cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs &#40;Générateur de rapports et SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  
