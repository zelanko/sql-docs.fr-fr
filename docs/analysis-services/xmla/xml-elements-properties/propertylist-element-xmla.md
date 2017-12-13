---
title: "Élément PropertyList (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PropertyList Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PropertyList
- microsoft.xml.analysis.propertylist
- urn:schemas-microsoft-com:xml-analysis#PropertyList
helpviewer_keywords: PropertyList element
ms.assetid: 58e63bd9-8aac-438d-adba-1868b4d123f5
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 795c91c398337bba1444735e54bbbfeb33d07933
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="propertylist-element-xmla"></a>Élément PropertyList (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contient une collection de XML pour les propriétés de Analysis (XMLA) utilisées par le [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) et [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) méthodes.  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Propriétés](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
|Éléments enfants|Propriétés XMLA (consultez la section Notes)|  
  
## <a name="remarks"></a>Notes  
 L'élément **PropertyList** contient une collection de propriétés XMLA. Chaque propriété permet à l'utilisateur de contrôler un aspect de la méthode **Discover** ou **Execute** , tel que la définition des informations requises pour se connecter à la source de données, la spécification du format de retour du jeu de résultats ou la spécification des paramètres régionaux selon lesquels les données doivent être mises en forme. Chaque propriété XMLA dans l'élément **PropertyList** est définie par un élément XML distinct. La valeur de la propriété XMLA correspond aux données figurant dans l'élément XML et le nom de la propriété XMLA correspond au nom de l'élément XML.  
  
 Les propriétés disponibles et leurs valeurs peuvent être obtenues via le type de demande DISCOVER_PROPERTIES avec la méthode **Discover** . Il n'existe aucun ordre requis pour les propriétés répertoriées dans l'élément **PropertyList** .  
  
 Pour plus d’informations sur les propriétés XMLA prises en charge par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], consultez [pris en charge les propriétés XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
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
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
