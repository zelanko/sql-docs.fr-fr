---
title: root Element (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 06325419de82d11aaefdad542552af3f61acae97
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="root-element-xmla"></a>Élément racine (Root) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
