---
title: Élément AggregationUsage (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- AggregationUsage Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationUsage
helpviewer_keywords:
- AggregationUsage element
ms.assetid: af0c2e7f-b659-4fbf-9b1a-66128db669a2
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8f85042458ba9aa2e580a1641a0a445fe34f2931
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="aggregationusage-element-assl"></a>Élément AggregationUsage (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contrôles comment le Concepteur d’agrégation dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crée des agrégations.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeAttribute>  
   ...  
   <AggregationUsage>...</AggregationUsage>  
   ...  
</CubeAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Par défaut*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Complet*|Toutes les agrégations de cube doivent inclure cet attribut.|  
|*Aucun*|Aucune agrégation du cube ne doit inclure cet attribut.|  
|*Non restreint*|Le concepteur d'agrégation ne fait l'objet d'aucune restriction.|  
|*Par défaut*|Le concepteur d'agrégation applique une règle par défaut en fonction du type d'attribut (*Full* pour les clés, *Unrestricted* pour les autres attributs)|  
  
 L’énumération qui correspond aux valeurs autorisées pour **AggregationUsage** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.AggregationUsage>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément cube & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
