---
title: Type de données ProactiveCachingObjectNotificationBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProactiveCachingObjectNotificationBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingObjectNotificationBinding data type
ms.assetid: b3cf5fb6-6121-4f25-8de6-f171792c440d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 201774fd7b46bf3d4fc30dfe304c8ffd80f7c6eb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080379"
---
# <a name="proactivecachingobjectnotificationbinding-data-type-assl"></a>Type de données ProactiveCachingObjectNotificationBinding (ASSL)
  Définit un type de données dérivé abstrait qui représente les informations de la [ProactiveCaching](../objects/proactivecaching-element-assl.md) élément sur les modifications de source de données, dans les tables et vues spécifiées ou dans les tables et les vues identifiées par le biais des liaisons de données existantes qui exigent une reconstruction du cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCachingObjectNotificationBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingObjectNotificationBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|Types de données dérivés|[ProactiveCachingInheritedBinding](inheritedbinding-data-type-assl.md), [ProactiveCachingTablesBinding](proactivecachingtablesbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[NotificationTechnique](../properties/notificationtechnique-element-assl.md)|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `ProactiveCachingBinding` type, y compris une table de la hiérarchie d’héritage de `ProactiveCachingBinding` types, consultez [Type de données ProactiveCachingBinding &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [Type de données de liaison &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ProactiveCachingObjectNotificationBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
