---
title: Type de données MiningModelingFlag (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MiningModelingFlag Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelingFlag
helpviewer_keywords:
- MiningModelingFlag data type
ms.assetid: aaa72ba8-051e-4b01-b1e9-9c8d83b8b752
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 32ee744bdfcd084c4be88511ecba025ca9a270de
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151776"
---
# <a name="miningmodelingflag-data-type-assl"></a>Type de données MiningModelingFlag (ASSL)
  Définit un type de données primitif qui représente les indicateurs de modélisation pour une [ModelingFlag](../objects/modelingflag-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModelingFlag>...</MiningModelingFlag>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|Chaîne (énumération)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|None|  
|Éléments dérivés|[ModelingFlag](../objects/modelingflag-element-assl.md) ([ModelingFlags](../collections/modelingflags-element-assl.md) collection de [MiningModelColumn](miningmodelcolumn-data-type-assl.md) ou [ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Le nom d'indicateur peut contenir des espaces. Les valeurs prises en charge en mode natif sont répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|La colonne doit être modélisée comme si elle contenait deux états (manquant et non manquant), quelles que soient les valeurs figurant dans la colonne. Cela peut s'avérer particulièrement utile pour les colonnes d'une table imbriquée où les valeurs sont réparties dans les cas.|  
|*NON NULL*|La colonne ne peut pas accepter de valeurs NULL.|  
|*RÉGRESSEUR*|La colonne fournit des valeurs de régresseur pour les scénarios de test.|  
  
 Indicateurs spécifiques au fournisseur supplémentaires peuvent être utilisés si des données ou OLE DB d’exploration de données tiers ont été agrégés sur l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Un élément étroitement lié dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  