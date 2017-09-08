---
title: root Element (XMLA) | Documents Microsoft
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
- Root Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#root
- urn:schemas-microsoft-com:xml-analysis#root
- microsoft.xml.analysis.root
helpviewer_keywords:
- root element
ms.assetid: ecd9d6e8-b16c-4d62-9a87-107c413a0056
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 972757d71db61ed5cbe82d9bf5e91b448c69260c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="root-element-xmla"></a>Élément racine (Root) (XMLA)
  Contient un résultat retourné par la [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) méthode ou une commande XML for Analysis (XMLA) exécutée à l’aide de la [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<return> <!-- or results-->  
   ...  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">...</root> <!-- for Execute method only -->  
   <!-- or -->  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">...</root>  
   <!-- or -->  
   <root xmlns= xmlns="urn:schemas-microsoft-com:xml-analysis:empty">...</root>  
   ...  
</return>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Consultez le tableau ci-dessous.|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
|Ancêtre|Type de données|  
|--------------|---------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[Ensemble de lignes](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md), [ensemble de lignes](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[résultats](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md), [de retour](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **racine** élément contient les informations retournées dans le le [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md) élément retourné par un seul **Discover** appel de méthode, ou dans le [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) élément retourné par une commande XMLA unique exécutée par un seul **Execute** appel de méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
