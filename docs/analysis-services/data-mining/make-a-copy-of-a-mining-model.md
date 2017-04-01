---
title: "Cr&#233;er une copie d&#39;un mod&#232;le d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles d’exploration de données [Analysis Services], copie"
  - "modèles d’exploration de données [Analysis Services], création"
  - "modèles d’exploration de données [Analysis Services], rubriques de procédures"
  - "copie de modèles d'exploration de données"
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
caps.latest.revision: 12
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 12
---
# Cr&#233;er une copie d&#39;un mod&#232;le d&#39;exploration de donn&#233;es
  La création d'une copie d'un modèle d'exploration de données est utile lorsque vous souhaitez créer rapidement plusieurs modèles d'exploration de données basés sur les mêmes données. Après avoir copié le modèle, vous pouvez ensuite changer la copie du modèle en modifiant des paramètres ou en ajoutant un filtre.  
  
 Par exemple, si vous avez une table de clients liée à une table d’achats, vous pouvez créer des copies pour générer des modèles d’exploration de données distincts pour chaque client en filtrant sur des informations démographiques, telles que des attributs d’âge ou de région.  
  
 Pour plus d’informations sur la copie du contenu du modèle (tel que la représentation graphique ou les schémas de modèles) dans le Presse-papiers pour une utilisation dans d’autres programmes, consultez [Copier une vue d’un modèle d’exploration de données](../../analysis-services/data-mining/copy-a-view-of-a-mining-model.md).  
  
### Pour créer un modèle d'exploration de données connexe  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans l’Explorateur de solutions, cliquez sur la structure d’exploration de données qui contient le modèle d’exploration de données.  
  
2.  Cliquez sur l'onglet **Modèles d'exploration de données** .  
  
3.  Sélectionnez le modèle et cliquez avec le bouton droit pour ouvrir le menu contextuel.  
  
     - ou -  
  
     Sélectionnez le modèle. Dans le menu **Modèle d’exploration de données**, sélectionnez **Nouveau modèle d’exploration de données**.  
  
4.  Tapez un nom pour le nouveau modèle d'exploration de données et sélectionnez un algorithme. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Pour modifier le filtre sur le modèle d'exploration de données copié  
  
1.  Sélectionnez le modèle d'exploration de données.  
  
2.  Dans la fenêtre **Propriétés**, cliquez dans la zone de texte de la propriété **Filter**, puis sur le bouton de génération **(…)**.  
  
3.  Modifiez les conditions de filtre.  
  
     Pour plus d’informations sur l’utilisation des boîtes de dialogue de l’éditeur de filtre, consultez [Appliquer un filtre à un modèle d’exploration de données](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md).  
  
4.  Dans la fenêtre **Propriétés**, dans la zone de texte **Paramètres d’algorithme**, cliquez sur **Définir les paramètres d’algorithme**, puis modifiez les paramètres de l’algorithme si nécessaire.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [Tâches du modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Supprimer un filtre d'un modèle d'exploration de données](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  