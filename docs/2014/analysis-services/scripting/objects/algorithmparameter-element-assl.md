---
title: Élément AlgorithmParameter (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 70e9e3619eb5f96ff2e64c87855b2bd33063aaf0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052507"
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
  
 Paramètres d’algorithme disponibles, y compris les informations de validation et d’affichage peuvent être récupérés à partir de la [DMSCHEMA_MINING_SERVICE_PARAMETERS](../../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md) de lignes du schéma.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AlgorithmParameter>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Élément Algorithm &#40;ASSL&#41;](../properties/algorithm-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  