---
title: Modifier les mappages de filtre de lignes (SSAS tabulaire), de tables ou de colonnes | Documents Microsoft
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
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2124c526-5772-4f84-a019-9dd3e906e8dd
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 055b4415c1b7c60a1f22047d8e7ac95c7bc0e8cb
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="change-table-column-or-row-filter-mappings-ssas-tabular"></a>Changer des mappages de filtres de lignes, de tables ou de colonnes (SSAS Tabulaire)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Cette rubrique explique comment modifier les mappages de filtre de lignes, de tables ou de colonnes à l’aide de la **modifier les propriétés de Table** boîte de dialogue de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
 Les options proposées dans la boîte de dialogue **Modifier les propriétés de la table** diffèrent selon que vous avez initialement importé les données en sélectionnant des tables dans une liste ou en utilisant une requête SQL. Si vous avez importé initialement les données par la sélection dans une liste, la boîte de dialogue **Modifier les propriétés de la table** affiche le mode Aperçu de la table. Ce mode affiche uniquement un sous-ensemble limité aux cinquante premières lignes de la table source. Si vous avez importé initialement les données à l’aide d’une instruction SQL, la boîte de dialogue **Modifier les propriétés de la table** affiche uniquement une instruction SQL. Si vous utilisez une instruction de requête SQL, vous pouvez récupérer un sous-ensemble de lignes, soit en concevant un filtre, soit en modifiant manuellement l'instruction SQL.  
  
 Si vous modifiez la source en une table qui comporte des colonnes différentes de la table actuelle, un message s'affiche pour vous avertir que les colonnes sont différentes. Vous devez ensuite sélectionner les colonnes que vous souhaitez placer dans la table actuelle et cliquer sur **Enregistrer**. Vous pouvez remplacer la table entière en activant la case à cocher située à la gauche de la table.  
  
> [!NOTE]  
>  Si votre table a plusieurs partitions, vous ne pouvez pas utiliser la boîte de dialogue Modifier les propriétés de la table pour modifier les mappages de filtre de lignes. Pour modifier des mappages de filtre de lignes dans des tables avec plusieurs partitions, utilisez le Gestionnaire de partitions. Pour plus d’informations, consultez [Partitions &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### <a name="to-change-table-column-or-row-filter-mappings"></a>Pour modifier des mappages de filtres de lignes, de tables ou de colonnes  
  
1.  Dans le générateur de modèles, cliquez sur la table, puis sur le menu **Table** , et enfin sur **Propriétés de la table**.  
  
2.  Dans la boîte de dialogue **Modifier les propriétés de la table** , recherchez la colonne qui contient les critères sur lesquels vous souhaitez effectuer le filtrage, puis cliquez sur la flèche Bas à la droite du titre de colonne.  
  
3.  Dans le menu **Filtre automatique** , effectuez l’une des opérations suivantes :  
  
    -   Dans la liste de valeurs de colonne, sélectionnez ou désélectionnez une ou plusieurs valeurs sur lesquelles filtrer les données, puis cliquez sur OK.  
  
         Si le nombre de valeurs est très important, les éléments individuels peuvent ne pas être affichés dans la liste. Le message « Trop d'éléments à afficher » sera alors affiché.  
  
    -   Cliquez sur **Filtres de nombres** ou sur **Filtres de texte** (en fonction du type de colonne), puis cliquez sur l’une des commandes de l’opérateur de comparaison (comme Égal à) ou cliquez sur Filtre personnalisé. Dans la boîte de dialogue **Filtre personnalisé** , créez le filtre, puis cliquez sur **OK**.  
  
         Si vous faites une erreur et devez recommencer, cliquez sur **Effacer les filtres de lignes**.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Modifier les propriétés de la table &#40;SSAS&#41;](http://msdn.microsoft.com/library/8d913e83-7246-44cc-8fc7-31729023c0d8)  
  
  
