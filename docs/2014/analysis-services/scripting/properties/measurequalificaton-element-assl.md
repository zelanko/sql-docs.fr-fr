---
title: Élément Measurequalification (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureQualificaton Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MeasureQualification element
ms.assetid: 754a037c-f20b-4717-a6e8-12f495e8e3b4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aff36cad69d59b7effa51ac9ab3e32490931f779
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48123329"
---
# <a name="measurequalificaton-element-assl"></a>Élément MeasureQualification (ASSL)
  Détermine si un préfixe est appliqué aux mesures dans le [MeasureGroup](../objects/group-element-assl.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroup>  
   ...  
   <MeasureQualification>...</MeasureQualification>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Aucun*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Groupe de mesures](../objects/group-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Aucun préfixe n'est appliqué aux mesures dans ce groupe de mesures.|  
|*PrefixMeasureGroup*|Le nom unique et la légende de chaque mesure dans ce groupe de mesures contient pour préfixe le nom du groupe de mesures suivi d'un espace unique.|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `MeasureQualification` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de cube &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Dimension élément &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Élément MeasureGroup &#40;ASSL&#41;](../objects/group-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
