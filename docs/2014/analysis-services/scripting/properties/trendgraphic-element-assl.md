---
title: Élément TrendGraphic (ASSL) | Documents Microsoft
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
- TrendGraphic Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TrendGraphic
helpviewer_keywords:
- TrendGraphic element
ms.assetid: 7448fd80-3072-4d85-b3a0-6606d1d20885
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8d4030a0936eee85fd32cfc87a4d5b441ef63b74
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051589"
---
# <a name="trendgraphic-element-assl"></a>Élément TrendGraphic (ASSL)
  Contient la représentation graphique recommandée de la tendance de la [Kpi](../objects/kpi-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Kpi>  
   ...  
   <TrendGraphic>...</TrendGraphic>  
   ...  
</Kpi>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Indicateur de performance clé](../objects/kpi-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Flèche standard*|Flèche standard|  
|*Flèche d’état - croissant*|Flèche d'état|  
|*Flèche d’état - décroissant*|Flèche d'état inversée|  
|*Émoticône*|Visage|  
  
 L’élément qui correspond au parent de `TrendGraphic` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  