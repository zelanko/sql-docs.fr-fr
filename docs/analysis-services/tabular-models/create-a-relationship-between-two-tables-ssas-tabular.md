---
title: "Créer une relation entre deux Tables (SSAS tabulaire) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.createrelatdb.f1
- sql13.asvs.bidtoolset.managereldb.f1
ms.assetid: 052d77b7-7922-408a-a200-786016ee4d15
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 79aa7bc1e5dff61693c4d7f5a671bffa49416bf6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="create-a-relationship-between-two-tables-ssas-tabular"></a>Créer une relation entre deux tables (SSAS Tabulaire)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Si les tables dans votre source de données n’ont pas de relations existantes, ou si vous ajoutez de nouvelles tables, vous pouvez utiliser les outils du Générateur de modèles pour créer des relations. Pour plus d’informations sur la façon dont les relations sont utilisées dans les modèles tabulaires, consultez [Relations &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/relationships-ssas-tabular.md).  
  
## <a name="create-a-relationship-between-two-tables"></a>Créer une relation entre deux tables  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-click-and-drag"></a>Pour créer une relation entre deux tables dans la vue de diagramme (clic et glisser-déplacer)  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Vue du modèle**, et enfin sur **Vue de diagramme**.  
  
2.  Cliquez (et maintenez le bouton de la souris enfoncé) sur une colonne dans une table, faites glisser le curseur vers une colonne de recherche associée dans une table de recherche associée, puis relâchez. La relation est automatiquement créée dans l'ordre correct.  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-right-click"></a>Pour créer une relation entre deux tables dans la vue de diagramme (clic droit)  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Vue du modèle**, et enfin sur **Vue de diagramme**.  
  
2.  Cliquez avec le bouton droit sur un en-tête ou une colonne de table, puis sélectionnez **Créer une relation**.  
  
3.  Dans la boîte de dialogue **Créer une relation** , pour **Table**, cliquez sur la touche Flèche bas et sélectionnez une table dans la liste déroulante.  
  
     Dans une relation « un à plusieurs », cette table doit être du côté « plusieurs ».  
  
4.  Pour **Colonne**, sélectionnez la colonne qui contient les données mises en rapport avec **Colonne de recherche associée**. La colonne est sélectionnée automatiquement si vous avez cliqué avec le bouton droit sur une colonne pour créer la relation.  
  
5.  Pour **Table de recherche associée**, sélectionnez une table qui comporte au moins une colonne de données mise en rapport avec la table que vous venez de sélectionner pour **Table**.  
  
     Dans une relation « un-à-plusieurs », cette table doit être sur côté « un », c'est-à-dire que les valeurs dans la colonne sélectionnée ne contiennent pas de doublons. Si vous essayez de créer la relation dans l’ordre incorrect (un-à-plusieurs au lieu de plusieurs-à-un), une icône apparaît en regard du champ **Colonne de recherche associée** . Inversez l'ordre pour créer une relation valide.  
  
6.  Pour **Colonne de recherche associée**, sélectionnez une colonne qui comporte des valeurs uniques qui correspondent aux valeurs dans la colonne que vous avez sélectionnée pour **Colonne**.  
  
7.  Cliquez sur **Créer**.  
  
#### <a name="to-create-a-relationship-between-two-tables-in-data-view"></a>Pour créer une relation entre deux tables dans la vue de données  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Table** , puis sur **Créer des relations**.  
  
2.  Dans la boîte de dialogue **Créer une relation** , pour **Table**, cliquez sur la touche Flèche bas et sélectionnez une table dans la liste déroulante.  
  
     Dans une relation « un à plusieurs », cette table doit être du côté « plusieurs ».  
  
3.  Pour **Colonne**, sélectionnez la colonne qui contient les données mises en rapport avec **Colonne de recherche associée**.  
  
4.  Pour **Table de recherche associée**, sélectionnez une table qui comporte au moins une colonne de données mise en rapport avec la table que vous venez de sélectionner pour **Table**.  
  
     Dans une relation « un-à-plusieurs », cette table doit être sur côté « un », c'est-à-dire que les valeurs dans la colonne sélectionnée ne contiennent pas de doublons. Si vous essayez de créer la relation dans l’ordre incorrect (un-à-plusieurs au lieu de plusieurs-à-un), une icône apparaît en regard du champ **Colonne de recherche associée** . Inversez l'ordre pour créer une relation valide.  
  
5.  Pour **Colonne de recherche associée**, sélectionnez une colonne qui comporte des valeurs uniques qui correspondent aux valeurs dans la colonne que vous avez sélectionnée pour **Colonne**.  
  
6.  Cliquez sur **Créer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer des relations &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/delete-relationships-ssas-tabular.md)   
 [Relations &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/relationships-ssas-tabular.md)  
  
  
