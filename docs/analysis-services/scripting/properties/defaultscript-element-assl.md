---
title: "Élément DefaultScript (ASSL) | Documents Microsoft"
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
apiname: DefaultScript Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DefaultScript
helpviewer_keywords: DefaultScript element
ms.assetid: 60716e63-2d64-4774-9ac9-253efe612fa5
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 72a8171e9dedf77983c685d3081a0525a1d4015c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="defaultscript-element-assl"></a>Élément DefaultScript (ASSL)
  Identifie la valeur par défaut [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md) élément dans le [MdxScripts](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MdxScript>  
   ...  
   <DefaultScript>...</DefaultScript>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|**True**|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L'attribution à **DefaultScript** de la valeur **True** pour un script affecte à **DefaultScript** la valeur **False** pour tous les autres éléments **MdxScript** de la collection **MdxScripts** .  
  
 L’élément qui correspond au parent de **DefaultScript** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MdxScript>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
