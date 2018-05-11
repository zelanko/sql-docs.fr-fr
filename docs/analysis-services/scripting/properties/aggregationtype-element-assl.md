---
title: Élément AggregationType (ASSL) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ccc54deedf73fa3b80d7f8bf9eeba7266ea747f1
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="aggregationtype-element-assl"></a>Élément AggregationType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Définit le type d’agrégation stocké par le [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AggregationInstance>  
   ...  
   <AggregationType>...</AggregationType>  
   ...  
</AggregationInstance>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément obligatoire qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*IndexedView*|L'agrégation est stockée dans une vue indexée.|  
|*Table*|L'agrégation est stockée dans une table.|  
|*Défini par l’utilisateur*|L'agrégation est définie par l'utilisateur.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **AggregationType** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
