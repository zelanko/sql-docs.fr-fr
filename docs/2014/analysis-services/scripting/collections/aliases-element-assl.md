---
title: Élément Aliases (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4783d4d24c383864efb212f512e24ceeb8b842b2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049089"
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
|Éléments parents|[compte](../objects/account-element-assl.md)|  
|Éléments enfants|[Alias](../properties/alias-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `Aliases` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comptes élément &#40;ASSL&#41;](accounts-element-assl.md)   
 [Élément de base de données &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
