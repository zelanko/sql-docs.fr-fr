---
title: Élément IsDefaultImage (XML) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e340755f5af06cc6b7c3b06fc5fa53975921b8e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="isdefaultimage-element-xml"></a>Élément IsDefaultImage (XML)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Indique qu'il est possible d'obtenir l'image par défaut de cette entité en parcourant cette relation jusqu'à l'autre table et en extrayant le membre ayant l'attribut IsDefaultImage.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultImage>...</IsDefaultImage>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|false|  
|Cardinalité|0-1 : élément facultatif qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[RelationshipEndVisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour **RelationshipEndVisualizationProperties** éléments, le **IsDefaultImage** élément indique que l’image par défaut pour cette entité peut être obtenu en accédant à l’autre extrémité de cette relation. La valeur par défaut **false** n’indique aucune image par défaut doit être obtenu.  
  
  
