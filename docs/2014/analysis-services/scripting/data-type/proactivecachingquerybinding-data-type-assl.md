---
title: Type de données ProactiveCachingQueryBinding (ASSL) | Documents Microsoft
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
- ProactiveCachingQueryBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingQueryBinding data type
ms.assetid: c1b06e50-9e68-40db-bdab-fc2cb3a8ff64
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 339c35a33d3d26268b027068c6ac7f5254046606
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139899"
---
# <a name="proactivecachingquerybinding-data-type-assl"></a>Type de données ProactiveCachingQueryBinding (ASSL)
  Définit un type de données dérivé qui représente les informations de la [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les modifications de source de données dans les tables et les vues identifiées lors de l’exécution des requêtes spécifiées qui exigent une reconstruction du cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCachingQueryBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <RefreshInterval>...</RefreshInterval>  
   <QueryNotification>...</QueryNotification>  
</ProactiveCachingQueryBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[QueryNotification](../objects/querynotification-element-assl.md), [RefreshInterval](../properties/refreshinterval-element-assl.md)|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `ProactiveCachingBinding` type, y compris une table de la hiérarchie d’héritage de `ProactiveCachingBinding` types, consultez [Type de données ProactiveCachingBinding &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [Type de données de liaison &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ProactiveCachingQueryBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  