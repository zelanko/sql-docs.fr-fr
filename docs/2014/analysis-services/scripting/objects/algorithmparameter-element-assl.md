---
title: Élément AlgorithmParameter (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AlgorithmParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AlgorithmParameter
helpviewer_keywords:
- AlgorithmParameter element
ms.assetid: 73211495-065c-43c6-a486-be6044617263
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d8eb25678d58f676ee10ef488b376c8331c59e15
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109960"
---
# <a name="algorithmparameter-element-assl"></a>Élément AlgorithmParameter (ASSL)
  Définit un paramètre pour l’algorithme utilisé par un [MiningModel](miningmodel-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AlgorithmParameters>  
   <AlgorithmParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </AlgorithmParameter>  
</AlgorithmParameters>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AlgorithmParameters](../collections/algorithmparameters-element-assl.md)|  
|Éléments enfants|[Nom](../properties/name-element-assl.md), [Valeur](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Un `AlgorithmParameter` est un paramètre destiné à un algorithme de modèle d'exploration de données. `AlgorithmParameter` représente ce paramètre sous la forme d'une paire nom/valeur. Le jeu de paramètres applicables qu'un `AlgorithmParameter` peut représenter dépend d'un algorithme. Pour plus d'informations sur les paramètres d'un algorithme spécifique, consultez la documentation relative à ce dernier.  
  
 Paramètres d’algorithme disponibles, y compris les informations de validation et d’affichage, peuvent être récupérées à partir de la [DMSCHEMA_MINING_SERVICE_PARAMETERS](../../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md) ensemble de lignes de schéma.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AlgorithmParameter>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Élément Algorithm &#40;ASSL&#41;](../properties/algorithm-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
