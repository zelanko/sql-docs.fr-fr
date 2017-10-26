---
title: "Élément SilenceOverrideInterval (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SilenceOverrideInterval Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- SilenceOverrideInterval
helpviewer_keywords:
- SilenceOverrideInterval element
ms.assetid: 0dcd2db4-9bc0-4460-b1dd-def0b38c4617
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c84c6f51a727620094aa21206da7d01187bbd6c2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="silenceoverrideinterval-element-assl"></a>Élément SilenceOverrideInterval (ASSL)
  Définit le temps qui doit s'écouler après la réception de la première notification et avant le démarrage de manière inconditionnelle du processus de création d'images MOLAP (multidimensional OLAP).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <SilenceOverrideInterval>...</SilenceOverrideInterval>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|duration|  
|Valeur par défaut|P0s|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de **SilenceOverrideInterval** remplace la valeur de **SilenceInterval** si une notification est reçue pendant la période de silence.  
  
 L’élément qui correspond au parent de **SilenceOverrideInterval** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

