---
title: "Élément UnknownMemberName (ASSL) | Documents Microsoft"
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
apiname: UnknownMemberName Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: UnknownMemberName
helpviewer_keywords: UnknownMemberName element
ms.assetid: 54271336-ea9b-4270-ac3a-9658a5cff77b
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2248afcd1d75e29368f0d7ca70b44ccba91bae37
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="unknownmembername-element-assl"></a>Élément UnknownMemberName (ASSL)
  Contient la légende (dans la langue par défaut de la dimension) du membre inconnu de la dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMemberName>...</UnknownMemberName>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|*Unknown*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de l'élément **UnknownMemberName** fournit la légende utilisée pour le membre inconnu. L'identificateur du membre inconnu est *Dimension*.UnknownMember, où *Dimension* est le nom unique de la dimension et ne peut pas être changé.  
  
 L’élément qui correspond au parent de **UnknownMemberName** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
