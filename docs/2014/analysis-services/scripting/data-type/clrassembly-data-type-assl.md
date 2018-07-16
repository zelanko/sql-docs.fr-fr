---
title: Type de données ClrAssembly (ASSL) | Microsoft Docs
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
- ClrAssembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClrAssembly
helpviewer_keywords:
- ClrAssembly data type
ms.assetid: 3f5dc5a1-ebd6-41b8-ac04-91d4de137eb4
caps.latest.revision: 44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 63809f3dd903878baf5eabf1642430fbe0d9aa8e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235579"
---
# <a name="clrassembly-data-type-assl"></a>Type de données ClrAssembly (ASSL)
  Définit un type de données dérivé qui représente un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly associé à un [base de données](../objects/database-element-assl.md) ou [Server](../objects/server-element-assl.md) élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ClrAssembly>  
      <!-- The following elements extend Assembly -->  
   <Files>...</Files>  
      <PermissionSet>...</PermissionSet>  
</ClrAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Assembly](../objects/assembly-element-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucun (type abstrait)|  
|Éléments enfants|[Fichiers](../collections/files-element-assl.md), [PermissionSet](../properties/permissionset-element-assl.md)|  
|Éléments dérivés|Consultez [Assembly](../objects/assembly-element-assl.md) ([assemblys](../collections/assemblies-element-assl.md) collection de [base de données](../objects/database-element-assl.md) ou [Server](../objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Le `ClrAssembly` élément contient les fichiers nécessaires pour recréer un [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly, associés soit à une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou avec une base de données spécifique sur une instance de [!INCLUDE[ssAS](../../../includes/ssas-md.md)], ainsi que le autorisations nécessaires pour exécuter l’assembly.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ClrAssembly>.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier d’élément &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Type de données ClrAssemblyFile &#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)   
 [Élément de données &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Type de données DataBlock &#40;ASSL&#41;](datablock-data-type-assl.md)   
 [Bloque l’élément &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Bloquer l’élément &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Type de données ComAssembly &#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
