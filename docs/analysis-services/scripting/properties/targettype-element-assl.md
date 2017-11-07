---
title: "Élément TargetType (ASSL) | Documents Microsoft"
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
- TargetType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TargetType
helpviewer_keywords:
- TargetType element
ms.assetid: 2c69ea6e-2af7-435b-9841-86117d5554a7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 49c2fd13925130bfb76730708775f6bb0d5e79ca
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="targettype-element-assl"></a>Élément TargetType (ASSL)
  Identifie le type d’élément de l’élément identifié dans le [cible](../../../analysis-services/scripting/properties/target-element-assl.md) élément.  
  
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
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Action](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Cube*|Un cube est la cible de l'action.|  
|*Cellules*|Un sous-cube est la cible de l'action.|  
|*Ensemble*|Un ensemble est la cible de l'action.|  
|*Hierarchy*|Une hiérarchie est la cible de l'action.|  
|*Level*|Un niveau est la cible de l'action.|  
|*DimensionMembers*|Les membres d'une dimension sont la cible de l'action.|  
|*HierarchyMembers*|Les membres d'une hiérarchie sont la cible de l'action.|  
|*LevelMembers*|Les membres d'un niveau sont la cible de l'action.|  
|*AttributeMembers*|Les membres d'un attribut sont la cible de l'action.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **TargetType** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ActionTargetType>.  
  
 L’élément qui correspond au parent de **TargetType** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

