---
title: Bloquer l’élément (ASSL) | Microsoft Docs
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
- Block Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Block
helpviewer_keywords:
- Block element
ms.assetid: f45c32ae-e4e0-465a-9564-9ccfb10a858f
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 44022a2e0bd538b7f4b33b0d1f1fb7b462e676e6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279435"
---
# <a name="block-element-assl"></a>Élément Block (ASSL)
  Contient tout ou partie du contenu binaire d’un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Blocks>  
   <Block>...</Block>  
</Blocks>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Base64Binary|  
|Valeur par défaut|None|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Blocs](../collections/blocks-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément assembly &#40;ASSL&#41;](assembly-element-assl.md)   
 [Type de données ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Fichiers d’élément &#40;ASSL&#41;](../collections/files-element-assl.md)   
 [Fichier d’élément &#40;ASSL&#41;](file-element-assl.md)   
 [Type de données ClrAssemblyFile &#40;ASSL&#41;](../data-type/clrassemblyfile-data-type-assl.md)   
 [Élément de données &#40;ASSL&#41;](data-element-assl.md)   
 [Type de données DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
