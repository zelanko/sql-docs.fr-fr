---
title: Onglet discrimination d’attribut (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.discrimination.f1
ms.assetid: 68323f23-121e-44fc-be85-6f9915d6d3c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69a03f1580b525707ccadbd018d9d270b0cc7740
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527907"
---
# <a name="attribute-discrimination-tab-mining-model-viewer"></a>Onglet Discrimination d'attribut (Visionneuse de modèle d'exploration de données)
  Utilisez l’onglet **Discrimination d’attribut** pour comparer les états des attributs d’entrée et examiner leur relation avec l’attribut de résultat. Les valeurs d'attribut qui présentent la plus grande différence entre les deux états d'attribut prédictible sélectionnés sont répertoriées en premier.  
  
 **Pour plus d’informations :** [Algorithme MNB (Microsoft Naive Bayes)](data-mining/microsoft-naive-bayes-algorithm.md), [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNB (Microsoft Naive Bayes)](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l'observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données parmi ceux de la structure d'exploration de données active. Le modèle d'exploration de données s'ouvre automatiquement dans la visionneuse personnalisée correcte.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Pour chaque modèle, vous pouvez choisir la visionneuse personnalisée ou [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer. Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Attribut**  
 Choisissez un attribut prédictible.  
  
 **Valeur 1**  
 Choisissez l’état de l’attribut prédictible à comparer à l’état contenu dans **Valeur 2**.  
  
 **Valeur 2**  
 Choisissez l’état de l’attribut prédictible à comparer à l’état contenu dans **Valeur 1**. Vous pouvez également sélectionner **tous les autres États** pour comparer la valeur de la **valeur 1** avec son complément, autrement dit, toutes les autres valeurs à l’exception de la valeur 1.  
  
 **Scores de discrimination pour \<Value 1> et\<Value 2>**  
 Le graphique contient les colonnes suivantes, qui décrivent comment l'attribut cible est lié aux états spécifiques de l'attribut d'entrée.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Attributs**|Attribut d'entrée du modèle d'exploration de données.|  
|**Valeurs**|État de l’attribut répertorié dans **Attributs**.|  
|**Privilégie\<Value 1>**|La barre indique si l’attribut actuel et la valeur favorisent les résultats cibles sélectionnés dans **Valeur 1**.|  
|**Privilégie\<Value 2>**|La barre indique si l’attribut actuel et la valeur favorisent les résultats cibles sélectionnés dans **Valeur 2**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;le concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
