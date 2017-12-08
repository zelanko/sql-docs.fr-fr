---
title: "Fichier de l’élément (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: File Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: File
helpviewer_keywords: File element
ms.assetid: 21c70707-d2f8-4040-9acb-cbce23076bcc
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a5d37a6ace9b56fe9bf5ae808c9a89bf49b6c568
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="file-element-assl"></a>Élément File (ASSL)
  Définit un des fichiers qui composent un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Files>  
   <File xsi:type="ClrAssemblyFile">...</File>  
</Files>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Fichiers](../../../analysis-services/scripting/collections/files-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **fichiers** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Voir aussi  
 [Server, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Élément de la base de données &#40; ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Élément Assemblies &#40; ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Assembly, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Type de données ClrAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Élément de données &#40; ASSL &#41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [Type de données DataBlock &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Élément Blocks &#40; ASSL &#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Élément de bloc &#40; ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Type de données ComAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
