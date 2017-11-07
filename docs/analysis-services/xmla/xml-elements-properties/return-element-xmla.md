---
title: "Élément Return (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- return Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06b93a7d4c785f8e298a40d6b0accd2ad945b53e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="return-element-xmla"></a>Élément return (XMLA)
  Contient des informations retournées par une [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md) élément en réponse à une [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) appel de méthode ou un [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) élément en réponse à une [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) appel de méthode.  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md), [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|  
|Éléments enfants|Consultez le tableau ci-dessous.|  
  
|Ancêtre|Éléments enfants|  
|--------------|--------------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[racine](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[racine](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) ou [résultats](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **retourner** élément contient les données retournées par le **Discover** et **Execute** méthodes. En règle générale, les **retourner** élément contienne un seul **racine** élément qui contient les données retournées par une réussite **Discover** ou **Execute** appel de méthode ou un XML pour l’exception de Analysis (XMLA) retournée par un appel de méthode échoue. Si le **Execute** méthode contient un **lot** commande qui effectue plusieurs opérations, le **retourner** élément contient un **résultats** élément qui, à son tour, contient un **racine** élément pour chaque commande exécutée avec succès ou non par le **lot** commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

