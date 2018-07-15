---
title: Type de données CubeAttribute (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CubeAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b1df72c234fe7835d739e2b1835b01041aa9cbe6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319349"
---
# <a name="cubeattribute-data-type-assl"></a>Type de données CubeAttribute (ASSL)
  Définit un type de données primitif qui représente un attribut associé à un [Cube](../objects/cube-element-assl.md) élément.  
  
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
|Types de données de base|None|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[AggregationUsage](../properties/aggregationusage-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../properties/enabled-element-assl.md), [AttributeHierarchyOptimizedState](../properties/state-element-assl.md), [ AttributeHierarchyVisible](../properties/visible-element-assl.md), [AttributeID](../properties/id-element-assl.md)|  
|Éléments dérivés|[Attribut](../objects/attribute-element-assl.md) ([attributs](../collections/attributes-element-assl.md) collection de [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Le *AttributeHierarchyOptimizedState* élément n’est pas pris en charge lors de l’exécution le service de configuration DeploymentMode de 1 ou 2 (modes SharePoint ou tabulaire, utilisés pour exécuter PowerPivot et les bases de données model tabulaires), les valeurs de propriété.  
  
 Un attribut ne peut pas être ajouté en tant que niveau d’une hiérarchie lorsque la propriété, *AtttributeHierarchyEnabled*, est définie sur FALSE et l’instance s’exécute sous DeploymentMode 1 ou 2 (mode de serveur SharePoint ou tabulaire).  
  
 Attributs dans le [CubeDimension](dimension-data-type-assl.md) élément qui ne sont pas inclus explicitement dans le [attributs](../collections/attributes-element-assl.md) dans collection deviennent la collection avec les valeurs par défaut affectées. Une fois que les attributs sont ajoutés à la collection, les attributs peuvent être retournés par la [Discover](../../xmla/xml-elements-methods-discover.md) (méthode).  
  
 Le [AggregationUsage](../properties/aggregationusage-element-assl.md) contrôles d’élément comment [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crée automatiquement des agrégations pour l’attribut. L'élément `AggregationUsage` ne produit aucun effet sur les agrégations créées manuellement pour le cube.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
