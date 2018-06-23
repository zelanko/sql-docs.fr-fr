---
title: Étapes de l’élément (XMLA) | Documents Microsoft
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
- Steps Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Steps
- microsoft.xml.analysis.steps
- urn:schemas-microsoft-com:xml-analysis#Steps
helpviewer_keywords:
- Steps element
ms.assetid: a6821a2a-89ec-418b-b2dd-92adf2ccc20e
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: cfafdc9aa9644b028d66b844550175a462a0258a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153558"
---
# <a name="steps-element-xmla"></a>Élément Steps (XMLA)
  Spécifie le nombre maximal d'étapes suivies par la commande [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md) pour concevoir des agrégations.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DesignAggregations>  
   ...  
   <Steps>...</Steps>  
   ...  
</DesignAggregations>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  