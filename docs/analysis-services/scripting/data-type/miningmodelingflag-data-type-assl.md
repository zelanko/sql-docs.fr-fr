---
title: Type de données MiningModelingFlag (ASSL) | Documents Microsoft
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
- MiningModelingFlag Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningModelingFlag
helpviewer_keywords:
- MiningModelingFlag data type
ms.assetid: aaa72ba8-051e-4b01-b1e9-9c8d83b8b752
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 24981d225175d45bee29a2372bb28492d3180be7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="miningmodelingflag-data-type-assl"></a>Type de données MiningModelingFlag (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Définit un type de données primitif représentant les indicateurs de modélisation d'un élément [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModelingFlag>...</MiningModelingFlag>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|Chaîne (énumération)|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|Aucune|  
|Éléments dérivés|[ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) (collection[ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md) de [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md) ou [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Le nom d'indicateur peut contenir des espaces. Les valeurs prises en charge en mode natif sont répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|La colonne doit être modélisée comme si elle contenait deux états (manquant et non manquant), quelles que soient les valeurs figurant dans la colonne. Cela peut s'avérer particulièrement utile pour les colonnes d'une table imbriquée où les valeurs sont réparties dans les cas.|  
|*NON NULL*|La colonne ne peut pas accepter de valeurs NULL.|  
|*RÉGRESSEUR*|La colonne fournit des valeurs de régresseur pour les scénarios de test.|  
  
 L'usage d'indicateurs spécifiques au fournisseur supplémentaires est envisageable si des fournisseurs OLE DB ou d'exploration de données tiers ont été agrégés sur l'instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Un élément étroitement lié dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
