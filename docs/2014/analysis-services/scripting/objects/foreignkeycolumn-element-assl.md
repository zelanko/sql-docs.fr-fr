---
title: Élément ForeignKeyColumn (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ForeignKeyColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ForeignKeyColumn
helpviewer_keywords:
- ForeignKeyColumn element
ms.assetid: 6c00dcc6-8d5b-4293-8b72-c7a22e298c8d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f4688ac6efd03e10b5950abcbcc0da99a1cbc5b6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149789"
---
# <a name="foreignkeycolumn-element-assl"></a>Élément ForeignKeyColumn (ASSL)
  Identifie la jointure à une table parente pour une source de données relationnelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ForeignKeyColumns>  
   <ForeignKeyColumn xsi:type="DataItem">...</ForeignKeyColumn>  
</ForeignKeyColumns>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ForeignKeyColumns](../collections/columns-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `DataItem` type, notamment un tableau des objets d’Analysis Services Scripting Language (ASSL) et les propriétés de la `DataItem` de type, consultez [Type de données DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 L'élément qui correspond au parent de la collection `ForeignKeyColumns` dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données TableMiningStructureColumn &#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [Type de données MiningStructureColumn &#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [Élément MiningStructure &#40;ASSL&#41;](miningstructure-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
