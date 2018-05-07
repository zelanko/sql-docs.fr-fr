---
title: Type de données CubeHierarchy (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d6603101210d6b965dd6be35ec1c5b312048199b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="cubehierarchy-data-type-assl"></a>Type de données CubeHierarchy (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Définit un type de données primitif qui représente les informations concernant un [hiérarchie](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) élément dans une [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CubeHierarchy>   <HierarchyID>...</HierarchyID>   <Name>...</Name>   <OptimizedState>...</OptimizedState>   <Visible>...</Visible>   <Enabled>...</Enabled>   <Annotations>...</Annotations></CubeHierarchy>  
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
|Éléments enfants|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [activé](../../../analysis-services/scripting/properties/enabled-element-assl.md), [HierarchyID](../../../analysis-services/scripting/properties/hierarchyid-element-assl.md), [nom](../../../analysis-services/scripting/properties/name-element-assl.md), [OptimizedState](../../../analysis-services/scripting/properties/optimizedstate-element-assl.md), [Visible](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
|Éléments dérivés|[Hiérarchie](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) ([hiérarchies](../../../analysis-services/scripting/collections/hierarchies-element-assl.md) collection de [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Ce type de données n'a pas de restrictions et peut être utilisé selon n'importe quel mode de déploiement : 0 - Multidimensionnel et d'exploration de données, 1 - SharePoint et 2 - Tabulaire.  
  
 Dans SQL Server 2016 Analysis Services et versions ultérieures, le *activé* propriété ne peut pas être définie sur **False** pour *CubeHierarchy*.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CubeHierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Discover &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Analysis Services script des Types de données XML Language & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
