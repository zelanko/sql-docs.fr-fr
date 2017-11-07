---
title: "L’élément Properties (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Properties Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Properties
- microsoft.xml.analysis.properties
- urn:schemas-microsoft-com:xml-analysis#Properties
- Properties
helpviewer_keywords:
- Properties element
ms.assetid: 0b5468e5-bf23-4d22-862f-72e27a9fff2f
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77029875d3c2e84c1b48c4e1e5454f735f5a2752
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="properties-element-xmla"></a>Élément Properties (XMLA)
  Contient du code XML pour les propriétés d’analyse (XMAL) utilisées par le [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) et [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) méthodes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Discover> <!-- or Execute -->  
...  
   <Properties>  
      <PropertyList>...</PropertyList>  
   </Properties>  
...  
</Discover>  
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
|Éléments parents|[Découvrir](../../../analysis-services/xmla/xml-elements-methods-discover.md), [exécuter](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|Éléments enfants|[PropertyList](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **propriétés** élément représente les propriétés XMLA utilisées pour contrôler des aspects de la **Discover** et **Execute** méthodes, telles que la définition des informations requises pour se connecter à la source de données, en spécifiant le format de retour du jeu de résultats, ou en spécifiant les paramètres régionaux dans lequel les données doivent être mises en forme.  
  
 Les propriétés disponibles et leurs valeurs peuvent être obtenues via le type de demande DISCOVER_PROPERTIES avec la méthode **Discover** .  
  
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
  
  

