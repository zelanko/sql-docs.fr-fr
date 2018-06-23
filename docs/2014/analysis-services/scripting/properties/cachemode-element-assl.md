---
title: Élément CacheMode (ASSL) | Documents Microsoft
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
- CacheMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- CacheMode element
ms.assetid: bfb8f7bb-ccd3-4dfe-a36a-1cea15edfe40
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0698628ee699ab19abaf7c1b1857db3c1d68dfc2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040960"
---
# <a name="cachemode-element-assl"></a>Élément CacheMode (ASSL)
  Détermine le mécanisme de mise en cache utilisé pour les données d'apprentissage récupérées au cours du traitement d'une structure d'exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructure>  
   ...  
   <CacheMode>...</CacheMode>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*KeepTrainingCases*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*KeepTrainingCases*|Les cas d'apprentissage sont mis en cache au cours du traitement et après celui-ci.|  
|*ClearAfterProcessing*|Les cas d'apprentissage sont mis en cache au cours du traitement mais sont supprimés après celui-ci.|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `CacheMode` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  