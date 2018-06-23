---
title: Élément CellInfo (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CellInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cellinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#CellInfo
- urn:schemas-microsoft-com:xml-analysis#CellInfo
helpviewer_keywords:
- CellInfo element
ms.assetid: 8b6420f1-e9a7-4975-b580-1439fa11f5ca
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 803640fe83ccc3137b4597b8c1b78850abeb55c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053584"
---
# <a name="cellinfo-element-xmla"></a>Élément CellInfo (XMLA)
  Représente les métadonnées de cellule contenue par le parent [OlapInfo](olapinfo-element-xmla.md) élément.  
  
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[OlapInfo](olapinfo-element-xmla.md)|  
|Éléments enfants|Une ou plusieurs définitions de propriété de cellule|  
  
## <a name="remarks"></a>Notes  
 L'élément `CellInfo` contient une collection de propriétés de cellule pour les cellules incluses dans le dataset multidimensionnel retourné par un élément `root` à l'aide du type de données `MDDataSet`. Chaque propriété de cellule dans l'élément `CellInfo` est définie par un élément XML distinct, chacune avec un attribut `name` et un attribut `type`. L'attribut `name` de la propriété de cellule correspond au nom de la propriété de cellule OLE DB pour OLAP représentée par l'élément XML et l'attribut `type` représente le type de données XML de la propriété de cellule. Le nom de l'élément XML permet d'identifier la valeur de la propriété de cellule pour les cellules contenues dans l'élément `CellData` de l'élément `root`.  
  
 La syntaxe suivante décrit une définition de propriété de cellule :  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 Les propriétés disponibles et leurs valeurs peuvent être obtenues en utilisant le type de demande DISCOVER_PROPERTIES avec la `Discover` (méthode). Il n'existe aucun ordre requis pour les propriétés répertoriées dans l'élément `PropertyList`.  
  
 Un fournisseur peut éventuellement spécifier des valeurs par défaut pour des propriétés de cellule ou de membre individuelles dans la section `AxisInfo` ou `CellInfo`. Les valeurs par défaut peuvent fournir un résultat plus restreint si la propriété affiche toujours, ou presque, la même valeur. Pour indiquer une valeur par défaut pour une propriété, le`Default` élément peut éventuellement être spécifié comme un élément enfant de l’un des éléments de définition de propriété de cellule. Par conséquent, l'absence d'une propriété de membre ou de cellule dans le résultat signifie que la valeur indiquée par défaut correspond à la valeur de la propriété de cellule.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre comment les propriétés de cellule VALUE, FORMATTED_VALUE et FORMAT_STRING sont représentées dans l'élément `CellInfo`.  
  
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
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  