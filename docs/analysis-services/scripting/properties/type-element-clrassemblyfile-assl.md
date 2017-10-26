---
title: "Type d’élément (ClrAssemblyFile) (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Type Element (ClrAssemblyFile)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ab9e1e2c-ab06-4cd1-b007-16d738dc5604
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 26a677b917f2b537f1c21858754fad7b8ade43d0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="type-element-clrassemblyfile-assl"></a>Élément Type (ClrAssemblyFile) (ASSL)
  Spécifie le type de fichier de l’un des fichiers qui appartiennent à un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] assembly .NET Framework.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ClrAssemblyFile>  
      ...  
      <Type>...</Type>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes suivantes :  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Principal*|Le fichier correspond au fichier principal dans l'assembly.|  
|*Dépendants*|Le fichier spécifié correspond au fichier dépendant dans l'assembly.|  
|*Débogage*|Le fichier spécifié contient des informations de débogage.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **Type** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ClrAssemblyFileType>.  
  
 L’élément qui correspond au parent de **Type** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément File &#40; ASSL &#41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Élément de fichiers &#40; ASSL &#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [Type de données ClrAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Assembly, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Élément Assemblies &#40; ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

