---
title: Élément DataAggregation (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataAggregation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataAggregation element
ms.assetid: baf6d2c9-54f6-4a6d-95f7-e1e758be458d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 01a86977cc6ebf85d004bf235b6d47a354e112a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134819"
---
# <a name="dataaggregation-element-assl"></a>Élément DataAggregation (ASSL)
  Détermine si l’instance peut agréger des données persistantes ou des données mises en cache pour le [MeasureGroup](../objects/group-element-assl.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroup>  
   ...  
   <DataAggregation>...</DataAggregation>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*DataAndCacheAggregatable*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Groupe de mesures](../objects/group-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|L'agrégation n'a pas lieu pour ce groupe de mesures.|  
|*DataAggregatable*|Les données persistantes peuvent être agrégées pour ce groupe de mesures.|  
|*CacheAggregatable*|Les données en cache peuvent être agrégées pour ce groupe de mesures.|  
|*DataAndCacheAggregatable*|Les données persistantes et les données en cache à la fois peuvent être agrégées pour ce groupe de mesures.|  
  
 L’élément qui correspond au parent de `DataAggregation` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de cube &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Dimension élément &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
