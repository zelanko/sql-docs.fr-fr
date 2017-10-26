---
title: "Élément KpiID (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- KpiID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- KpiID
helpviewer_keywords:
- KpiID element
ms.assetid: a76395bc-bc84-40f8-9770-6275842f93b5
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c464e68cab5ba1f4e9ae87b6ae11fb185068373e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="kpiid-element-assl"></a>Élément KpiID (ASSL)
  Contient un identificateur (ID) qui associe un [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md) élément avec un [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<PerspectiveKpi>  
      ...  
   <KpiID>...</KpiID>  
   ...  
</PerspectiveKpi>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[PerspectiveKpi](../../../analysis-services/scripting/data-type/perspectivekpi-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **KpiID** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.PerspectiveKpi>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés (ASSL)](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

