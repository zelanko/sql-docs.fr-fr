---
title: Onglet caractéristiques (visionneuse de modèle d’exploration de données) de cluster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cd78b9b59b69614958abb86febcd2bd290b9f302
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62680809"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a>Onglet Caractéristiques du cluster (Visionneuse de modèle d'exploration de données)
  L’onglet **Caractéristiques du cluster** vous permet d’explorer les caractéristiques d’un cluster dans un modèle de clustering, ou l’ensemble de tous les cas du modèle. Le graphique affiche l'importance de chaque paire attribut-valeur comme caractéristique qui définit le cluster, en comparaison avec d'autres clusters.  
  
 **Pour plus d’informations :** [Algorithme de gestion de clusters Microsoft](data-mining/microsoft-clustering-algorithm.md), [Explorer un modèle à l’aide de Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données parmi ceux de la structure d'exploration de données active. Le modèle d'exploration de données s'ouvre dans la visionneuse personnalisée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée associée à ce type de modèle, ou la visionneuse de contenu d’exploration de données ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer). Vous pouvez également utiliser les éventuelles visionneuses de plug-in disponibles.  
  
 **Cluster**  
 Choisissez le cluster à afficher, ou choisissez **Remplissage (tout)** pour voir la distribution des attributs du modèle dans son ensemble.  
  
 **Caractéristiques pour \<cluster >**  
 Le graphique contient les colonnes suivantes, qui décrivent les caractéristiques du cluster sélectionné.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variable**|Répertorie les attributs du modèle d'exploration de données qui se trouvent dans le cluster sélectionné.|  
|**Valeurs**|Répertorie les valeurs des attributs actuels qui se trouvent dans le cluster sélectionné.|  
|**Probabilité**|La barre indique la puissance de la paire attribut-valeur comme fonctionnalité de distinction de ce cluster. Si vous pointez la souris sur la barre, vous pouvez consulter la valeur de probabilité, représentée en pourcentage. Elle indique, étant donné cette combinaison d'attributs et de valeurs dans un cas particulier, la probabilité d'appartenance du cas à ce cluster.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
