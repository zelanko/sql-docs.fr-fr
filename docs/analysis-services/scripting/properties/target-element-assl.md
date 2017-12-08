---
title: "Cible de l’élément (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Target Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Target
helpviewer_keywords: Target element
ms.assetid: 08ce0441-94b6-4f1d-acba-f31c8212cb79
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1d4f0334fde6506dbb5630fc1dc47efe88a5d48a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="target-element-assl"></a>Élément Target (ASSL)
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
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
