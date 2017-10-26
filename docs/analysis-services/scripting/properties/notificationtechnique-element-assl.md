---
title: "Élément NotificationTechnique (ASSL) | Documents Microsoft"
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
- NotificationTechnique Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- NotificationTechnique element
ms.assetid: 80c43de3-f147-4bf5-bb85-da9d182ce415
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0a5fdcfc7dc7d86e9036ed075e5c5332e76dc3be
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="notificationtechnique-element-assl"></a>Élément NotificationTechnique (ASSL)
  Spécifie si [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou une application cliente externe traite les notifications.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCachingBinding>  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Client*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Client*|L'application cliente externe traite la notification.|  
|*Server*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] traite la notification.|  
  
 L’élément qui correspond au parent de **NotificationTechnique** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ProactiveCachingBinding>.  
  
 L’énumération qui correspond aux valeurs autorisées pour **NotificationTechnique** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.NotificationTechnique>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données ProactiveCachingBinding &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)  
  
  

