---
title: Type de données ClrAssemblyFile (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ClrAssemblyFile Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ClrAssemblyFile
helpviewer_keywords:
- ClrAssemblyFile data type
ms.assetid: 91074677-c149-483b-a56d-0e35d959d9eb
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 66941082bd01fba162191f8ee83fb69ce1e54a12
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="clrassemblyfile-data-type-assl"></a>Type de données ClrAssemblyFile (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Définit un type de données primitif qui représente un des fichiers qui composent un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] **Assembly** ([ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) élément).  
  
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
|Éléments enfants|[Données](../../../analysis-services/scripting/objects/data-element-assl.md), [nom](../../../analysis-services/scripting/properties/name-element-assl.md), [Type](../../../analysis-services/scripting/properties/type-element-clrassemblyfile-assl.md)|  
|Éléments dérivés|[Fichier](../../../analysis-services/scripting/objects/file-element-assl.md) ([fichiers](../../../analysis-services/scripting/collections/files-element-assl.md) collection de [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes   
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Voir aussi  
 [Server, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Élément de la base de données &#40; ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Élément Assemblies &#40; ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Assembly, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Type de données DataBlock &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Élément Blocks &#40; ASSL &#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Élément de bloc &#40; ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Type de données ComAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
