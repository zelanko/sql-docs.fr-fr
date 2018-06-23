---
title: Élément TableID (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TableID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableID
helpviewer_keywords:
- TableID element
ms.assetid: 45fe7e23-b274-4bc2-be63-1a5bb6680f51
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9b8f85ee3fecac1b098a16afe6cf2d0eca61226b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154920"
---
# <a name="tableid-element-assl"></a>Élément TableID (ASSL)
  Contient l’identificateur (ID) de la table (à partir de la [DataSourceView](../objects/datasourceview-element-assl.md) élément) associé à l’élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ColumnBinding> <!-- or DSVTableBinding, RowBinding, IncrementalProcessingNotification -->  
   ...  
   <TableID>...</TableID>  
   ...  
</ColumnBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ColumnBinding](../data-type/binding-data-type-assl.md), [DSVTableBinding](../data-type/tablebinding-data-type-assl.md), [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md), [RowBinding](../data-type/rowbinding-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La table identifiée par `TableID` doit être dans la source de données à laquelle l'objet propriétaire (dimension ou cube) est lié.  
  
 Les éléments qui correspondent aux parents de `TableID` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.ColumnBinding>, <xref:Microsoft.AnalysisServices.DSVTableBinding>, <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification> et <xref:Microsoft.AnalysisServices.RowBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  