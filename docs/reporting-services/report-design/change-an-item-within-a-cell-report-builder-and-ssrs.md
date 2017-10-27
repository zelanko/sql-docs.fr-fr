---
title: "Modifier un élément dans une cellule (Générateur de rapports et SSRS) | Documents Microsoft"
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
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2f4a345f97fc3b414f6d804b127b625faa8e1204
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a>Modifier un élément dans une cellule (Générateur de rapports et SSRS)
Dans les rapports paginés [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , seuls les éléments non-conteneurs, tels que les zones de texte, les lignes ou les images, peuvent être remplacés par un nouvel élément de rapport. Par exemple, vous pouvez faire glisser une table dans une zone de texte pour remplacer la zone de texte par une table.  
  
 Si une cellule contient un élément conteneur comme un rectangle, une liste, un tableau ou une matrice, le nouvel élément est ajouté à l'élément conteneur au lieu de le remplacer. Pour remplacer un élément de conteneur par un nouvel élément, supprimez le conteneur. Sa suppression entraîne son remplacement par une zone de texte, que vous pouvez ensuite remplacer par un autre élément.  
  
 Par défaut, toutes les cellules d'une table, matrice ou région de données de type liste contiennent une zone de texte.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-an-item-within-a-cell"></a>Pour modifier un élément dans une cellule  
  
-   Sous l'onglet **Insérer** , dans le groupe **Régions de données** ou **Éléments de rapport** , cliquez sur l'élément à ajouter au rapport, puis sur le rapport. L'élément est ajouté au rapport.  
  
> [!NOTE]  
>  La boîte de dialogue **Propriétés de l’image** s’ouvre quand vous faites glisser un élément de rapport d’image vers une cellule, où vous pouvez définir des propriétés, telles que la source de l’image, avant que l’image ne soit ajoutée à la cellule.  
  
## <a name="see-also"></a>Voir aussi  
 [Images, zones de texte, Rectangles et lignes &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/images-text-boxes-rectangles-and-lines-report-builder-and-ssrs.md)   
 [Tables, Matrices et listes &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  

