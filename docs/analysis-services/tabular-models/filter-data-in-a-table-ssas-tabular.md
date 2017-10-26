---
title: "Filtrer des données dans une Table (SSAS tabulaire) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.notallitemsshowing.f1
- sql13.asvs.bidtoolset.autofiltermenu.f1
- sql13.asvs.bidtoolset.customfilterdb.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 310909a6e5f607a9473fca8720d718351ef00476
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="filter-data-in-a-table-ssas-tabular"></a>Filtrer des données dans une table (SSAS Tabulaire)
  Vous pouvez appliquer des filtres quand vous importez des données pour contrôler les lignes chargées dans une table. Une fois les données importées, vous ne pouvez pas supprimer de lignes individuelles. Toutefois, vous pouvez appliquer des filtres personnalisés pour contrôler la façon dont les lignes sont affichées. Les lignes qui ne répondent pas à ces critères de filtrage sont masquées. Vous pouvez filtrer les données sur une ou plusieurs colonnes. Les filtres sont additifs, ce qui signifie que chaque filtre supplémentaire est basé sur le filtre actuel et réduit davantage le sous-ensemble de données.  
  
> [!NOTE]  
>  La fenêtre d'aperçu de filtre limite le nombre de valeurs différentes affichées. Si la limite est dépassée, un message s'affiche.  
  
### <a name="to-filter-data-based-on-column-values"></a>Pour filtrer des données selon les valeurs de colonne  
  
1.  Dans le générateur de modèles, sélectionnez une table, puis cliquez sur la flèche dans l'en-tête de la colonne par laquelle vous voulez effectuer le filtrage.  
  
2.  Dans le menu Filtre automatique, effectuez l'une des opérations suivantes :  
  
    -   Dans la liste de valeurs de colonne, sélectionnez ou désélectionnez une ou plusieurs valeurs sur lesquelles filtrer les données, puis cliquez sur **OK**.  
  
         Si le nombre de valeurs est très important, les éléments individuels peuvent ne pas être affichés dans la liste. Le message « Trop d'éléments à afficher » sera alors affiché.  
  
    -   Cliquez sur **Filtres de nombres** ou sur **Filtres de texte** (en fonction du type de colonne), puis cliquez sur l’une des commandes de l’opérateur de comparaison (comme **Égal à**) ou cliquez sur **Filtre personnalisé**. Dans la boîte de dialogue **Filtre personnalisé** , créez le filtre, puis cliquez sur **OK**.  
  
### <a name="to-clear-a-filter-for-a-column"></a>Pour effacer le filtre d'une colonne  
  
1.  Cliquez sur la flèche dans l'en-tête de la colonne dont vous souhaitez effacer un filtre.  
  
2.  Cliquez sur **effacer le filtre de \<nom de colonne >**.  
  
### <a name="to-clear-all-filters-for-a-table"></a>Pour effacer tous les filtres d'une table  
  
1.  Dans le générateur de modèles, sélectionnez la table dont vous souhaitez effacer les filtres.  
  
2.  Cliquez sur le menu **Colonne** , puis sur **Effacer tous les filtres**.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer et trier les données &#40;SSAS tabulaire&#41;](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [Perspectives &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Rôles &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  

