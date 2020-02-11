---
title: Ajouter des graphiques sparkline et des barres de données (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1dbb3fd9ec10c5e1ca11a7e150f0d8a4c0fec883
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106518"
---
# <a name="add-sparklines-and-data-bars-report-builder-and-ssrs"></a>Ajouter des graphiques sparkline et des barres de données (Générateur de rapports et SSRS)
  Les graphiques sparkline et les barres de données sont des graphiques de petite taille qui communiquent beaucoup d'informations avec peu de détails superflus. Pour plus d’informations sur ces graphiques, consultez [Graphiques sparkline et barres de données &#40;Générateur de rapports et SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
 Les graphiques sparkline et les barres de données sont généralement placés dans les cellules d'une table ou d'une matrice. Les graphiques sparkline affichent habituellement une seule série chacun. Les barres de données peuvent contenir un ou plusieurs points de données. Les graphiques sparkline et barres de données tirent tous deux leur impact de la répétition des informations de série pour chaque ligne dans la table ou la matrice.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-sparkline-or-data-bar-to-a-table-or-matrix"></a>Pour ajouter un graphique sparkline ou une barre de données à une table ou une matrice  
  
1.  Si vous ne l'avez pas encore fait, créez une table ou une matrice avec les données que vous souhaitez afficher. Pour plus d’informations, consultez [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md) ou [Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).  
  
2.  Insérez une colonne dans votre table ou matrice. Pour plus d’informations, consultez [Insérer ou supprimer une colonne &#40;Générateur de rapports et SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Sous l’onglet **Insérer** , cliquez sur **Graphique sparkline** ou sur **Barre de données**, puis cliquez dans une cellule de la nouvelle colonne.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas insérer de graphiques sparkline dans un groupe de détails dans une table. Ils doivent entrer dans une cellule associée à un groupe.  
  
4.  Dans la boîte de dialogue **Changer le type de graphique sparkline/Changer le type de barre de données** , cliquez sur le type de graphique sparkline ou de barre de données de votre choix, puis sur **OK**.  
  
5.  Cliquez sur le graphique sparkline ou la barre de données.  
  
     Le volet **Données du graphique** s’ouvre.  
  
6.  Dans la zone **Valeurs** , cliquez sur le signe plus ( **)** Ajouter des champs **+** , puis sur le champ dont vous voulez représenter les valeurs graphiquement.  
  
7.  Dans la zone **Groupes de catégories** , cliquez sur le signe plus ( **)** Ajouter des champs **+** , puis sur le champ selon lequel vous voulez regrouper les valeurs.  
  
     En général, pour les graphiques sparkline et les barres de données, vous n’ajoutez pas de champ à la zone **Groupes de séries** car vous voulez une seule série pour chaque ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Aligner les données d’un graphique dans une table ou une matrice &#40;Générateur de rapports et SSRS&#41;](align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
