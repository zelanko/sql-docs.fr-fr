---
title: Élément AggregateFunction (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AggregateFunction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregateFunction
helpviewer_keywords:
- AggregateFunction element
ms.assetid: 880b6bd0-d62a-4221-831c-39f748ee84f2
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2eb41e7a281d3ee343b8b96c339fb8baa1a5283e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="aggregatefunction-element-assl"></a>Élément AggregateFunction (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Définit le type de fonction d’agrégation utilisée par un [mesure](../../../analysis-services/scripting/objects/measure-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Measure>  
   ...  
   <AggregateFunction>...</AggregateFunction>  
   ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Sum*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Mesure](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes   
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Sum*|La mesure est agrégée à l'aide de la fonction **Sum** .|  
|*Nombre*|La mesure est agrégée à l'aide de la fonction **Count** .|  
|*Min*|La mesure est agrégée à l'aide de la fonction **Min** .|  
|*Max*|La mesure est agrégée à l'aide de la fonction **Max** .|  
|*DistinctCount*|La mesure est agrégée à l'aide de la fonction **DistinctCount** .|  
|*Aucun*|La mesure n'est pas agrégée.|  
|*ByAccount*|La mesure est agrégée par compte.|  
|*AverageOfChildren*|La mesure est agrégée par retour de la moyenne de ses enfants.|  
|*FirstChild*|La mesure est agrégée par retour de son premier membre enfant.|  
|*LastChild*|La mesure est agrégée par retour de son dernier membre enfant.|  
|*Premier non vide*|La mesure est agrégée par retour de son premier membre non vide.|  
|*LastNonEmpty*|La mesure est agrégée par retour de son dernier membre non vide.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **AggregateFunction** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
