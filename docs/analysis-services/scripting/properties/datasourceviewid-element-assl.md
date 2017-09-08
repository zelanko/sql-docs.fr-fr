---
title: "Élément DataSourceViewID (ASSL) | Documents Microsoft"
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
- DataSourceViewID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DataSourceViewID
helpviewer_keywords:
- DataSourceViewID element
ms.assetid: dcf617fe-0bf6-4767-af35-07c0c7fd96e5
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ecf937676d947103f6ad5e8a5d327592e0fb69d4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="datasourceviewid-element-assl"></a>Élément DataSourceViewID (ASSL)
  Identifie la [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md) élément associé à la [liaison](../../../analysis-services/scripting/data-type/binding-data-type-assl.md) élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataSourceViewBinding> <!-- or DSVTableBinding -->  
   ...  
   <DataSourceViewID>...</DataSourceViewID>  
   ...  
</DataSourceViewBinding>  
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
|Élément parent|[DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md), [DSVTableBinding](../../../analysis-services/scripting/data-type/dsvtablebinding-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de **DataSourceViewID** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.DataSourceViewBinding> et <xref:Microsoft.AnalysisServices.DSVTableBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
