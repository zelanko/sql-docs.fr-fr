---
title: Type de données ComAssembly (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cf05a673de90310563cdc5264f61e2da0952450
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133449"
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
 Le `ComAssembly` élément contient une référence (le nom de fichier qualifié complet ou l’identificateur programmatique) pour une bibliothèque COM associée à une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou avec une base de données spécifique sur une instance de [!INCLUDE[ssAS](../../../includes/ssas-md.md)].  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ClrAssembly &#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
