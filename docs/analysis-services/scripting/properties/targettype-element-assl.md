---
title: Élément TargetType (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5261d212777049c907af8d4db8f3b085ded8740e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="targettype-element-assl"></a>Élément TargetType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|*Hiérarchie*|Une hiérarchie est la cible de l'action.|  
|*Level*|Un niveau est la cible de l'action.|  
|*DimensionMembers*|Les membres d'une dimension sont la cible de l'action.|  
|*HierarchyMembers*|Les membres d'une hiérarchie sont la cible de l'action.|  
|*LevelMembers*|Les membres d'un niveau sont la cible de l'action.|  
|*AttributeMembers*|Les membres d'un attribut sont la cible de l'action.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **TargetType** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ActionTargetType>.  
  
 L’élément qui correspond au parent de **TargetType** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
