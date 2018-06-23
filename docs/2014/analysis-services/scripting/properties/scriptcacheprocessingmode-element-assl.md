---
title: Élément ScriptCacheProcessingMode (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ScriptCacheProcessingMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ScriptCacheProcessingMode
helpviewer_keywords:
- ScriptCacheProcessingMode element
ms.assetid: 95c0723c-69a4-43e7-b743-f712180a7681
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0566ea0411eb3f6574d03e738017d8ca6a5bdf2f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155124"
---
# <a name="scriptcacheprocessingmode-element-assl"></a>Élément ScriptCacheProcessingMode (ASSL)
  Indique si le serveur doit construire le cache des scripts au cours du traitement ou après celui-ci.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube>  
   ...  
      <ScriptCacheProcessingMode>...</ScriptCacheProcessingMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Régulière*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Cube](../objects/cube-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Régulière*|Le serveur construit le cache des scripts au cours du traitement.|  
|*Différé*|Le serveur construit le cache des scripts après le traitement.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `ScriptCacheProcessingMode` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ScriptCacheProcessingMode>.  
  
 L’élément qui correspond au parent de `ScriptCacheProcessingMode` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Cube>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  