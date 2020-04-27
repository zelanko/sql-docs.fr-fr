---
title: Filtrer des données dans une table (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 869185e56db9a4ffb07282d3ce51ced191a6bac8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66067130"
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
  
    -   Cliquez sur **filtres de nombres** ou filtres de **texte** (selon le type de colonne), puis cliquez sur les commandes de l’opérateur de comparaison (comme **égal**à) ou cliquez sur **filtre personnalisé**. Dans la boîte de dialogue **Filtre personnalisé** , créez le filtre, puis cliquez sur **OK**.  
  
### <a name="to-clear-a-filter-for-a-column"></a>Pour effacer le filtre d'une colonne  
  
1.  Cliquez sur la flèche dans l'en-tête de la colonne dont vous souhaitez effacer un filtre.  
  
2.  Cliquez sur **effacer le \<filtre du nom de la colonne>**.  
  
### <a name="to-clear-all-filters-for-a-table"></a>Pour effacer tous les filtres d'une table  
  
1.  Dans le générateur de modèles, sélectionnez la table dont vous souhaitez effacer les filtres.  
  
2.  Cliquez sur le menu **Colonne** , puis sur **Effacer tous les filtres**.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer et trier des données &#40;la&#41;tabulaire SSAS](../filter-and-sort-data-ssas-tabular.md)   
 [Perspectives &#40;&#41;tabulaire SSAS](perspectives-ssas-tabular.md)   
 [Rôles &#40;SSAS Tabulaire&#41;](roles-ssas-tabular.md)  
  
  
