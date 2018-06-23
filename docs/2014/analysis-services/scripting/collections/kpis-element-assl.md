---
title: Élément KPIs (ASSL) | Documents Microsoft
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
- Kpis Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Kpis
helpviewer_keywords:
- Kpis element
ms.assetid: da4e32a0-1416-4d32-8b7f-7d74be23c9d4
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 892e5997802b2d24d23ac9cb7e3be4ecb1b401c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140639"
---
# <a name="kpis-element-assl"></a>Élément Kpis (ASSL)
  Contient la collection d’indicateurs de performance clés ([Kpi](../objects/kpi-element-assl.md) éléments) associé à l’élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube><!-- or Perspective -->  
   ...  
   <Kpis>  
      <Kpi>...</Kpi> <!-- parent: Cube -->  
<!-- or -->  
      <Kpi xsi:type="PerspectiveKpi">...</Kpi> <!-- parent: Perspective -->  
   ...  
</Cube>  
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
|Éléments parents|[Cube](../objects/cube-element-assl.md), [Perspective](../objects/perspective-element-assl.md)|  
  
|Ancêtre ou parent|Élément enfant|  
|------------------------|-------------------|  
|[Cube](../objects/cube-element-assl.md)|[Indicateur de performance clé](../objects/kpi-element-assl.md)|  
|[Point de vue](../objects/perspective-element-assl.md)|[Indicateur de performance clé](../objects/kpi-element-assl.md) de type [PerspectiveKpi](../data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.KpiCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  