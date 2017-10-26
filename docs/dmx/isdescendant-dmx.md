---
title: IsDescendant (DMX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsDescendant
dev_langs:
- DMX
helpviewer_keywords:
- IsDescendant function
ms.assetid: d9fe7446-edb5-487b-8ea6-c9efaccf6d90
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4a1e7959a303b768851784af0ab9c88abd257674
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="isdescendant-dmx"></a>IsDescendant (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indique si le nœud actuel provient du nœud spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>Type de retour  
 Type booléen  
  
## <a name="remarks"></a>Notes  
 **IsDescendant** est utilisée uniquement dans [SELECT FROM &#60; modèle &#62;. CONTENU &#40; DMX &#41; ](../dmx/select-from-model-content-dmx.md) et [SELECT FROM &#60; modèle &#62;. DIMENSION_CONTENT &#40; DMX &#41; ](../dmx/select-from-model-dimension-content-dmx.md) requêtes.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne tous les cas qui descendent du nœud spécifié dans la fonction IsDescendant.  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

