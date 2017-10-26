---
title: "Élément Measurequalification (ASSL) | Documents Microsoft"
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
- MeasureQualificaton Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MeasureQualification element
ms.assetid: 754a037c-f20b-4717-a6e8-12f495e8e3b4
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 01bb9fa9dab28eafbe0cd833028c7eef451d9c3f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="measurequalificaton-element-assl"></a>Élément MeasureQualification (ASSL)
  Détermine si un préfixe est appliqué aux mesures dans le [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md).  
  
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
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Groupe de mesures](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Aucun préfixe n'est appliqué aux mesures dans ce groupe de mesures.|  
|*PrefixMeasureGroup*|Le nom unique et la légende de chaque mesure dans ce groupe de mesures contient pour préfixe le nom du groupe de mesures suivi d'un espace unique.|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **MeasureQualification** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément cube &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Élément dimension &#40; ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Élément MeasureGroup &#40; ASSL &#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

