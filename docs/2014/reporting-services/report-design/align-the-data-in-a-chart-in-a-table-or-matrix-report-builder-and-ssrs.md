---
title: Aligner les données d’un graphique dans une table ou une matrice (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 7277e8a0b50fb8e67a6601218190241c11efbd74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102409"
---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a>Aligner les données d'un graphique dans une table ou une matrice (Générateur de rapports et SSRS)
  Les graphiques sparkline et les barres de données sont des graphiques simples de petite taille qui communiquent beaucoup d'informations avec peu de détails superflus. Lorsque vous activez cette option, les valeurs dans vos graphiques sparkline et barres de données sont alignées dans les différentes cellules de la table ou matrice, même s'il manque des valeurs dans les données sur lesquelles ils sont basés.  
  
 ![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")  
  
 Dans cette image, l'histogramme affiche les ventes quotidiennes pour chaque employé. Notez que les jours pendant lesquels un employé ne génère aucun chiffre d'affaires, le graphique laisse un espace et aligne les jours suivants horizontalement. Il aligne également les graphiques verticalement en définissant les tailles des différents graphiques les unes par rapport aux autres. Pour plus d’informations, consultez [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="align-the-data-in-a-sparkline-or-data-bar"></a>Aligner les données dans un graphique sparkline ou une barre de données  
  
1.  Cliquez dans le graphique sparkline ou la barre de données, puis choisissez **Propriétés de l’axe horizontal** ou **Propriétés de l’axe vertical**.  
  
2.  Sous l’onglet **Options de l’axe** , cochez la case **Aligner les axes dans** puis, dans la zone déroulante, sélectionnez le groupe sur lequel aligner l’axe.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Ajouter des graphiques sparkline et barres de données &#40;Générateur de rapports et SSRS&#41;](add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
