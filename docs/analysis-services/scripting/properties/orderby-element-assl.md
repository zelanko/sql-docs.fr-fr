---
title: "Élément OrderBy (ASSL) | Documents Microsoft"
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
- OrderBy Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- OrderBy
helpviewer_keywords:
- OrderBy element
ms.assetid: d7a0564b-430e-44eb-913a-fe1f98917d0f
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 35479ebb898200c9082a7e08369a3ae5d4c57ac3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="orderby-element-assl"></a>Élément OrderBy (ASSL)
  Décrit comment classer les membres contenus dans l'attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderBy>...</OrderBy>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Nom*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Nom*|Classement d'après le nom de membre.|  
|*Clé*|Classement d'après la clé de membre.|  
|*AttributeKey*|Trier par la clé de membre de l’attribut spécifié dans le [OrderByAttributeID](../../../analysis-services/scripting/properties/orderbyattributeid-element-assl.md) élément de **DimensionAttribute**.|  
|*AttributeName*|Classement d'après le nom de membre de l'attribut spécifié dans l'élément **OrderByAttributeID** de **DimensionAttribute**.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **OrderBy** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.OrderBy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
