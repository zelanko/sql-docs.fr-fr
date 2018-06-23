---
title: L’élément Properties (XMLA) | Documents Microsoft
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
caps.latest.revision: 30
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 66accb9aab2c970c1fd09b1e14408b5585269d7f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040047"
---
# <a name="properties-element-xmla"></a>Élément Properties (XMLA)
  Contient du code XML pour les propriétés d’analyse (XMAL) utilisées par le [Discover](../xml-elements-methods-discover.md) et [Execute](../xml-elements-methods-execute.md) méthodes.  
  
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
  
 Les propriétés disponibles et leurs valeurs peuvent être obtenues en utilisant le type de demande DISCOVER_PROPERTIES avec la `Discover` (méthode).  
  
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
  
  