---
title: Élément RefreshPolicy (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RefreshPolicy Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RefreshPolicy
helpviewer_keywords:
- RefreshPolicy element
ms.assetid: f4c36280-1a39-4f1c-a3ab-fbeb81742d6d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6322c725a0c4b339425b9cc9e10aa6596c9fc34c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144429"
---
# <a name="refreshpolicy-element-assl"></a>Élément RefreshPolicy (ASSL)
  Détermine la fréquence à laquelle la partie dynamique de la dimension ou groupe de mesures (comme spécifié par le [persistance](persistence-element-assl.md) élément) est activée pour les modifications.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <RefreshPolicy>...</RefreshPolicy>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
|Ancêtre ou parent|Valeur par défaut|  
|------------------------|-------------------|  
|[DimensionBinding](../data-type/binding-data-type-assl.md)|*ByQuery*|  
|[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|None|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DimensionBinding](../data-type/binding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*ByQuery*|Chaque requête procède à une vérification pour savoir si les données sources ont été modifiées.|  
|*ByInterval*|Source de données est activée uniquement pour les modifications à l’intervalle spécifié par [RefreshInterval](refreshinterval-element-assl.md).|  
  
 L’énumération qui correspond aux valeurs autorisées pour `RefreshPolicy` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.RefreshPolicy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Persistence &#40;ASSL&#41;](persistence-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
