---
title: Élément PendingValue (ASSL) | Documents Microsoft
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
- PendingValue Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PendingValue
helpviewer_keywords:
- PendingValue element
ms.assetid: 386b2ec6-3d83-42d2-b83a-83e375fbdcbd
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 120c98d128698331a054a89be97ffa1513bb0191
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044831"
---
# <a name="pendingvalue-element-assl"></a>Élément PendingValue (ASSL)
  Contient la lecture seule en attente de la valeur de la [ServerProperty](../objects/serverproperty-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ServerProperty>  
   ...  
   <PendingValue>...</PendingValue>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout simpleType|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ServerProperty](../objects/serverproperty-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Cet élément contient la valeur de la `ServerProperty` qui sera utilisée la prochaine fois que l’instance actuelle de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est démarré. Cette valeur est généralement récupérée à partir du lieu de stockage de la valeur de la propriété de serveur : un fichier d'initialisation, le Registre [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ou tout autre mécanisme de stockage.  
  
 L’élément qui correspond au parent de `PendingValue` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ServerProperties &#40;ASSL&#41;](../collections/serverproperties-element-assl.md)   
 [Élément serveur &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  