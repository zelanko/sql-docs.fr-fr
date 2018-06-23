---
title: Élément PropertyList (XMLA) | Documents Microsoft
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
- PropertyList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PropertyList
- microsoft.xml.analysis.propertylist
- urn:schemas-microsoft-com:xml-analysis#PropertyList
helpviewer_keywords:
- PropertyList element
ms.assetid: 58e63bd9-8aac-438d-adba-1868b4d123f5
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 4b49ad0cf03ce331a00a7eefc9f1302176d89e74
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039171"
---
# <a name="propertylist-element-xmla"></a>Élément PropertyList (XMLA)
  Contient une collection de XML pour les propriétés de Analysis (XMLA) utilisées par le [Discover](../xml-elements-methods-discover.md) et [Execute](../xml-elements-methods-execute.md) méthodes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Properties>  
   <PropertyList>  
      <!-- Zero or more XMLA properties -->  
   </PropertyList>  
</Properties>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Propriétés](properties-element-xmla.md)|  
|Éléments enfants|Propriétés XMLA (consultez la section Notes)|  
  
## <a name="remarks"></a>Notes  
 Le `PropertyList` élément contient une collection de propriétés XMLA. Chaque propriété permet à l'utilisateur de contrôler un aspect de la méthode `Discover` ou `Execute`, tel que la définition des informations requises pour se connecter à la source de données, la spécification du format de retour du jeu de résultats ou la spécification des paramètres régionaux selon lesquels les données doivent être mises en forme. Chaque propriété XMLA dans le `PropertyList` est définie par un élément XML distinct. La valeur de la propriété XMLA correspond aux données figurant dans l'élément XML et le nom de la propriété XMLA correspond au nom de l'élément XML.  
  
 Les propriétés disponibles et leurs valeurs peuvent être obtenues en utilisant le type de demande DISCOVER_PROPERTIES avec la `Discover` (méthode). Il n'existe aucun ordre requis pour les propriétés répertoriées dans l'élément `PropertyList`.  
  
 Pour plus d’informations sur les propriétés XMLA prises en charge par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], consultez [pris en charge les propriétés XMLA &#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md).  
  
## <a name="example"></a>Exemple  
  
```  
<Properties>  
   <PropertyList>  
      <DataSourceInfo>  
         Provider=MSOLAP;Data Source=local;  
      </DataSourceInfo>  
      <Catalog>  
         Foodmart 2000  
      </Catalog>  
      <Format>  
         Multidimensional  
      </Format>  
   </PropertyList>  
</Properties>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  