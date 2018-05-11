---
title: Cible de l’élément (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 796d81ddb3c2d56f8efd25b9df194a2e4d942be5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="target-element-assl"></a>Élément Target (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifie la cible de la [Action](../../../analysis-services/scripting/objects/action-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action>  
   ...  
   <Target>...</Target>  
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
 La valeur attendue de cet élément dépend de la valeur de la [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) élément parent **Action**. Le tableau suivant décrit les valeurs attendues de **Target** en fonction de la valeur de **TargetType**.  
  
|Valeur de TargetType|Valeur attendue|  
|----------------------|--------------------|  
|*Cube*|Nom d'un cube.|  
|*Cellules*|Expression de sous-cube.|  
|*Ensemble*|Expression d'ensemble ou nom d'un jeu nommé.<br /><br /> Remarque : Une instruction de sous-sélection ne peut pas être utilisée.|  
|*Hiérarchie, HierarchyMembers*|Nom d'une hiérarchie.|  
|*Dimension, DimensionMembers*|Nom d'une dimension.|  
|*Niveau de LevelMembers*|Nom d'un niveau.|  
|*Attribut, AttributeMembers*|Nom d'un attribut.|  
  
 L’élément qui correspond au parent de **cible** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
