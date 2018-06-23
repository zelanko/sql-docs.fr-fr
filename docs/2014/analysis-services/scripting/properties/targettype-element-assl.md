---
title: Élément TargetType (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TargetType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TargetType
helpviewer_keywords:
- TargetType element
ms.assetid: 2c69ea6e-2af7-435b-9841-86117d5554a7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e4a36c4ca0e38fe00990f2185685205840eafc66
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142566"
---
# <a name="targettype-element-assl"></a>Élément TargetType (ASSL)
  Identifie le type d’élément de l’élément identifié dans le [cible](target-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action>  
   ...  
   <TargetType>...</TargetType>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Action](../objects/action-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Cube*|Un cube est la cible de l'action.|  
|*Cellules*|Un sous-cube est la cible de l'action.|  
|*ensemble*|Un ensemble est la cible de l'action.|  
|*Hierarchy*|Une hiérarchie est la cible de l'action.|  
|*Level*|Un niveau est la cible de l'action.|  
|*DimensionMembers*|Les membres d'une dimension sont la cible de l'action.|  
|*HierarchyMembers*|Les membres d'une hiérarchie sont la cible de l'action.|  
|*LevelMembers*|Les membres d'un niveau sont la cible de l'action.|  
|*AttributeMembers*|Les membres d'un attribut sont la cible de l'action.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `TargetType` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ActionTargetType>.  
  
 L’élément qui correspond au parent de `TargetType` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  