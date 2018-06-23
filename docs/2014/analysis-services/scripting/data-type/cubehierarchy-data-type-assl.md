---
title: Type de données CubeHierarchy (ASSL) | Documents Microsoft
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
- CubeHierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeHierarchy
helpviewer_keywords:
- CubeHierarchy data type
ms.assetid: cd633409-0c14-4dd9-97cc-3d30e25df24f
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 48176b4096b7fa7ba8e1847750410be0f65da552
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139677"
---
# <a name="cubehierarchy-data-type-assl"></a>Type de données CubeHierarchy (ASSL)
  Définit un type de données primitif qui représente les informations concernant un [hiérarchie](../objects/hierarchy-element-assl.md) élément dans une [Cube](../objects/cube-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CubeHierarchy>   <HierarchyID>...</HierarchyID>   <Name>...</Name>   <OptimizedState>...</OptimizedState>   <Visible>...</Visible>   <Enabled>...</Enabled>   <Annotations>...</Annotations></CubeHierarchy>  
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
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [activé](../properties/enabled-element-assl.md), [HierarchyID](../properties/id-element-assl.md), [nom](../properties/name-element-assl.md), [OptimizedState](../properties/state-element-assl.md), [Visible](../properties/visible-element-assl.md)|  
|Éléments dérivés|[Hiérarchie](../objects/hierarchy-element-assl.md) ([hiérarchies](../collections/hierarchies-element-assl.md) collection de [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Ce type de données n'a pas de restrictions et peut être utilisé selon n'importe quel mode de déploiement : 0 - Multidimensionnel et d'exploration de données, 1 - SharePoint et 2 - Tabulaire.  
  
 Dans [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)], le *activé* propriété ne peut pas être définie sur `False` pour *CubeHierarchy*.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CubeHierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Discover &#40;XMLA&#41;](../../xmla/xml-elements-methods-discover.md)   
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  