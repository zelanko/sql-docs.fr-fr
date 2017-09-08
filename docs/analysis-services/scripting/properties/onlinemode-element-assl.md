---
title: "Élément OnlineMode (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- OnlineMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- OnlineMode
helpviewer_keywords:
- OnlineMode element
ms.assetid: 0bbac4e2-002f-4be4-8dd6-ccd7034f5f93
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bf7b07efcfdc165ed3abd737aaecd241a225a71b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="onlinemode-element-assl"></a>Élément OnlineMode (ASSL)
  Spécifie si la base de données est remise en ligne immédiatement dès le début de la reconstruction du cache ou seulement lorsque la reconstruction du cache est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <OnlineMode>...</OnlineMode>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Immédiate*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Immédiate*|La base de données est remise en ligne immédiatement lorsque la reconstruction du cache est initiée.|  
|*OnCacheComplete*|La base de données n'est remise en ligne que lorsque la reconstruction du cache est terminée.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **OnlineMode** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Voir aussi  
 [ProactiveCaching, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)  
  
  
