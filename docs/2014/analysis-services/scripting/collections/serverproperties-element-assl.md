---
title: Élément ServerProperties (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ServerProperties Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ServerProperties
helpviewer_keywords:
- ServerProperties element
ms.assetid: 8ccbef3f-1388-4fa3-b0a4-c89b89f09056
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95e921a9bc531b66b38423df74f33e2bb53d8078
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157479"
---
# <a name="serverproperties-element-assl"></a>Élément ServerProperties (ASSL)
  Contient la collection de [ServerProperty](../objects/serverproperty-element-assl.md) éléments associés à un [Server](../objects/server-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Server>  
      ...  
   <ServerProperties>  
      <ServerProperty>...</ServerProperty>  
   </ServerProperties>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Server](../objects/server-element-assl.md)|  
|Éléments enfants|[ServerProperty](../objects/serverproperty-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ServerPropertyCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
