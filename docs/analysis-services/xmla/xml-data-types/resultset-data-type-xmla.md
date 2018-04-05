---
title: Type de données ResultSet (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Resultset Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Resultset
- urn:schemas-microsoft-com:xml-analysis#Resultset
- Resultset
helpviewer_keywords:
- Resultset data type
ms.assetid: 45e7d7d6-1f89-4dc8-b39d-9270ea2db541
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6fd063f8a32fbd65ef806d624a7f82d9b154f3e5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="resultset-data-type-xmla"></a>Type de données Resultset (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Définit un type de données primitif abstrait qui représente les données retournées par une [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) ou [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) appel de méthode.  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis:resultset  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Resultset>  
   <Exception>...</Exception>  
   <Messages>...</Messages>  
</Resultset>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md), [ensemble de lignes](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Exception](../../../analysis-services/xmla/xml-elements-properties/exception-element-xmla.md), [Messages](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes   
 Le type de données **Resultset** est un jeu de résultats XML autodescriptif pouvant contenir le schéma et les données, selon le type d'informations à retourner.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XML &#40; XMLA &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
