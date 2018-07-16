---
title: Fichiers, élément (ASSL) | Microsoft Docs
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
- Files Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Files
helpviewer_keywords:
- Files element
ms.assetid: 8a1327cb-1f60-42a7-b8ef-213d45a63e55
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d4ed9199f5b715c00e70da39e1742a2638cf67a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196039"
---
# <a name="files-element-assl"></a>Élément Files (ASSL)
  Contient la collection de [fichier](../objects/file-element-assl.md) éléments qui composent un [ClrAssembly](../data-type/assembly-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Assembly xsi:type="ClrAssembly">  
   ...  
   <Files>  
      <File xsi:type="ClrAssemblyFile">...</File>  
   </Files>  
   ...  
</Assembly>  
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
|Éléments parents|[Assembly](../objects/assembly-element-assl.md) de type [ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|Éléments enfants|[Fichier](../objects/file-element-assl.md) de type [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ClrAssemblyFileCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de serveur &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Élément de base de données &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Élément Assemblies &#40;ASSL&#41;](assemblies-element-assl.md)   
 [Élément de données &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Type de données DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Bloque l’élément &#40;ASSL&#41;](blocks-element-assl.md)   
 [Bloquer l’élément &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Type de données ComAssembly &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
