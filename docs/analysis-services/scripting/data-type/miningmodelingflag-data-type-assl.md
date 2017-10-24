---
title: "Type de données MiningModelingFlag (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
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
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bab055eef15474bfa22adefdc8ea6709659af978
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="miningmodelingflag-data-type-assl"></a>Type de données MiningModelingFlag (ASSL)
  Définit un type de données primitif qui représente les indicateurs de modélisation pour une [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) élément.  
  
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
|Éléments dérivés|[ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) ([ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md) collection de [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md) ou [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Le nom d'indicateur peut contenir des espaces. Les valeurs prises en charge en mode natif sont répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|La colonne doit être modélisée comme si elle contenait deux états (manquant et non manquant), quelles que soient les valeurs figurant dans la colonne. Cela peut s'avérer particulièrement utile pour les colonnes d'une table imbriquée où les valeurs sont réparties dans les cas.|  
|*NON NULL*|La colonne ne peut pas accepter de valeurs NULL.|  
|*RÉGRESSEUR*|La colonne fournit des valeurs de régresseur pour les scénarios de test.|  
  
 Indicateurs spécifiques au fournisseur supplémentaires peuvent être utilisés si des données ou OLE DB d’exploration de données tiers ont été agrégés sur l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Un élément étroitement lié dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

