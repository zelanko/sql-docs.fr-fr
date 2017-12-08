---
title: "Élément DataSourceViewID (ASSL) | Documents Microsoft"
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
apiname: DataSourceViewID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DataSourceViewID
helpviewer_keywords: DataSourceViewID element
ms.assetid: dcf617fe-0bf6-4767-af35-07c0c7fd96e5
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 64aa61d22ba55ef2e44d6631fc6b1b1d0df471c4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
  
  
