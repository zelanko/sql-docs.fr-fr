---
title: Attribut profils onglet (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2bb75ec06d9b5c14ce5c2dcc85561412b362b40
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66063169"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a>Onglet Profils d'attribut (Visionneuse de modèle d'exploration de données)
  Utilisez l’onglet **Profils d’attribut** pour voir comment la distribution des valeurs d’entrée dans un état de modèle Naive Bayes contribue à chaque état de l’attribut de résultat. La distribution de valeurs est affichée sous la forme d'un histogramme coloré, toutes les distributions étant présentées dans un format tabulaire, afin de faciliter la comparaison des valeurs.  
  
 **Pour plus d’informations :** [L’algorithme Microsoft Naive Bayes](data-mining/microsoft-naive-bayes-algorithm.md), [Explorer un modèle à l’aide de l’Observateur de Microsoft Naive Bayes](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données à afficher, parmi ceux de la structure d'exploration de données active. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Vous pouvez choisir la visionneuse personnalisée fournie pour chaque modèle d’exploration de données ou [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer. Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Afficher la légende**  
 Sélectionnez cette option pour afficher une clé qui fait correspondre chaque valeur dans **États** à l’une des couleurs utilisées dans le graphique de distribution.  
  
 **Barres de l’histogramme**  
 Sélectionnez le nombre de barres à inclure dans l'histogramme. S’il existe davantage de barres que le nombre que vous choisissez d’afficher, les barres de la plus grande importance sont conservées et les barres restantes sont regroupées dans **Autre**.  
  
 **Prévisibles**  
 Sélectionnez une colonne prédictible dans le modèle d'exploration de données.  
  
 **Profils d'attribut**  
 La table contient les colonnes suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|**Attributs**|Affiche la liste des colonnes contenues dans le modèle d'exploration de données.|  
|**États**|Colonne facultative qui décrit l'état que représente la couleur de la ligne correspondante d'attributs. Ajoutez-la ou supprimez-la à l’aide de la case à cocher **Afficher la légende** .|  
|**Remplissage**|Affiche la répartition de l'attribut dans l'ensemble du dataset.|  
|**Colonne pour les États d’attribut prédictible**|Affiche une colonne pour chaque état de la colonne prédictible, chaque ligne correspondant à un attribut d'entrée du modèle.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
