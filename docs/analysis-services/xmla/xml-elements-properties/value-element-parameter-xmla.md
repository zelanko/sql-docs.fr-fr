---
title: "Valeur d’élément (Parameter) (XMLA) | Documents Microsoft"
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
- Value Element (Parameter)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: e590d189-91aa-40c7-8669-09c87812f4ce
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2f421aec3724eb6359bb0c55f825b4e630580b46
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="value-element-parameter-xmla"></a>Élément Value (Parameter) (XMLA)
  Contient la valeur d’un paramètre représenté par le [paramètre](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Parameter>  
   ...  
   <Value>...</Value>  
   ...  
</Parameter>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Paramètre](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **valeur** élément peut stocker n’importe quel type XML simple, ainsi que le code XML for Analysis (XMLA) **ensemble de lignes** type de données, pour les paramètres utilisés par les commandes XMLA dans le [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

