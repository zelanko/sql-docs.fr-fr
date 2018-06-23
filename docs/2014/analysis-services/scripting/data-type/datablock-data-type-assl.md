---
title: Type de données DataBlock (ASSL) | Documents Microsoft
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
- DataBlock Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataBlock
helpviewer_keywords:
- DataBlock data type
ms.assetid: 4192b388-613a-472b-881c-f9c02215aa81
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 12cbd6c1a2723cfc0d9e5b68ff4a484878c82a74
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045050"
---
# <a name="datablock-data-type-assl"></a>Type de données DataBlock (ASSL)
  Définit un type de données primitif qui représente une collection de blocs de données utilisé pour stocker le contenu binaire d’un [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataBlock>  
   <Blocks>...</Blocks>  
</DataBlock>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Blocs](../collections/blocks-element-assl.md)|  
|Éléments dérivés|[Données](../objects/data-element-assl.md) élément de [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) type ([fichiers](../collections/files-element-assl.md) collection de [ClrAssembly](assembly-data-type-assl.md) type)|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Élément de fichier &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Bloquer l’élément &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  