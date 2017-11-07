---
title: "Type de données CubeAttribute (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CubeAttribute Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c04b5602de94ac46b736ebfc878760174ced5a8d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="cubeattribute-data-type-assl"></a>Type de données CubeAttribute (ASSL)
  Définit un type de données primitif qui représente un attribut associé avec un [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeAttribute>  
   <AttributeID>...</AttributeID>  
   <AggregationUsage>...</AggregationUsage>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <Annotations>...</Annotations>  
</CubeAttribute>  
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
|Éléments enfants|[AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md), [AttributeHierarchyOptimizedState](../../../analysis-services/scripting/properties/attributehierarchyoptimizedstate-element-assl.md), [AttributeHierarchyVisible](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md), [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)|  
|Éléments dérivés|[Attribut](../../../analysis-services/scripting/objects/attribute-element-assl.md) ([attributs](../../../analysis-services/scripting/collections/attributes-element-assl.md) collection de [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Le *AttributeHierarchyOptimizedState* élément n’est pas pris en charge lors de l’exécution du service dans les valeurs de propriété de configuration DeploymentMode de 1 ou 2 (modes SharePoint ou tabulaire, utilisés pour exécuter [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] et bases de données model tabulaire).  
  
 Un attribut ne peut pas être ajouté en tant que niveau d’une hiérarchie lorsque la propriété *AtttributeHierarchyEnabled*, est définie sur FALSE et l’instance est sous DeploymentMode 1 ou 2 (mode de serveur SharePoint ou tabulaire).  
  
 Les attributs dans le [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md) élément qui ne sont pas inclus explicitement dans le [attributs](../../../analysis-services/scripting/collections/attributes-element-assl.md) dans collection devienne la collection avec les valeurs par défaut affectée à ceux-ci. Une fois les attributs sont ajoutés à la collection, les attributs peuvent être retournées par la [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) (méthode).  
  
 Le [AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md) contrôles d’élément comment [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crée automatiquement des agrégations pour l’attribut. Le **AggregationUsage** élément ne contrainte pas toutes les agrégations sont créées manuellement pour le cube.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

