---
title: Visionneuse de l’arborescence de contenu générique Microsoft (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.contentviewer.f1
ms.assetid: 751b4393-f6fd-48c1-bcef-bdca589ce34c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 96a259ed9436bb7c8b79a8eb9da1c3c899e6d994
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545481"
---
# <a name="microsoft-generic-content-tree-viewer-data-mining"></a>Visionneuse de l'arborescence de contenu générique Microsoft (exploration de données)
  La **Visionneuse de l'arborescence de contenu générique Microsoft** affiche des informations détaillées sur le contenu d'un modèle d'exploration de données dans un format de table HTML standardisé. Cette vue est utile car elle présente la structure sous-jacente du modèle, ainsi que des détails sur les coefficients, la distribution des valeurs, et beaucoup plus encore.  
  
 Le contenu réel affiché dans la table varie selon l'algorithme utilisé et peut inclure des colonnes, des règles, des propriétés, des attributs, des nœuds et des formules. Pour plus d’informations sur le contenu du modèle et sur l’interprétation des informations relatives à chaque type de modèle, consultez [Contenu du modèle d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).  
  
 Les informations affichées dans la visionneuse utilisent une structure commune basée sur l'ensemble de lignes de schéma du contenu des modèles d'exploration de données. L'ensemble de lignes de schéma de contenu est une infrastructure générique pour le stockage des modèles, des statistiques et d'autres contenus d'un modèle d'exploration de données. Pour obtenir la liste des colonnes contenues dans l’ensemble de lignes de schéma pour les modèles d’exploration de données, consultez [Ensemble de lignes DMSCHEMA_MINING_MODEL_CONTENT](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).  
  
## <a name="options"></a>Options  
 **Légende de nœud (identificateur unique)**  
 Ce volet affiche la liste de tous les nœuds dans le modèle d'exploration de données sélectionné. La façon dont les nœuds sont réorganisés dans l'arborescence est différente selon le type de modèle que vous affichez.  
  
 Vous pouvez cliquer sur chaque nœud pour afficher des détails le concernant dans le volet **Détails du nœud** .  
  
 **Détails du nœud**  
 Affiche des informations détaillées à propos du contenu du nœud sélectionné. Chaque nœud stocke les informations le concernant dans un format standardisé, mais le contenu et la précision de chaque ligne de la table dépendent du type de modèle ou du type de nœud que vous affichez. Par exemple, les informations stockées pour un nœud qui représente une règle dans un modèle d'association contiennent des informations différentes d'un nœud qui représente une arborescence dans un modèle d'arbre de décision.  
  
 Pour en savoir plus sur l’interprétation des informations de nœud d’un type de modèle spécifique, consultez [Contenu du modèle d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;le concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Requêtes d’exploration de données](data-mining/data-mining-queries.md)  
  
  
