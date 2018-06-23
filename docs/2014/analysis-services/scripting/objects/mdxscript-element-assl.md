---
title: Élément MdxScript (ASSL) | Documents Microsoft
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
- MdxScript Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MdxScript
helpviewer_keywords:
- MdxScript element
ms.assetid: 0c59a550-dc95-4d50-948a-bb99348bdd86
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 81d83e2d179e5a16d17cc6988b209f348dbc2572
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141635"
---
# <a name="mdxscript-element-assl"></a>Élément MdxScript (ASSL)
  Contient des informations sur un script MDX (Multidimensional Expressions) qui est associé à un [Cube](cube-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MdxScripts>  
   <MdxScript>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Annotations>...</Annotations>  
      <Commands>...</Commands>  
      <DefaultScript>...</DefaultScript>  
      <CalculationProperties>...</CalculationProperties>  
   </MdxScript>  
</MdxScripts>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[MdxScripts](../collections/mdxscripts-element-assl.md)|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [CalculationProperties](../collections/calculationproperties-element-assl.md), [commandes](../collections/commands-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DefaultScript](../properties/defaultscript-element-assl.md), [Description](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [nom](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément `DefaultScript` d'un script a par défaut la valeur `True`. Si vous affectez à l'élément `DefaultScript` la valeur `True` pour un script particulier, l'élément `DefaultScript` adopte la valeur `False` pour tous les autres scripts.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MdxScript>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  