---
title: "Condition d’élément (ASSL) | Documents Microsoft"
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
- Condition Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- condition
helpviewer_keywords:
- Condition element
ms.assetid: 9c3cb31c-4aa1-49e4-aeb2-6cab54db0be3
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0f979f051615ef44f713b93736ca20a8913d7bce
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="condition-element-assl"></a>Élément Condition (ASSL)
  Contient une expression MDX (Multidimensional Expressions) qui détermine si le [Action](../../../analysis-services/scripting/objects/action-element-assl.md) élément parent s’applique à la cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action>  
   ...  
   <Condition>...</Condition  
      ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Action](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L'élément **Condition** contient une expression MDX qui correspond à une valeur booléenne. Si l’expression retourne **True**, puis le **Action** s’applique à la cible spécifiée dans le [cible](../../../analysis-services/scripting/properties/target-element-assl.md) élément. Dans le cas contraire, l'élément **Action** ne peut s'appliquer.  
  
 L’élément qui correspond au parent de **Condition** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

