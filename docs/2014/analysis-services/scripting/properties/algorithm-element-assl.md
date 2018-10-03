---
title: Élément Algorithm (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Algorithm Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Algorithm
helpviewer_keywords:
- Algorithm element
ms.assetid: 188bf7ce-c5c9-406a-af75-5a026c92a569
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9fb2ab30f6abd753f0c954ef41ad26d0af9dcda8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149779"
---
# <a name="algorithm-element-assl"></a>Élément Algorithm (ASSL)
  Définit l’algorithme utilisé par un [MiningModel](../objects/miningmodel-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModel>  
      ...  
   <Algorithm>...</Algorithm>  
      ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément obligatoire qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de l'élément `Algorithm` est une chaîne qui identifie l'algorithme. Par exemple, la chaîne peut être *Microsoft_Naive_Bayes*, *Microsoft_Decision_Trees*, ou *Microsoft_Clustering.* La chaîne identifie les algorithmes fournis par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] et algorithmes personnalisés fournis par l’utilisateur. Les valeurs disponibles pour le `Algorithm` élément peut être récupéré à partir de la colonne SERVICE_NAME de le [DMSCHEMA_MINING_SERVICES](../../schema-rowsets/data-mining/dmschema-mining-services-rowset.md) ensemble de lignes de schéma.  
  
 L’élément qui correspond au parent de `Algorithm` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MiningModel>. Un élément étroitement lié dans le modèle objet AMO est <xref:Microsoft.AnalysisServices.MiningModelAlgorithms>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AlgorithmParameter &#40;ASSL&#41;](../objects/algorithmparameter-element-assl.md)   
 [Élément AlgorithmParameters &#40;ASSL&#41;](../collections/algorithmparameters-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
