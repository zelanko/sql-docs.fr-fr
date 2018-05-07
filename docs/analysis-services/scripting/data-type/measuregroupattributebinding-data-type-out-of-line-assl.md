---
title: Type de données MeasureGroupAttributeBinding (hors de ligne) (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 623de08bdac340eb3fadccb73c5e5f5c293afdd6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="measuregroupattributebinding-data-type-out-of-line-assl"></a>Type de données MeasureGroupAttributeBinding (hors ligne) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Définit un type de données dérivé qui représente une liaison hors ligne pour un attribut dans une dimension incluse dans un groupe de mesures.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroupAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <GranularityAttributeID>...</GranularityAttributeID>  
   <Source>...</Source>  
</MeasureGroupAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Liaison](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[CubeID](../../../analysis-services/scripting/properties/cubeid-element-assl.md), [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md), [MeasureGroupID](../../../analysis-services/scripting/properties/measuregroupid-element-assl.md), [GranularityAttributeID](../../../analysis-services/scripting/properties/granularityattributeid-element-assl.md), [Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
|Éléments dérivés|[Liaison](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md) ([liaisons](../../../analysis-services/scripting/collections/attributes-element-assl.md) collection de XML for Analysis (XMLA) [lot](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) et [processus](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) commandes)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les liaisons hors ligne, consultez [des Sources de données et liaisons & #40 ; SSAS multidimensionnel & #41 ; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
