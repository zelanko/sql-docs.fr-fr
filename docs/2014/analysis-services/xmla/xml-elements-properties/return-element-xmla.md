---
title: Élément Return (XMLA) | Microsoft Docs
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
- return Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4808372fbf80b2b3a79bc11e3f2423511eb717be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192401"
---
# <a name="return-element-xmla"></a>Élément return (XMLA)
  Contient des informations retournées par une [DiscoverResponse](../xml-elements-objects-discoverresponse.md) élément en réponse à une [Discover](../xml-elements-methods-discover.md) appel de méthode ou un [ExecuteResponse](../xml-elements-objects-executeresponse.md) élément en réponse à une [Execute](../xml-elements-methods-execute.md) appel de méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DiscoverResponse> <!-- or ExecuteResponse -->  
   <return>  
      <root>...</root>  
      <!-- or -->  
      <results>...</results> <!-- ExecuteResponse only -->  
   </return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DiscoverResponse](../xml-elements-objects-discoverresponse.md), [ExecuteResponse](../xml-elements-objects-executeresponse.md)|  
|Ancêtre :[DiscoverResponse](../xml-elements-objects-discoverresponse.md)|Enfant : <br />                        [racine](root-element-xmla.md)|  
|Ancêtre : <br />                        [ExecuteResponse](../xml-elements-objects-executeresponse.md)|Enfant : [racine](root-element-xmla.md) ou [résultats](results-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément `return` contient les données retournées par les méthodes `Discover` et `Execute`. En général, l'élément `return` contient un seul élément `root` contenant soit les données retournées par un appel de méthode `Discover` ou `Execute` réussi, soit une exception XMLA (XML for Analysis) retournée par un appel de méthode infructueux. Si la méthode `Execute` contient une commande `Batch` qui effectue plusieurs opérations, l'élément `return` contient un élément `results` qui, à son tour, contient un élément `root` pour chaque commande exécutée avec ou sans succès par la commande `Batch`.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
