---
title: "Ajouter un Total à un groupe ou d’une région de données de tableau matriciel (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf1b96c3-7f0f-4c94-ad08-5239c77ccfe4
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c9547d7950bc594580194ee27dae65b583616a5c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs"></a>Ajouter un total à un groupe ou à une région de données de tableau matriciel (Générateur de rapports et SSRS)
 Dans un rapport paginé [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , vous pouvez ajouter des totaux à une région de données de tableau matriciel pour un groupe ou pour la totalité de la région de données. Par défaut, un total est la somme des données numériques non Null d'un groupe ou d'une région de données, après application des filtres. Pour ajouter des totaux pour un groupe, cliquez sur **Ajouter un total** dans le menu contextuel du groupe dans le volet Regroupement. Pour ajouter des totaux pour une cellule individuelle dans la zone du corps du tableau matriciel, cliquez sur **Ajouter un total** dans le menu contextuel de la cellule. La commande **Ajouter un total** est contextuelle et active uniquement pour les champs de type numérique. Selon la cellule de tableau matriciel que vous sélectionnez, vous pouvez ajouter un total pour une cellule unique en sélectionnant une cellule dans la zone du corps du tableau matriciel ou pour la totalité du groupe en sélectionnant une cellule dans la zone du groupe de lignes ou la zone du groupe de colonnes du tableau matriciel. Pour plus d’informations sur les zones de tableau matriciel, consultez [Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md).  
  
 Après avoir ajouté un total, vous pouvez remplacer la fonction par défaut Sum par une autre fonction d’agrégation de la liste des fonctions de rapport intégrées. Pour plus d’informations, consultez [référence aux fonctions d’agrégation &#40; Le Générateur de rapports et SSRS &#41; ](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-total-for-an-individual-value-in-the-tablix-body-area"></a>Pour ajouter un total pour une valeur individuelle dans la zone du corps du tableau matriciel  
  
-   Dans la zone du corps de la région de données du tableau matriciel, cliquez avec le bouton droit dans la cellule où vous souhaitez ajouter le total. La cellule doit contenir un champ de type numérique. Pointez sur **Ajouter un total**, puis cliquez sur **Ligne** ou **Colonne**.  
  
     Une nouvelle ligne ou colonne à l'extérieur du groupe actuel est ajoutée à la région de données, avec un total par défaut pour le champ dans la cellule où vous avez cliqué.  
  
     Si la région de données de tableau matriciel est une table, une ligne est ajoutée automatiquement.  
  
## <a name="to-add-totals-for-a-row-group"></a>Pour ajouter des totaux pour un groupe de lignes  
  
-   Dans la zone de groupe de lignes d’une région de données du tableau matriciel, cliquez avec le bouton droit sur une cellule dans le groupe de lignes pour lequel vous souhaitez ajouter un total, pointez sur **Ajouter un total**, puis cliquez sur **Avant** ou **Après**.  
  
     Une nouvelle ligne à l'extérieur du groupe actuel est ajoutée à la région de données, et un total par défaut est ajouté pour chaque champ de type numérique dans la ligne.  
  
## <a name="to-add-totals-for-a-column-group"></a>Pour ajouter des totaux pour un groupe de colonnes  
  
-   Dans la zone de groupe de lignes d’une région de données du tableau matriciel, cliquez avec le bouton droit sur une cellule dans le groupe de colonnes pour lequel vous souhaitez ajouter un total, pointez sur **Ajouter un total**, puis cliquez sur **Avant** ou **Après**.  
  
     Une nouvelle colonne à l'extérieur du groupe actuel est ajoutée à la région de données, et un total par défaut est ajouté pour chaque champ de type numérique dans la colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)   
 [Région de données de tableau matriciel &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Tables, Matrices et listes &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  

