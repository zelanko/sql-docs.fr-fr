---
title: "Axes, élément (XMLA) | Documents Microsoft"
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
apiname: Axes Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- Axes
- http://schemas.microsoft.com/analysisservices/2003/engine#Axes
- microsoft.xml.analysis.axes
- urn:schemas-microsoft-com:xml-analysis#Axes
helpviewer_keywords: Axes element
ms.assetid: 2005d06a-f8a2-4b4f-8c0d-2f7f73eb6f5c
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: facdfe5f8f4a03c5fcacff459dac78cb330f8f3b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="axes-element-xmla"></a>Élément Axes (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contient une collection de [axe](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) éléments représentant des données de l’axe contenues par un [racine](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) élément qui utilise le [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) type de données.  
  
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
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[racine](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Éléments enfants|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Sous le **Axes** élément, le **axe** éléments sont répertoriés dans l’ordre où ils apparaissent dans le jeu de données, en commençant à zéro. Le **AxisFormat** définition de la propriété XMLA détermine comment **axe** mise en forme des éléments. Pour plus d’informations sur la **AxisFormat** propriété, consultez [pris en charge les propriétés XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
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
  
|Opération| Description|  
|---------------|-----------------|  
|Membre|La plus petite unité d'un axe représentant le membre d'une hiérarchie de dimension.|  
|Membres|Une collection de **membre** les objets de la même hiérarchie de dimension.|  
|Tuple|Une collection de membres de hiérarchies de dimension différentes.|  
|Tuples|Une collection de **Tuple** objets avec la même dimensionnalité.|  
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
  
 Un client peut utiliser le **AxisFormat** propriété pour demander une représentation spécifique.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données MDDataSet &#40; XMLA &#41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
