---
title: Type d’élément (ClrAssemblyFile) (ASSL) | Documents Microsoft
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
- Type Element (ClrAssemblyFile)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ab9e1e2c-ab06-4cd1-b007-16d738dc5604
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c253b2975c5e4f4cbf27c5b2d655a09617d644de
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038666"
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
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Principal*|Le fichier correspond au fichier principal dans l'assembly.|  
|*Dépendants*|Le fichier spécifié correspond au fichier dépendant dans l'assembly.|  
|*Débogage*|Le fichier spécifié contient des informations de débogage.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `Type` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ClrAssemblyFileType>.  
  
 L’élément qui correspond au parent de `Type` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de fichier &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Fichiers d’élément &#40;ASSL&#41;](../collections/files-element-assl.md)   
 [Type de données ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Élément assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Élément Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  