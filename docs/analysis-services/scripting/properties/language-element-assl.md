---
title: "Élément de langage (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Language Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: LANGUAGE
helpviewer_keywords: Language element
ms.assetid: 4d745d23-6b1f-4a85-97cf-d034cc41356f
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ac4036b7ce722d716b82550b77a8778c31c766b7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="language-element-assl"></a>Élément Language (ASSL)
  Contient l'identificateur de langue de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube> <!-- or Database, Dimension, MiningModel, MiningStructure, Translation -->  
   ...  
   <Language>...</Language>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|Aucune|  
|Cardinalité|Consultez le tableau ci-dessous.|  
  
|Ancêtre ou parent|Cardinalité|  
|------------------------|-----------------|  
|[Traduction](../../../analysis-services/scripting/objects/translation-element-assl.md)|1-1 : élément requis qui apparaît une fois et une seule.|  
|Autres|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), [base de données](../../../analysis-services/scripting/objects/database-element-assl.md), [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [traduction](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **langage** élément contient l’identificateur de langue par défaut qui est utilisé par l’élément parent, ou l’identificateur de langue spécifique pour un **traduction** élément. La langue doit être définie en utilisant des codes d'identificateur de paramètres régionaux (LCID). Par exemple, LCID 1033 est utilisé pour indiquer la langue anglaise (États-Unis).  
  
 Les éléments qui correspondent aux parents de la **langage** élément dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure>, et <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
