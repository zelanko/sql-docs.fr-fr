---
title: "Élément DiscretizationMethod (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DiscretizationMethod Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DiscretizationMethod
helpviewer_keywords: DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fd84d0426afa9ee1272c26c8ca7ac302972748b4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="discretizationmethod-element-assl"></a>Élément DiscretizationMethod (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Définit la méthode à utiliser pour la discrétisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationMethod>...</DiscretizationMethod>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Aucun*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes   
 La valeur de l'élément **DiscretizationMethod** détermine comment les valeurs de l'élément **DimensionAttribute** ou **ScalarMiningStructureColumn** sont discrétisées ou organisées en un jeu de groupes spécifique. Pour plus d’informations sur les méthodes de discrétisation, consultez [méthodes de discrétisation &#40; exploration de données &#41;](../../../analysis-services/data-mining/discretization-methods-data-mining.md).  
  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Automatic*|Équivaut à la méthode de discretisation AUTOMATIC pour les colonnes de structure d'exploration de données.|  
|*EqualAreas*|Équivaut à la méthode de discretisation EQUAL_AREAS pour les colonnes de structure d'exploration de données.|  
|*Clusters*|Équivaut à la méthode de discretisation CLUSTERS pour les colonnes de structure d'exploration de données.|  
|*Seuils*|Équivaut à la méthode de discretisation THRESHOLDS pour les colonnes de structure d'exploration de données.|  
|*EqualRanges*|Équivaut à la méthode de discretisation EQUAL_RANGES pour les colonnes de structure d'exploration de données.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **DiscretizationMethod** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DiscretizationMethod>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
