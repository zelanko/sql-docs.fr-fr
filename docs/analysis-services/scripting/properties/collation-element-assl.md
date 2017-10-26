---
title: "Élément Collation (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Collation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Collation
helpviewer_keywords:
- Collation element
ms.assetid: 9b6dbe19-543e-43e6-abe9-1e8b4dfaa275
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d6d76943f405e883ec361868f9492fc1485f9222
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="collation-element-assl"></a>Élément Collation (ASSL)
  Détermine le classement utilisé par l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Database> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Collation>...</Collation>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), [base de données](../../../analysis-services/scripting/objects/database-element-assl.md), [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md), [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La chaîne **Collation** se compose de l'indicateur de paramètres régionaux (LCID) et de l'indicateur de comparaison séparés par un caractère de soulignement. Par exemple, Latin1_General_CI_AS est une chaîne acceptable.  
  
 Les éléments qui correspondent aux parents de **classement** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataItem>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MiningModel>, et <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

