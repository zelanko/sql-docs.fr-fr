---
title: Élément OlapInfo (XMLA) | Documents Microsoft
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
- OlapInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#OlapInfo
- microsoft.xml.analysis.olapinfo
- urn:schemas-microsoft-com:xml-analysis#OlapInfo
- OLAPInfo
helpviewer_keywords:
- OlapInfo element
ms.assetid: 8828fdd7-c0f7-48ce-a0d0-ab4bc1a995cf
caps.latest.revision: 27
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 9b183bfa01d2e4060c38fa2768f63b21fff693e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139662"
---
# <a name="olapinfo-element-xmla"></a>Élément OlapInfo (XMLA)
  Contient les métadonnées de l’axe et la cellule contenue par un [racine](root-element-xmla.md) élément qui utilise le [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) type de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <OlapInfo>  
      <CubeInfo>...</CubeInfo>  
      <AxesInfo>...</AxesInfo>  
      <CellInfo>...</CellInfo>  
   </OlapInfo>  
   ...  
</root>  
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
|Éléments parents|[racine](root-element-xmla.md)|  
|Éléments enfants|[AxesInfo](axesinfo-element-xmla.md), [CellInfo](cellinfo-element-xmla.md), [CubeInfo](cubeinfo-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La section `OLAPInfo` d'un élément `root` qui utilise le type de données `MDDataSet` fournit des métadonnées relatives au cube, aux axes du résultat multidimensionnel et aux propriétés des cellules incluses dans le résultat.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  