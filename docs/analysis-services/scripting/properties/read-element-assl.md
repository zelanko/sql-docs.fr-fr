---
title: "Lire l’élément (ASSL) | Documents Microsoft"
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
- Read Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Read element
ms.assetid: 2e2c1173-72ca-4e8a-a6cd-fd348ef96d78
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aff524460850c6e875f5e703f5bbc065fc5ad50a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="read-element-assl"></a>Élément Read (ASSL)
  Détermine si les données ou les métadonnées peuvent être lues pour un donné [CubeDimensionPermission](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md) ou [autorisation](../../../analysis-services/scripting/data-type/permission-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Read>...</Read>  
   ...  
</CubeDimensionPermission>  
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
|Éléments parents|[CubeDimensionPermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [autorisation](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Aucun accès aux données ou métadonnées de l'objet parent n'est autorisé.|  
|*Autorisé*|Un accès en lecture aux données et métadonnées de l'objet parent est autorisé.|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de **en lecture** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.CubeDimensionPermission> et <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément cube &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Élément dimension &#40; ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Élément CubePermission &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)   
 [Type de données d’autorisation &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

