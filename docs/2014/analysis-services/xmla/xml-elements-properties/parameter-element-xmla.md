---
title: Élément Parameter (XMLA) | Documents Microsoft
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
- Parameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Parameter
- microsoft.xml.analysis.parameter
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameter
helpviewer_keywords:
- Parameter element
ms.assetid: fe31ac3d-a3e8-4f60-a81a-c43271ddbed4
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 6e39068ff0fc5c1e0bf866029ad2e4413768c1c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141406"
---
# <a name="parameter-element-xmla"></a>Élément Parameter (XMLA)
  Contient le nom et la valeur d'un paramètre utilisé par la méthode [Execute](../xml-elements-methods-execute.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Parameters>  
...  
   <Parameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </Parameter>  
...  
</Parameters>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Paramètres](parameters-element-xmla.md)|  
|Éléments enfants|[Nom](name-element-parameter-xmla.md), [Valeur](value-element-parameter-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Certaines commandes XMLA (XML for Analysis), telles que la commande [Process](../xml-elements-commands/process-element-xmla.md) , peuvent exiger des informations supplémentaires. L'élément `Parameter` offre un mécanisme qui fournit des informations supplémentaires, y compris des informations mémorisées en bloc, à une commande XMLA.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  