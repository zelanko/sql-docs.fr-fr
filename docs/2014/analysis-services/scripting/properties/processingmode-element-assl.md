---
title: Élément ProcessingMode (ASSL) | Documents Microsoft
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
- ProcessingMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ProcessingMode
helpviewer_keywords:
- ProcessingMode element
ms.assetid: dff6eeba-f09c-4d8c-ad81-caef76254af0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a4f302608db355a639d9fb82e024a7a72cf560b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043931"
---
# <a name="processingmode-element-assl"></a>Élément ProcessingMode (ASSL)
  Indique si l'instance doit créer les index et effectuer l'agrégation lors du traitement ou après celui-ci.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <ProcessingMode>...</ProcessingMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Régulière*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Cube](../objects/cube-element-assl.md), [Dimension](../objects/dimension-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [Partition](../objects/partition-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de `ProcessingMode` dans l'élément `Cube` fournit la valeur par défaut pour le cube et peut être remplacée en définissant l'élément `ProcessingMode` pour chaque partition.  
  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Régulière*|L'instance crée des index et effectue des agrégations au cours du traitement.|  
|*LazyOptimizations*|L'instance crée des index et effectue des agrégations après le traitement.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `ProcessingMode` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ProcessingMode>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  