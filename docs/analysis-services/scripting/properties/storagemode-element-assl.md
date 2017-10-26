---
title: "Élément StorageMode (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- StorageMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- StorageMode
helpviewer_keywords:
- StorageMode element
ms.assetid: 197e8153-1ab6-43ba-a7e9-ae9be19ac511
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd6ed7838025255015c3a4103689b772dd035771
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="storagemode-element-assl"></a>Élément StorageMode (ASSL)
  Détermine le mode de stockage de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <StorageMode>...</StorageMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*MOLAP*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Élément cube &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/cube-element-assl.md), [De dimension, élément &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/dimension-element-assl.md), [Élément MeasureGroup &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [De partition, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*MOLAP*|Le parent utilise le mode OLAP multidimensionnel (MOLAP).|  
|*ROLAP*|Le parent utilise le mode OLAP relationnel (ROLAP).|  
|*HOLAP*|Le parent utilise le mode OLAP hybride (HOLAP).<br /><br /> Remarque : Cette valeur n’est pas valide pour [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md) éléments parents.|  
|*En mémoire*|Le parent utilise le stockage IMBI.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **StorageMode** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.StorageMode>.  
  
 Les éléments qui correspondent aux parents de **StorageMode** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, et <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

