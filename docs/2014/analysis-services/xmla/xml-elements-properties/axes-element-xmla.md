---
title: Axes, élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Axes Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Axes
- http://schemas.microsoft.com/analysisservices/2003/engine#Axes
- microsoft.xml.analysis.axes
- urn:schemas-microsoft-com:xml-analysis#Axes
helpviewer_keywords:
- Axes element
ms.assetid: 2005d06a-f8a2-4b4f-8c0d-2f7f73eb6f5c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bdb5aa48dd3a65f99b424274fdb89b3aee8c9591
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094905"
---
# <a name="axes-element-xmla"></a>Élément Axes (XMLA)
  Contient une collection de [axe](axis-element-xmla.md) éléments représentant les données d’axe contenues par un [racine](root-element-xmla.md) élément qui utilise le [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) type de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <Axes>  
      <Axis>...</Axis>  
   </Axes>  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Racine](root-element-xmla.md)|  
|Éléments enfants|[Axis](axis-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Sous l'élément `Axes`, les éléments `Axis` sont répertoriés dans l'ordre où ils apparaissent dans le dataset, en commençant à zéro. Le paramètre de propriété XMLA `AxisFormat` détermine comment les éléments `Axis` sont mis en forme. Pour plus d’informations sur la `AxisFormat` propriété, consultez [propriétés XMLA prises en charge &#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md).  
  
 Un axe représente un jeu de tuples dans lequel tous les tuples ont la même dimensionnalité. Un jeu peut être représenté de plusieurs façons offrant différents avantages. Par exemple, le jeu de quatre tuples suivant peut être représenté comme une collection de tuples à deux dimensions ou un produit cartésien de deux ensembles unidimensionnels.  
  
|1999|1999|2000|2000|  
|----------|----------|----------|----------|  
|Réel|Budget|Réel|Budget|  
  
 Ce jeu de tuples peut être représenté comme une collection de tuples à deux dimensions :  
  
```  
{ ( 1999, Actual ), ( 1999, Budget ), ( 2000, Actual ), ( 2000, Budget ) }  
```  
  
 Ce jeu peut également être représenté comme un produit cartésien de deux ensembles unidimensionnels :  
  
```  
{ 1999, 2000 } x { Actual, Budget }  
```  
  
 La première représentation, les tuples à deux dimensions, est plus simple à utiliser pour les outils clients. La seconde représentation, un produit cartésien d'ensembles unidimensionnels, utilise moins d'espace et conserve la nature multidimensionnelle du jeu.  
  
 Le tableau suivant répertorie les opérations qui peuvent être utilisées pour définir et caractériser la structure et les membres d'un axe.  
  
|Opération|Description|  
|---------------|-----------------|  
|Membre|La plus petite unité d'un axe représentant le membre d'une hiérarchie de dimension.|  
|Membres|Une collection d'objets `Member` de la même hiérarchie de dimension.|  
|Tuple|Une collection de membres de hiérarchies de dimension différentes.|  
|Tuples|Une collection d'objets `Tuple` de même dimensionnalité.|  
|Union|Une union d'ensembles.|  
|CrossJoin|Un produit cartésien d'ensembles.|  
  
 Ces opérations traduisent les tuples à deux dimensions et le produit cartésien d'ensembles unidimensionnels de la façon suivante.  
  
## <a name="two-dimensional-tuples"></a>Tuples à deux dimensions  
  
```  
Tuples (  
   Tuple( Member(1999), Member(Actual) ),  
   Tuple( Member(1999), Member(Budget) ),  
   Tuple( Member(2000), Member(Actual) ),  
   Tuple( Member(2000), Member(Budget) )  
```  
  
## <a name="cartesian-product-of-one-dimensional-sets"></a>Produit cartésien d'ensembles unidimensionnels  
  
```  
CrossProduct (  
   Members( Member(1999), Member(2000) ),  
   Members( Member(Actual), Member(Budget) )  
```  
  
 Un client peut utiliser la propriété `AxisFormat` pour demander une représentation spécifique.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données MDDataSet &#40;XMLA&#41;](../xml-data-types/mddataset-data-type-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
