---
title: Supprimer un filtre d’un modèle d’exploration de données | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 66293cf1be2ced3106e2966a930639c12330a660
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52545662"
---
# <a name="delete-a-filter-from-a-mining-model"></a>Supprimer un filtre d'un modèle d'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Lorsque vous créez un filtre sur un modèle d'exploration de données, vous pouvez créer des modèles sur un sous-ensemble des données contenues dans la vue de source de données. Les filtres sont également utiles pour tester la précision du modèle sur un sous-ensemble des données d'origine.  
  
 Toutefois, vous devez supprimer le filtre si vous souhaitez réafficher l'intégralité des cas. Cette procédure décrit comment supprimer des conditions sur un filtre ou supprimer complètement le filtre.  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a>Pour supprimer une condition d'un filtre sur un modèle d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans l'Explorateur de solutions, cliquez sur la structure d'exploration de données qui contient le modèle d'exploration de données à filtrer.  
  
2.  Cliquez sur l'onglet **Modèles d'exploration de données** .  
  
3.  Sélectionnez le modèle et cliquez avec le bouton droit pour ouvrir le menu contextuel.  
  
     -ou-  
  
     Sélectionnez le modèle. Dans le menu **Modèle d'exploration de données** , sélectionnez **Définir le filtre de modèle**.  
  
4.  Dans la boîte de dialogue **Filtre de modèle** , cliquez avec le bouton droit sur la ligne dans la grille qui contient la condition que vous souhaitez supprimer.  
  
5.  Sélectionnez **Supprimer**.  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a>Pour effacer le filtre sur un modèle d'exploration de données dans la boîte de dialogue Éditeur de filtre  
  
-   Dans la boîte de dialogue **Éditeur de filtre** , cliquez avec le bouton droit sur n’importe quelle ligne de la grille et sélectionnez **Supprimer tout**.  
  
## <a name="working-with-model-filters-using-the-properties-window"></a>Utilisation des filtres de modèle à l'aide de la fenêtre Propriétés  
 Si vous souhaitez supprimer le filtre entier, vous n'avez pas besoin d'ouvrir les boîtes de dialogue de l'Éditeur de filtre. Les conditions de filtre que vous avez créées sont disponibles dans la propriété **Filter** du modèle d'exploration de données.  
  
> [!NOTE]  
>  Vous pouvez afficher les propriétés d'un modèle d'exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], mais pas dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a>Pour effacer le filtre sur un modèle d'exploration de données dans l'Explorateur de solutions  
  
1.  Dans l'Explorateur de solutions, cliquez sur le modèle d'exploration de données qui contient le filtre.  
  
2.  Dans la fenêtre **Propriétés** , cliquez avec le bouton droit sur le texte du filtre de la propriété **Filter** , puis sélectionnez **Sélectionner tout**.  
  
3.  Appuyez sur la touche Retour arrière ou Suppr.  
  
## <a name="see-also"></a>Voir aussi  
 [Extraire des données de cas à partir d'un modèle d'exploration de données](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)   
 [Tâches du modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
