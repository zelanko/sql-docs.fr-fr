---
title: Élément de données (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Data Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Data
helpviewer_keywords:
- Data element
ms.assetid: e52b1961-7e11-4029-8ab1-84d275845067
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 57958cfe25563b4a7e2fd53f639d3bc289dce07c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117359"
---
# <a name="data-element-assl"></a>Éléments Data (ASSL)
  Contient (dans la collection d’enfants [élément Block &#40;ASSL&#41; ](block-element-assl.md) éléments) le contenu binaire d’un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<File xsi:type="ClrAssemblyFile">  
   ...  
   <Data xsi:type="DataBlock">...</Data>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[DataBlock](../data-type/datablock-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Fichier](file-element-assl.md) de type [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `Data` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément assembly &#40;ASSL&#41;](assembly-element-assl.md)   
 [Type de données ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Fichiers d’élément &#40;ASSL&#41;](../collections/files-element-assl.md)   
 [Bloque l’élément &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
