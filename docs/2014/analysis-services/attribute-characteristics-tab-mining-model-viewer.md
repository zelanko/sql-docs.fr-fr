---
title: Attribut de l’onglet caractéristiques (visionneuse de modèle d’exploration de données) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9a2e67e05ac9129bd667f50bc4b6acbe673d8729
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045074"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a>Onglet Caractéristiques d'attribut (Visionneuse de modèle d'exploration de données)
  Le volet **Caractéristiques d’attribut** permet d’explorer les relations entre les résultats et les attributs d’entrée dans un modèle Naïve Bayes. Vous pouvez choisir la valeur de l'attribut cible, puis consulter la liste des attributs d'entrée qui ont l'effet le plus important sur les résultats.  
  
 **Pour plus d’informations :** [Algorithme MNB (Microsoft Naive Bayes)](data-mining/microsoft-naive-bayes-algorithm.md), [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNB (Microsoft Naive Bayes)](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de la visionneuse**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données à afficher, parmi ceux de la structure d'exploration actuelle. Le modèle d'exploration de données s'ouvre automatiquement dans une visionneuse personnalisée qui est la mieux adaptée pour le type particulier de modèle que vous avez choisi.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Pour chaque modèle, vous avez le choix entre une visionneuse personnalisée ou la visionneuse de contenu d’exploration de données ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer). Les visionneuses de plug-in apparaissent également dans cette liste, le cas échéant.  
  
 **Attribute**  
 Choisissez l'attribut prédictible que vous souhaitez analyser.  
  
 **Value**  
 Choisissez un état pour l’attribut prédictible que vous avez défini dans **Attribut**. Étant donné que les modèles Naïve Bayes ne prennent pas en charge les variables continues, tous les attributs cibles possèdent des résultats discrets ou discrétisés. L'attribut manquant est toujours ajouté automatiquement à la liste.  
  
 **Caractéristiques de \<état prévisible >**  
 Ce graphique contient les colonnes suivantes, qui décrivent la relation des états des attributs d'entrée par rapport à l'état de l'attribut prédictible sélectionné.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Variable**|Répertorie les attributs d'entrée du modèle d'exploration de données.|  
|**Valeurs**|Répertorie chaque état de l’attribut d’entrée dans **Variable**.|  
|**Probabilité**|La barre représente la probabilité que l'attribut et la valeur de cette ligne soient associés à l'état sélectionné de l'attribut prédictible. Pointez la souris sur la barre afin d'afficher la probabilité en pourcentage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèle d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  