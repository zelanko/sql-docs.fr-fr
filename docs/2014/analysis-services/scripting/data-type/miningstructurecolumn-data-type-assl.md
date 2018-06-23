---
title: Type de données MiningStructureColumn (ASSL) | Documents Microsoft
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
- MiningStructureColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructureColumn
helpviewer_keywords:
- MiningStructureColumn data type
ms.assetid: b6d6e7a5-9c48-40c4-b147-8fcd5e429ae3
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1b1fc3d4f25bb5aa261179904939a271774de446
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043000"
---
# <a name="miningstructurecolumn-data-type-assl"></a>Type de données MiningStructureColumn (ASSL)
  Définit un type de données primitif abstrait qui représente des informations sur une colonne dans un [MiningStructure](../objects/miningstructure-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructureColumn>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <Type>...</Type>  
   <Annotations>...</Annotations>  
</MiningStructureColumn>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md), [TableMiningStructureColumn](tableminingstructurecolumn-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|None|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [Description](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [nom](../properties/name-element-assl.md), [Type](../properties/type-element-miningstructurecolumn-assl.md)|  
|Éléments dérivés|[Colonne](../objects/column-element-assl.md) ([colonnes](../collections/columns-element-assl.md) collection de [MiningStructure](../objects/miningstructure-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  