---
title: Bloque l’élément (ASSL) | Documents Microsoft
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
- Blocks Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Blocks
helpviewer_keywords:
- Blocks element
ms.assetid: d6fd4e6b-b5bd-43cd-9c28-48af57cf977c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bf944cc053e7a8c32efec50d10f6cc176942cce1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043941"
---
# <a name="blocks-element-assl"></a>Élément Blocks (ASSL)
  Contient la collection de blocs de données binaires qui représentent le contenu binaire d’un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Data xsi:type="DataBlock">  
   ...  
   <Blocks>  
      <Block>...</Block>  
   </Blocks>  
   ...  
</File>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Données](../objects/data-element-assl.md) de type [DataBlock](../data-type/datablock-data-type-assl.md)|  
|Éléments enfants|[bloc](../objects/block-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `Blocks` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Type de données ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Fichiers d’élément &#40;ASSL&#41;](files-element-assl.md)   
 [Élément de fichier &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Type de données ClrAssemblyFile &#40;ASSL&#41;](../data-type/clrassemblyfile-data-type-assl.md)   
 [Élément de données &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Type de données DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Élément Blocks](blocks-element-assl.md)   
 [Bloquer l’élément &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  