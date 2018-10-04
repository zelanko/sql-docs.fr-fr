---
title: Columns (élément) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Columns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- COLUMNS
helpviewer_keywords:
- Columns element
ms.assetid: 14011eed-6f10-4120-b256-d599d59bde80
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 16e8d446b3ffeb4895bde76a739d7ec63a01337d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131509"
---
# <a name="columns-element-assl"></a>Élément Columns (ASSL)
  Contient la collection de colonnes associée à l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action xsi:type="DrillThroughAction"> <!-- or one of the elements listed below in the Element Relationships table -->  
   <Columns>  
      <Column xsi:type="MeasureBinding">...</Column> <!-- parent: DrillThroughAction -->  
      <!-- or -->  
      <Column xsi:type="CubeAttributeBinding">...</Column> <!-- parent: DrillThroughAction -->  
      <!-- or -->  
      <Column xsi:type="EventColumn">...</Column> <!-- parent: Event -->  
      <!-- or -->  
      <Column xsi:type="MiningModelColumn">...</Column> <!-- parent: MiningModel or MiningModelColumn -->  
      <!-- or -->  
      <Column xsi:type="MiningStructureColumn">...</Column> <!-- parent: MiningStructure or TableMiningStructureColumn -->  
   </Columns>  
</DrillThroughAction>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
  
|Ancêtre ou parent|Cardinalité|  
|------------------------|-----------------|  
|[Événement](../objects/event-element-assl.md)|1-1 : élément requis qui apparaît une fois et une seule.|  
|Autres|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Action](../objects/action-element-assl.md) de type [DrillThroughAction](../data-type/action-data-type-assl.md), [événement](../objects/event-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [ MiningStructure](../objects/miningstructure-element-assl.md), [TableMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
  
|Ancêtre ou parent|Éléments enfants|  
|------------------------|--------------------|  
|[DrillThroughAction](../data-type/binding-data-type-assl.md) ou [MeasureBinding](../data-type/measurebinding-data-type-assl.md)|  
|[Événement](../data-type/eventcolumn-data-type-assl.md)|  
|[MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md), [TableMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Pour `DrillThroughAction` éléments, le `Columns` collection identifie les colonnes qui contiennent des données qui doivent être retournées lorsque l’action est effectuée.  
  
 Pour `TableMiningStructureColumn` éléments, le `Columns` collection ne permet qu’un seul niveau de récursivité. En d’autres termes, un `TableMiningStructureColumn` élément inclus dans cette collection ne peut contenir aucun `TableMiningStructureColumn` éléments dans son `Columns` collection.  
  
 Certains des éléments correspondants dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.TraceColumnCollection>, <xref:Microsoft.AnalysisServices.MiningModelColumnCollection> et <xref:Microsoft.AnalysisServices.MiningStructureColumnCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
