---
title: Élément Aliases (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Aliases Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Aliases
helpviewer_keywords:
- Aliases element
ms.assetid: 9de9e683-d30d-4d61-b32d-c5a946825742
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 677434b5ea6383e5905a703225edb5e56e3fb4e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267685"
---
# <a name="aliases-element-assl"></a>Élément Aliases (ASSL)
  Contient la collection de [Alias](../properties/alias-element-assl.md) éléments associés à un [compte](../objects/account-element-assl.md) élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Account>  
      ...  
   <Aliases>  
      <Alias>...</Alias>  
      </Aliases>  
      ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucun (collection)|  
|Valeur par défaut|Aucun (collection)|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Compte](../objects/account-element-assl.md)|  
|Éléments enfants|[Alias](../properties/alias-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `Aliases` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comptes élément &#40;ASSL&#41;](accounts-element-assl.md)   
 [Élément de base de données &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
