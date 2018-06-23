---
title: Élément AggregationFunction (ASSL) | Documents Microsoft
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
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6c8b28c740e82d661c2664eac576f0e079fd3d46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041896"
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
|Éléments parents|[Compte](../objects/account-element-assl.md)|  
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
|*Premier non vide*|La mesure est agrégée par retour de son premier membre non vide.|  
|*LastNonEmpty*|La mesure est agrégée par retour de son dernier membre non vide.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `AggregationFunction` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comptes d’élément &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  