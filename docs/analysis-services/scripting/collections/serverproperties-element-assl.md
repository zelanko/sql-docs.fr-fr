---
title: "Élément ServerProperties (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ServerProperties Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ServerProperties
helpviewer_keywords: ServerProperties element
ms.assetid: 8ccbef3f-1388-4fa3-b0a4-c89b89f09056
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ab839c124a555d0b7310dcdaa3517a87326329b6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="serverproperties-element-assl"></a>Élément ServerProperties (ASSL)
  Contient la collection de [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md) éléments associés à un [Server](../../../analysis-services/scripting/objects/server-element-assl.md) élément.  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Éléments enfants|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ServerPropertyCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections de &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
