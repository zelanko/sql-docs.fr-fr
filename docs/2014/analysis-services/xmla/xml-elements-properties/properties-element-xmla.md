---
title: Properties, élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Properties Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Properties
- microsoft.xml.analysis.properties
- urn:schemas-microsoft-com:xml-analysis#Properties
- Properties
helpviewer_keywords:
- Properties element
ms.assetid: 0b5468e5-bf23-4d22-862f-72e27a9fff2f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 83234d39c39ec4e52d387f074a3f2d753ef323d8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054839"
---
# <a name="properties-element-xmla"></a>Élément Properties (XMLA)
  Contient le code XML pour les propriétés de Analysis (XMLA) utilisées par le [Discover](../xml-elements-methods-discover.md) et [Execute](../xml-elements-methods-execute.md) méthodes.  
  
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Découvrir](../xml-elements-methods-discover.md), [exécuter](../xml-elements-methods-execute.md)|  
|Éléments enfants|[PropertyList](propertylist-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément `Properties` représente les propriétés XMLA utilisées pour contrôler des aspects des méthodes `Discover` et `Execute`, tels que la définition des informations requises pour se connecter à la source de données, la spécification du format de retour du jeu de résultats ou la spécification des paramètres régionaux selon lesquels les données doivent être mises en forme.  
  
 Les propriétés disponibles et leurs valeurs peuvent être obtenus en utilisant le type de demande DISCOVER_PROPERTIES avec la `Discover` (méthode).  
  
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
  
  
