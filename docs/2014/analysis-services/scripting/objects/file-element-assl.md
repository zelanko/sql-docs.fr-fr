---
title: Fichier de l’élément (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- File
helpviewer_keywords:
- File element
ms.assetid: 21c70707-d2f8-4040-9acb-cbce23076bcc
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 645882666ba82f965fddff9e1c886e97ff092a90
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042091"
---
# <a name="file-element-assl"></a>Élément File (ASSL)
  Définit un des fichiers qui composent un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [ClrAssembly](../data-type/assembly-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Files>  
   <File xsi:type="ClrAssemblyFile">...</File>  
</Files>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Fichiers](../collections/files-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `Files` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément serveur &#40;ASSL&#41;](server-element-assl.md)   
 [Élément de base de données &#40;ASSL&#41;](database-element-assl.md)   
 [Élément Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Élément assembly &#40;ASSL&#41;](assembly-element-assl.md)   
 [Type de données ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Élément de données &#40;ASSL&#41;](data-element-assl.md)   
 [Type de données DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Bloque l’élément &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Bloquer l’élément &#40;ASSL&#41;](block-element-assl.md)   
 [Type de données ComAssembly &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  