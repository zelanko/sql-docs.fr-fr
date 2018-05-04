---
title: Élément EndOfData (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- EndOfData Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- EndOfData
helpviewer_keywords:
- EndOfData element
ms.assetid: 4cee48bc-d486-4125-9d65-f323c6ec9d09
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6789b60061d59009913f95c54fe395346a552d7f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="endofdata-element-assl"></a>Élément EndOfData (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indique la fin des données provenance d’un [PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<PushedDataSource>  
   ...  
   <EndOfData>...</EndOfData>  
   ...  
</PushedDataSource  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément obligatoire qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le dernier paquet de données à partir de la **PushedDataSource** doit définir le **EndOfData** élément **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
