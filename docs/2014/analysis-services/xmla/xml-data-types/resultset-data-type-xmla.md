---
title: Type de données ResultSet (XMLA) | Documents Microsoft
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
- Resultset Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
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
manager: mblythe
ms.openlocfilehash: d8a571012c82c9e4d26d9f586cf67344f19258a6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039390"
---
# <a name="resultset-data-type-xmla"></a>Type de données Resultset (XMLA)
  Définit un type de données primitif abstrait qui représente les données retournées par une [Discover](../xml-elements-methods-discover.md) ou [Execute](../xml-elements-methods-execute.md) appel de méthode.  
  
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
|Types de données dérivés|[MDDataSet](mddataset-data-type-xmla.md), [olapxmla_EmptyResult](emptyresult-data-type-xmla.md), [ensemble de lignes](rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Exception](../xml-elements-properties/exception-element-xmla.md), [Messages](../xml-elements-properties/messages-element-xmla.md)|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes  
 Le type de données `Resultset` est un jeu de résultats XML autodescriptif pouvant contenir le schéma et les données, selon le type d'informations à retourner.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  