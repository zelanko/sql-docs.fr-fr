---
title: Aligner les données d’un graphique dans une table ou une matrice (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 74b6e86e6c9e7fd9d293e4c1bdab952468adb4b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106509"
---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a>Aligner les données d'un graphique dans une table ou une matrice (Générateur de rapports et SSRS)
  Les graphiques sparkline et les barres de données sont des graphiques simples de petite taille qui communiquent beaucoup d'informations avec peu de détails superflus. Lorsque vous activez cette option, les valeurs dans vos graphiques sparkline et barres de données sont alignées dans les différentes cellules de la table ou matrice, même s'il manque des valeurs dans les données sur lesquelles ils sont basés.  
  
 ![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")  
  
 Dans cette image, l'histogramme affiche les ventes quotidiennes pour chaque employé. Notez que les jours pendant lesquels un employé ne génère aucun chiffre d'affaires, le graphique laisse un espace et aligne les jours suivants horizontalement. Il aligne également les graphiques verticalement en définissant les tailles des différents graphiques les unes par rapport aux autres. Pour plus d’informations, consultez [Graphiques sparkline et barres de données &#40;Générateur de rapports et SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="align-the-data-in-a-sparkline-or-data-bar"></a>Aligner les données dans un graphique sparkline ou une barre de données  
  
1.  Cliquez dans le graphique sparkline ou la barre de données, puis choisissez **Propriétés de l’axe horizontal** ou **Propriétés de l’axe vertical**.  
  
2.  Sous l’onglet **Options de l’axe** , cochez la case **Aligner les axes dans** puis, dans la zone déroulante, sélectionnez le groupe sur lequel aligner l’axe.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Ajouter des graphiques sparkline et des barres de données &#40;Générateur de rapports et SSRS&#41;](add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
