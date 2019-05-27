---
title: Onglet de sélection (vue graphique d’analyse de précision d’exploration de données) des entrées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.columnmapping.f1
ms.assetid: f8b1193c-5c86-4c7e-8e35-158d293184fa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3fb4771c7345eb270e91a377d2755a25606f9a93
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080422"
---
# <a name="input-selection-tab-mining-accuracy-chart-view"></a>Onglet Sélection d'entrée (vue Graphique d'analyse de précision de l'exploration de données)
  Utilisez l’onglet **Sélection d’entrée** du concepteur **Graphique d’analyse de précision de l’exploration de données** pour spécifier la source des données utilisées pour tester le modèle et générer le graphique d’analyse de précision.  
  
 **Pour plus d'informations, consultez :** [Test et validation &#40;exploration de données&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Options  
 **Synchroniser les colonnes**  **de prédiction et les valeurs**  
 Activez cette case à cocher pour coordonner les attributs prédictibles dans la grille, de sorte que même s'ils portent un nom différent, ils sont dérivés de la même colonne prédictible de la structure d'exploration de données pendant l'apprentissage du modèle.  
  
 **Remarque** Cette option est activée par défaut. Vous ne devez la désactiver que dans les cas où vous savez que deux colonnes de la structure d'exploration de données dérivent de la même source relationnelle ou multidimensionnelle sous-jacente et que les colonnes contiennent les mêmes états ou ont été discrétisées de la même façon.  
  
 **Sélectionnez les colonnes du modèle d’exploration de données prévisibles à afficher dans le graphique de courbes d’élévation**  
 Grille contenant les colonnes permettant de contrôler les modèles qui sont inclus dans le graphique de courbes d'élévation et leur mode d'utilisation dans ce graphique.  
  
|Value|Description|  
|-----------|-----------------|  
|**Afficher**|Activez la case à cocher située en regard du nom de chaque colonne prédictible dans le modèle d'exploration de données que vous souhaitez afficher dans le graphique.<br /><br /> Si le graphique est trop complexe pour être consulté facilement, désactivez la case à cocher en regard d'une ou de plusieurs colonnes pour le simplifier.<br /><br /> Remarque : Impossible de créer un graphique de précision que si au moins une colonne est sélectionnée.|  
|**Modèle d'exploration de données**|Répertorie les modèles d'exploration de données contenus dans la structure d'exploration de données.|  
|**Nom de la colonne prévisible**|Sélectionnez une colonne prédictible contenue dans les modèles d'exploration de données qui sont utilisés pour créer le graphique de courbes d'élévation.|  
|**Prédire la valeur**|Sélectionnez une valeur pour la colonne prédictible. Si vous laissez ce champ vide, le graphique de courbes d'évaluation prédit le comportement du modèle pour tous les états de la colonne prédictible.|  
  
 **Sélectionner le jeu de données à utiliser pour le graphique de précision**  
 Groupe d'options qui contient trois options pour spécifier les données de test de précision.  
  
|Value|Description|  
|-----------|-----------------|  
|**Utiliser des scénarios de test de modèle d'exploration de données**|Utilisez le jeu de test créé lorsque vous avez partitionné la structure d'exploration de données et appliquez le filtre défini sur le modèle. Pour plus d’informations sur les filtres de modèle, consultez [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)|  
|**Utiliser des scénarios de test de structure d'exploration de données**|Utilisez le jeu de test créé lorsque vous avez partitionné la structure d'exploration de données.|  
|**Spécifier un autre jeu de données**|Spécifiez une table d'une vue de source de données existante à utiliser comme jeu de données de test.|  
  
## <a name="filtering-options"></a>Options de filtrage  
 Si vous sélectionnez l’option **Spécifier un autre jeu de données**, vous pouvez définir une vue de source de données et créer des filtres à appliquer à ces données. Lorsque vous créez un filtre, vous créez une clause WHERE dans la requête qui retourne les données de test de la vue de source de données.  
  
 **Remarque** Vous ne pouvez pas spécifier de filtre sur le modèle d’exploration de données en utilisant l’onglet **Sélection d’entrée** . Pour créer un filtre de modèle, cliquez sur l’onglet **Modèles d’exploration de données** et modifiez les propriétés de modèle.  
  
 Si vous n'avez pas créé de jeu d'exclusion pour le test lorsque vous avez créé la structure d'exploration de données, vous pouvez sélectionner cette option, puis spécifier la vue de source de données d'origine comme jeu de test. En utilisant cette solution de contournement, vous pouvez également définir des filtres sur les jeux de données d'origine.  
  
 **Spécifier le mappage de colonne**  
 Ouvre la boîte de dialogue **Spécifier le mappage des colonnes**, dans laquelle vous sélectionnez la source de données, spécifiez les tables de cas et imbriquées, ainsi que mappez des colonnes de données externes aux colonnes de la structure d’exploration de données.  
  
 Pour plus d’informations, consultez [Boîte de dialogue Spécifier le mappage des colonnes &#40;Graphique d’analyse de précision de l’exploration de données&#41;](specify-column-mapping-dialog-box-mining-accuracy-chart.md).  
  
 **Expression de filtre**  
 Affiche la condition de filtre que vous avez générée avec les éditeurs de filtre.  
  
 **Éditeur de filtre ouvert**  
 Ouvre la boîte de dialogue **Filtre de jeu de données** qui vous permet de sélectionner des tables externes et de définir des conditions sur les colonnes de table de cas ; ouvre également la boîte de dialogue **Filtre** permettant de générer des conditions qui s’appliquent à chaque colonne de la table sélectionnée ou aux colonnes des tables imbriquées.  
  
## <a name="see-also"></a>Voir aussi  
 [Test et des tâches de Validation et des procédures &#40;exploration de données&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Concepteur graphique d’analyse de précision d’exploration de données &#40;exploration de données&#41;](mining-accuracy-chart-designer-data-mining.md)   
 [Appliquer un filtre à un modèle d’exploration de données](data-mining/apply-a-filter-to-a-mining-model.md)   
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/mining-models-analysis-services-data-mining.md)  
  
  
