---
title: Élément IsDefaultMeasure (XML) | Documents Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 523cf3d7-9df0-4f9d-8486-9109de8d3cca
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3739cf8669385a6f60a5141f53566599da285569
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="isdefaultmeasure-element-xml"></a>Élément IsDefaultMeasure (XML)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Indique qu'il est possible d'obtenir la mesure par défaut de cette entité en parcourant cette relation jusqu'à l'autre table et en extrayant le membre ayant l'attribut DefaultMeasure.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultMeasure>...</IsDefaultMeasure>  
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
 Pour **RelationshipEndVisualizationProperties** éléments, le **IsDefaultMeasure** élément indique qu’il est possible d’obtenir la mesure par défaut pour cette entité en accédant à l’autre extrémité de cette relation. La valeur par défaut **false** indique il n’existe aucune mesure par défaut doit être obtenu.  
  
  
