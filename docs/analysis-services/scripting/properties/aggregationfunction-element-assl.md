---
title: "Élément AggregationFunction (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
apiname:
- AggregationFunction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationFunction
helpviewer_keywords:
- AggregationFunction element
ms.assetid: 40cfc7f9-1089-45f9-be90-a29770ed9682
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e14f744b35fc1d48ba2a96b15bd8bc3ec46e8e20
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Compte](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes suivantes :  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Sum*|La mesure est agrégée à l'aide de la fonction **Sum** .|  
|*Nombre*|La mesure est agrégée à l'aide de la fonction **Count** .|  
|*Min*|La mesure est agrégée à l'aide de la fonction **Min** .|  
|*Max*|La mesure est agrégée à l'aide de la fonction **Max** .|  
|*DistinctCount*|La mesure est agrégée à l'aide de la fonction **DistinctCount** .|  
|*Aucun*|La mesure n'est pas agrégée.|  
|*AverageOfChildren*|La mesure est agrégée par retour de la moyenne de ses enfants.|  
|*FirstChild*|La mesure est agrégée par retour de son premier membre enfant.|  
|*LastChild*|La mesure est agrégée par retour de son dernier membre enfant.|  
|*Premier non vide*|La mesure est agrégée par retour de son premier membre non vide.|  
|*LastNonEmpty*|La mesure est agrégée par retour de son dernier membre non vide.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **AggregationFunction** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Accounts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

