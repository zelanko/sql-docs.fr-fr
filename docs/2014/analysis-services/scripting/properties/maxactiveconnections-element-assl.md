---
title: Élément MaxActiveConnections (ASSL) | Documents Microsoft
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
- MaxActiveConnections Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MaxActiveConnections element
ms.assetid: 0dc5b64d-061d-409f-95c0-4c63f87f5ee4
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df2dafc69a97d1beb954100413761c07878881d4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040958"
---
# <a name="maxactiveconnections-element-assl"></a>Élément MaxActiveConnections (ASSL)
  Contient le nombre maximal de connexions simultanées autorisées par un élément qui est dérivé de la [source de données](../data-type/datasource-data-type-assl.md) type de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataSource>  
   ...  
   <MaxActiveConnections>...</MaxActiveConnections>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|`10`|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DataSource](../data-type/datasource-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Si la valeur de cet élément est définie à zéro, le nombre maximal de connexions simultanées est déterminé par la cartouche utilisée pour accéder à la source de données. Si la valeur de cet élément est négative, le nombre maximal de connexions simultanées est illimité.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  