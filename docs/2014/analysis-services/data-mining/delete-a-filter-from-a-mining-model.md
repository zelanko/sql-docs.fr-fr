---
title: Supprimer un filtre d’un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filters [Analysis Services]
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a8b19c9c23857013796885eb8d2d3469607eae17
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66084732"
---
# <a name="delete-a-filter-from-a-mining-model"></a>Supprimer un filtre d'un modèle d'exploration de données
  Lorsque vous créez un filtre sur un modèle d'exploration de données, vous pouvez créer des modèles sur un sous-ensemble des données contenues dans la vue de source de données. Les filtres sont également utiles pour tester la précision du modèle sur un sous-ensemble des données d'origine.  
  
 Toutefois, vous devez supprimer le filtre si vous souhaitez réafficher l'intégralité des cas. Cette procédure décrit comment supprimer des conditions sur un filtre ou supprimer complètement le filtre.  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a>Pour supprimer une condition d'un filtre sur un modèle d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans l'Explorateur de solutions, cliquez sur la structure d'exploration de données qui contient le modèle d'exploration de données à filtrer.  
  
2.  Cliquez sur l'onglet **Modèles d'exploration de données** .  
  
3.  Sélectionnez le modèle et cliquez avec le bouton droit pour ouvrir le menu contextuel.  
  
     -ou-  
  
     Sélectionnez le modèle. Dans le menu **Modèle d'exploration de données** , sélectionnez **Définir le filtre de modèle**.  
  
4.  Dans la boîte de dialogue **Filtre de modèle** , cliquez avec le bouton droit sur la ligne dans la grille qui contient la condition que vous souhaitez supprimer.  
  
5.  Sélectionnez **supprimer**.  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a>Pour effacer le filtre sur un modèle d'exploration de données dans la boîte de dialogue Éditeur de filtre  
  
-   Dans la boîte de dialogue **Éditeur de filtre** , cliquez avec le bouton droit sur n’importe quelle ligne de la grille et sélectionnez **Supprimer tout**.  
  
## <a name="working-with-model-filters-using-the-properties-window"></a>Utilisation des filtres de modèle à l'aide de la fenêtre Propriétés  
 Si vous souhaitez supprimer le filtre entier, vous n'avez pas besoin d'ouvrir les boîtes de dialogue de l'Éditeur de filtre. Les conditions de filtre que vous avez créées sont disponibles dans la propriété `Filter` du modèle d'exploration de données.  
  
> [!NOTE]  
>  Vous pouvez afficher les propriétés d'un modèle d'exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], mais pas dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a>Pour effacer le filtre sur un modèle d'exploration de données dans l'Explorateur de solutions  
  
1.  Dans l'Explorateur de solutions, cliquez sur le modèle d'exploration de données qui contient le filtre.  
  
2.  Dans la fenêtre **Propriétés** , cliquez avec le bouton droit sur le texte `Filter` de filtre dans la propriété, puis sélectionnez **Sélectionner tout**.  
  
3.  Appuyez sur la touche Retour arrière ou Suppr.  
  
## <a name="see-also"></a>Voir aussi  
 [Extraction des données de cas à partir d’un modèle d’exploration de données](drill-through-to-case-data-from-a-mining-model.md)   
 [Tâches du modèle d’exploration de données et procédures](mining-model-tasks-and-how-tos.md)   
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services d’exploration de données&#41;](mining-models-analysis-services-data-mining.md)  
  
  
