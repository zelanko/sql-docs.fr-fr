---
title: "Élément CellInfo (XMLA) | Documents Microsoft"
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
- CellInfo Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cellinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#CellInfo
- urn:schemas-microsoft-com:xml-analysis#CellInfo
helpviewer_keywords:
- CellInfo element
ms.assetid: 8b6420f1-e9a7-4975-b580-1439fa11f5ca
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3a7b38201d5ba5c051cfacfb139ea52a6b93fb09
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="cellinfo-element-xmla"></a>Élément CellInfo (XMLA)
  Représente les métadonnées de cellule contenue par le parent [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<OlapInfo>  
   ...  
   <CellInfo>  
      <!-- One or more cell property definitions -->  
   </CellInfo>  
   ...  
</OlapInfo>  
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
|Éléments parents|[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Éléments enfants|Une ou plusieurs définitions de propriété de cellule|  
  
## <a name="remarks"></a>Notes  
 Le **CellInfo** élément contient une collection de propriétés de cellule pour les cellules incluses dans le dataset multidimensionnel retourné par une **racine** à l’aide de l’élément le **MDDataSet** type de données. Chaque propriété de cellule dans le **CellInfo** est définie par un élément XML distinct, chacun avec un **nom** attribut et un **type** attribut. Le **nom** attribut de la propriété de cellule correspond au nom d’OLE DB pour la propriété de cellule OLAP représentée par l’élément XML et le **type** attribut représente le type de données XML de la propriété de cellule. Le nom de l’élément XML est utilisé pour identifier la valeur de la propriété de cellule pour les cellules contenues dans le **CellData** élément de la **racine** élément.  
  
 La syntaxe suivante décrit une définition de propriété de cellule :  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 Les propriétés disponibles et leurs valeurs peuvent être obtenues via le type de demande DISCOVER_PROPERTIES avec la méthode **Discover** . Il n'existe aucun ordre requis pour les propriétés répertoriées dans l'élément **PropertyList** .  
  
 Un fournisseur peut éventuellement spécifier des valeurs par défaut pour les propriétés de membre ou une cellule individuelles dans le **AxisInfo** ou **CellInfo** section. Les valeurs par défaut peuvent fournir un résultat plus restreint si la propriété affiche toujours, ou presque, la même valeur. Pour indiquer une valeur par défaut pour une propriété, le**par défaut** élément peut éventuellement être spécifié comme un élément enfant de l’un des éléments de définition de propriété de cellule. Par conséquent, l'absence d'une propriété de membre ou de cellule dans le résultat signifie que la valeur indiquée par défaut correspond à la valeur de la propriété de cellule.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment les propriétés de cellule valeur, FORMATTED_VALUE et FORMAT_STRING sont représentées dans le **CellInfo** élément.  
  
```  
<OlapInfo>  
   ...  
      <CellInfo>  
         <Value name="VALUE"></Value>  
         <FmtValue name="FORMATTED_VALUE"></FmtValue>  
         <FormatString name="FORMAT_STRING"></FormatString>  
      </CellInfo>  
</OlapInfo>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

