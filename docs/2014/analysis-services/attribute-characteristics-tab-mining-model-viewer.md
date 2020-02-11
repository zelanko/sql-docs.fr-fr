---
title: Onglet caractéristiques d’attribut (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e35cf7db00effb5ce700a1ac883877f67650d3cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66063046"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a>Onglet Caractéristiques d'attribut (Visionneuse de modèle d'exploration de données)
  Le volet **Caractéristiques d’attribut** permet d’explorer les relations entre les résultats et les attributs d’entrée dans un modèle Naïve Bayes. Vous pouvez choisir la valeur de l'attribut cible, puis consulter la liste des attributs d'entrée qui ont l'effet le plus important sur les résultats.  
  
 **Pour plus d’informations :** [algorithme Microsoft Naive Bayes](data-mining/microsoft-naive-bayes-algorithm.md), [Parcourir un modèle à l’aide de Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l'observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d’exploration de données**  
 Choisissez un modèle d'exploration de données à afficher, parmi ceux de la structure d'exploration actuelle. Le modèle d'exploration de données s'ouvre automatiquement dans une visionneuse personnalisée qui est la mieux adaptée pour le type particulier de modèle que vous avez choisi.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Pour chaque modèle, vous avez le choix entre une visionneuse personnalisée ou la visionneuse de contenu d’exploration de données ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer). Les visionneuses de plug-in apparaissent également dans cette liste, le cas échéant.  
  
 **Attribut**  
 Choisissez l'attribut prédictible que vous souhaitez analyser.  
  
 **Valeur**  
 Choisissez un état pour l’attribut prédictible que vous avez défini dans **Attribut**. Étant donné que les modèles Naïve Bayes ne prennent pas en charge les variables continues, tous les attributs cibles possèdent des résultats discrets ou discrétisés. L'attribut manquant est toujours ajouté automatiquement à la liste.  
  
 **Caractéristiques de \<l’état prévisible>**  
 Ce graphique contient les colonnes suivantes, qui décrivent la relation des états des attributs d'entrée par rapport à l'état de l'attribut prédictible sélectionné.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Variable**|Répertorie les attributs d'entrée du modèle d'exploration de données.|  
|**Valeurs**|Répertorie chaque état de l’attribut d’entrée dans **Variable**.|  
|**Risque**|La barre représente la probabilité que l'attribut et la valeur de cette ligne soient associés à l'état sélectionné de l'attribut prédictible. Pointez la souris sur la barre afin d'afficher la probabilité en pourcentage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;le concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
