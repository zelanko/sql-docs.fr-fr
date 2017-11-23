---
title: "Élément alias (ASSL) | Documents Microsoft"
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
apiname: Alias Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Alias
helpviewer_keywords: Alias element
ms.assetid: 674fdb06-e33c-4f35-bd6a-d9bbb13ececa
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 993a01aec0033f89a984358df7061c03512b0295
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="alias-element-assl"></a>Élément Alias (ASSL)
  Définit un alias pour une [compte](../../../analysis-services/scripting/objects/account-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Aliases>  
      <Alias>...</Alias>  
</Aliases>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Alias](../../../analysis-services/scripting/collections/aliases-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de l'élément **Alias** est utilisée comme un autre nom pour le compte défini par l'élément **Account** parent ; elle permet en outre d'identifier la combinaison de type de compte et de fonction d'agrégation dans une interface utilisateur.  
  
 L’élément qui correspond au parent de la **alias** collection dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
