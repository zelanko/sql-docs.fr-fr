---
title: Élément AggregationFunction (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationFunction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationFunction
helpviewer_keywords:
- AggregationFunction element
ms.assetid: 40cfc7f9-1089-45f9-be90-a29770ed9682
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 453d51d678a8e721eaa7fa280e23248c66019b5b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153209"
---
# <a name="aggregationfunction-element-assl"></a>Élément AggregationFunction (ASSL)
  Contient la fonction d'agrégation à utiliser pour le type de compte.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Account>  
   ...  
   <AggregationFunction>...</AggregationFunction>  
   ...  
</Account>  
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
|Éléments parents|[compte](../objects/account-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Sum*|La mesure est agrégée à l'aide de la fonction `Sum`.|  
|*Nombre*|La mesure est agrégée à l'aide de la fonction `Count`.|  
|*Min*|La mesure est agrégée à l'aide de la fonction `Min`.|  
|*Max*|La mesure est agrégée à l'aide de la fonction `Max`.|  
|*DistinctCount*|La mesure est agrégée à l'aide de la fonction `DistinctCount`.|  
|*Aucun*|La mesure n'est pas agrégée.|  
|*AverageOfChildren*|La mesure est agrégée par retour de la moyenne de ses enfants.|  
|*FirstChild*|La mesure est agrégée par retour de son premier membre enfant.|  
|*LastChild*|La mesure est agrégée par retour de son dernier membre enfant.|  
|*FirstNonEmpty*|La mesure est agrégée par retour de son premier membre non vide.|  
|*LastNonEmpty*|La mesure est agrégée par retour de son dernier membre non vide.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `AggregationFunction` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comptes élément &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
