---
title: Élément RefreshPolicy (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: eaf54e5bab5c74bc04057c89a6ec5304168b5e64
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="refreshpolicy-element-assl"></a>Élément RefreshPolicy (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Détermine à quelle fréquence la partie dynamique de la dimension ou du groupe de mesures (telle que spécifiée par l'élément [Persistence](../../../analysis-services/scripting/properties/persistence-element-assl.md) ) fait l'objet d'une recherche de modifications.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <RefreshPolicy>...</RefreshPolicy>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|Consultez le tableau ci-dessous.|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
|Ancêtre ou parent|Valeur par défaut|  
|------------------------|-------------------|  
|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)|*ByQuery*|  
|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|Aucune|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*ByQuery*|Chaque requête procède à une vérification pour savoir si les données sources ont été modifiées.|  
|*ByInterval*|Les modifications sont recherchées dans les données sources à l'intervalle spécifié par [RefreshInterval](../../../analysis-services/scripting/properties/refreshinterval-element-assl.md).|  
  
 L’énumération qui correspond aux valeurs autorisées pour **RefreshPolicy** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.RefreshPolicy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Persistence & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/persistence-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
