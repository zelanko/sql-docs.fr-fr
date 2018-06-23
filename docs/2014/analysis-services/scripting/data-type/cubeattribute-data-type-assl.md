---
title: Type de données CubeAttribute (ASSL) | Documents Microsoft
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dce594145db99d7edfa991c2e975f62e55d3ef34
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045047"
---
# <a name="cubeattribute-data-type-assl"></a>Type de données CubeAttribute (ASSL)
  Définit un type de données primitif qui représente un attribut associé avec un [Cube](../objects/cube-element-assl.md) élément.  
  
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
  
 Un attribut ne peut pas être ajouté en tant que niveau d’une hiérarchie lorsque la propriété *AtttributeHierarchyEnabled*, est définie sur FALSE et l’instance est sous DeploymentMode 1 ou 2 (mode de serveur SharePoint ou tabulaire).  
  
 Les attributs dans le [CubeDimension](dimension-data-type-assl.md) élément qui ne sont pas inclus explicitement dans le [attributs](../collections/attributes-element-assl.md) dans collection devienne la collection avec les valeurs par défaut affectée à ceux-ci. Une fois les attributs sont ajoutés à la collection, les attributs peuvent être retournées par la [Discover](../../xmla/xml-elements-methods-discover.md) (méthode).  
  
 Le [AggregationUsage](../properties/aggregationusage-element-assl.md) contrôles d’élément comment [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crée automatiquement des agrégations pour l’attribut. L'élément `AggregationUsage` ne produit aucun effet sur les agrégations créées manuellement pour le cube.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  