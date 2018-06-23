---
title: Type de données ClrAssemblyFile (ASSL) | Documents Microsoft
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
- ClrAssemblyFile Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClrAssemblyFile
helpviewer_keywords:
- ClrAssemblyFile data type
ms.assetid: 91074677-c149-483b-a56d-0e35d959d9eb
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b542c4193d80fa80cc9aed6663f41e102266000b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041481"
---
# <a name="clrassemblyfile-data-type-assl"></a>Type de données ClrAssemblyFile (ASSL)
  Définit un type de données primitif qui représente un des fichiers qui composent un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] `Assembly` ([ClrAssembly](assembly-data-type-assl.md) élément).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ClrAssemblyFile>  
   <Name>...</Name>  
      <Type>...</Type>  
      <Data>...</Data>  
</ClrAssemblyFile>  
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
|Éléments enfants|[Données](../objects/data-element-assl.md), [nom](../properties/name-element-assl.md), [Type](../properties/type-element-clrassemblyfile-assl.md)|  
|Éléments dérivés|[Fichier](../objects/file-element-assl.md) ([fichiers](../collections/files-element-assl.md) collection de [ClrAssembly](assembly-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément serveur &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Élément de base de données &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Élément Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Élément assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Type de données DataBlock &#40;ASSL&#41;](datablock-data-type-assl.md)   
 [Bloque l’élément &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Bloquer l’élément &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Type de données ComAssembly &#40;ASSL&#41;](comassembly-data-type-assl.md)   
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  