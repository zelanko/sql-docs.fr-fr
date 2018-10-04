---
title: Élément DefaultScript (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DefaultScript Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultScript
helpviewer_keywords:
- DefaultScript element
ms.assetid: 60716e63-2d64-4774-9ac9-253efe612fa5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a1eef79aabede1198c45c9f5481f13bd597db42c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152739"
---
# <a name="defaultscript-element-assl"></a>Élément DefaultScript (ASSL)
  Identifie la valeur par défaut [MdxScript](../objects/mdxscript-element-assl.md) élément dans le [MdxScripts](../collections/mdxscripts-element-assl.md) collection.  
  
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
|Valeur par défaut|`True`|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[MdxScript](../objects/mdxscript-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'attribution à `DefaultScript` de la valeur `True` pour un script affecte à `DefaultScript` la valeur `False` pour tous les autres éléments `MdxScript` de la collection `MdxScripts`.  
  
 L’élément qui correspond au parent de `DefaultScript` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MdxScript>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
