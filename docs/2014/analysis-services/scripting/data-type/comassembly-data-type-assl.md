---
title: Type de données ComAssembly (ASSL) | Documents Microsoft
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
- ComAssembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ComAssembly
helpviewer_keywords:
- ComAssembly data type
ms.assetid: 23c0f4b3-b6ac-4ec8-9254-74d2f84f5244
caps.latest.revision: 49
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bfe3a7791d02d97b4283b63a1aedd3b6702fe563
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144375"
---
# <a name="comassembly-data-type-assl"></a>Type de données ComAssembly (ASSL)
  Définit un type de données dérivé qui représente une bibliothèque COM associée à un [Server](../objects/server-element-assl.md) ou [base de données](../objects/database-element-assl.md) élément.  
  
> [!IMPORTANT]  
>  Les assemblys COM peuvent présenter un risque pour la sécurité. En raison de ce risque et d'autres considérations, les assemblys COM ont été déconseillés dans [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]. Les assemblys COM peuvent ne pas être pris en charge dans les versions ultérieures.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ComAssembly>  
      <!-- The following elements extend Assembly -->  
   <Source>...</Source>  
</ComAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[assembly](../objects/assembly-element-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Source](../properties/source-element-comassembly-assl.md)|  
|Éléments dérivés|Consultez [Assembly](../objects/assembly-element-assl.md) ([assemblys](../collections/assemblies-element-assl.md) collection de [base de données](../objects/database-element-assl.md) ou [Server](../objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Le `ComAssembly` élément contient une référence (le nom de fichier qualifié complet ou l’identificateur programmatique) à une bibliothèque COM associée à une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou avec une base de données spécifique sur une instance de [!INCLUDE[ssAS](../../../includes/ssas-md.md)].  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ClrAssembly &#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  