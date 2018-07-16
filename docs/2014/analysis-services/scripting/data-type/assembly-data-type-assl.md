---
title: Type de données assembly (ASSL) | Microsoft Docs
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
- Assembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Assembly data type
ms.assetid: 0a381322-9509-4579-a754-c6cdd0a70cc9
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 40cafd0d8ef11feaebce5161e97ef3717a9fb943
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233829"
---
# <a name="assembly-data-type-assl"></a>Type de données Assembly (ASSL)
  Définit un type de données primitif abstrait qui représente un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly ou une bibliothèque de liens dynamiques (DLL) COM associée une [Server](../objects/server-element-assl.md) ou [base de données](../objects/database-element-assl.md) élément.  
  
> [!IMPORTANT]  
>  Les assemblys COM peuvent présenter un risque pour la sécurité. En raison de ce risque et d'autres considérations, les assemblys COM ont été déconseillés dans [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]. Les assemblys COM peuvent ne pas être pris en charge dans les versions ultérieures.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Assembly>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <CreatedTimestamp>...</CreatedTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <ImpersonationInfo>...</ImpersonationInfo>  
   <Annotations>...</Annotations>  
</Assembly>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|[ClrAssembly](assembly-data-type-assl.md), [ComAssembly](comassembly-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [Description](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [ImpersonationInfo](../properties/impersonationinfo-element-assl.md), [ LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [nom](../properties/name-element-assl.md)|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes  
 Le type de données `Assembly` sert comme type de données de base pour l'élément `ComAssembly`, qui représente des bibliothèques COM associées à l'instance ou à la base de données, et l'élément `ClrAssembly`, qui représente des assemblys [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] associés à l'instance ou à la base de données. Pour plus d’informations, consultez [gestion des assemblys de modèle multidimensionnel](../../multidimensional-models/multidimensional-model-assemblies-management.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Assembly>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de serveur &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Élément de base de données &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
