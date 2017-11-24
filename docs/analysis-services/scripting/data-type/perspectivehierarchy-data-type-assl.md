---
title: "Type de données PerspectiveHierarchy (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
apiname: PerspectiveHierarchy Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: PerspectiveHierarchy
helpviewer_keywords: PerspectiveHierarchy data type
ms.assetid: 30366bd0-ee1c-4940-8c1f-ca5e0dd5fe4b
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2b63eccbc3f380d8224d0375ee357f07713b802a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="perspectivehierarchy-data-type-assl"></a>Type de données PerspectiveHierarchy (ASSL)
  Définit un type de données primitif qui représente des informations sur une hiérarchie dans un [PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<PerspectiveHierarchy>  
   <HierarchyID>...</HierarchyID>  
      <Annotations>...</Annotations>  
</PerspectiveHierarchy>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|Aucune|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [HierarchyID](../../../analysis-services/scripting/properties/hierarchyid-element-assl.md)|  
|Éléments dérivés|[Hiérarchie](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) ([hiérarchies](../../../analysis-services/scripting/collections/hierarchies-element-assl.md) collection de [PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.PerspectiveHierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
