---
title: Caption, élément (ASSL) | Microsoft Docs
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
- Caption Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Caption
helpviewer_keywords:
- Caption element
ms.assetid: ed2be851-0ddc-4fa5-8aee-b2acb2e6d25e
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 283e7f84373d5f36431ba1b706b4d27e23cb876f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167700"
---
# <a name="caption-element-assl"></a>Élément Caption (ASSL)
  Contient la légende de l'élément parent associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action> <!-- or Translation -->  
   ...  
  <Caption>...</Caption>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Action](../objects/action-element-assl.md), [traduction](../objects/translation-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de `Caption` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.Action> et <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
