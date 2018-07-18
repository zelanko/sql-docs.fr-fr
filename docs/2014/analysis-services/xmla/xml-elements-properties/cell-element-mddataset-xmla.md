---
title: Élément (MDDataSet) (XMLA) de cellule | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Cell Element (MDDataSet)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cell
- http://schemas.microsoft.com/analysisservices/2003/engine#Cell
- urn:schemas-microsoft-com:xml-analysis#Cell
helpviewer_keywords:
- Cell element
ms.assetid: c4ea08a4-f653-4ade-be07-b91eb5b1ef32
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f07798a28c59597575de08bf5d0f3ea1d7087c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269505"
---
# <a name="cell-element-mddataset-xmla"></a>Élément Cell (MDDataSet) (XMLA)
  Contient des informations sur une cellule unique contenue par un parent [CellData](celldata-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CellData>  
   <Cell CellOrdinal="unsignedInt">  
      <!-- Zero or more cell property values -->  
      <!-- or -->  
      <Error>...</Error>  
   </Cell>  
</CellData>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CellData](celldata-element-xmla.md)|  
|Éléments enfants|Zéro ou plusieurs valeurs de propriété de cellule ou [erreur](error-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribute|Description|  
|---------------|-----------------|  
|CellOrdinal|Requis `unsignedInt` attribut. Position ordinale de la cellule dans le dataset multidimensionnel.|  
  
## <a name="remarks"></a>Notes  
 Dans l'élément `root` parent, l'élément `Axes` est suivi de l'élément `CellData`, collection d'éléments `Cell` contenant les valeurs de propriété de chaque cellule retournée dans le dataset multidimensionnel. L'élément `Cell` contient l'attribut `CellOrdinal` qui indique la position ordinale de base zéro de la cellule dans le dataset multidimensionnel, ainsi qu'un élément pour chaque valeur de propriété de cellule associée à la cellule. Chaque valeur de propriété de cellule dans l'élément `Cell` est définie par un élément XML distinct. La valeur de la propriété de cellule correspond aux données figurant dans l'élément XML et le nom de la propriété de cellule, tel que défini dans l'élément `CellInfo` de l'élément racine parent, correspond au nom de l'élément XML.  
  
 La syntaxe suivante décrit une valeur de propriété de cellule :  
  
```  
<CellProperty xsi:type="string">value</CellProperty>  
```  
  
 Le type de données d'une valeur de propriété de cellule est spécifié uniquement pour la propriété de cellule VALUE. Les types de données d'autres propriétés de cellule sont déterminés par la définition de propriété de cellule incluse dans l'élément `CellInfo`. Une valeur de propriété de cellule peut être exclue si une valeur par défaut a été spécifiée (en incluant un élément `Default` pour une définition de propriété de cellule contenue dans l'élément `CellInfo`) pour une propriété de cellule ou si aucune valeur par défaut n'a été spécifiée et si la valeur de la propriété de cellule a la valeur NULL.  
  
## <a name="cell-property-errors"></a>Erreurs de propriété de cellule  
 Si une propriété de cellule ne peut pas être retournée en raison d’une erreur se produit sur l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], telle qu’une erreur de calcul qui empêche que la valeur retournée pour une cellule donnée, un `Error` élément remplace la contenu de la propriété de cellule en question. L'exemple XML suivant décrit une erreur de propriété de cellule :  
  
```  
<Cell CellOrdinal="0">  
   <Value xsi:type="xsd:double">  
      <Error>  
         <ErrorCode>2148497527</ErrorCode>  
         <Description>Unknown error</Description>  
      </Error>  
   </Value>  
</Cell>  
```  
  
## <a name="calculating-cell-ordinal-values"></a>Calcul des valeurs ordinales d'une cellule  
 Les axes de référence d'une cellule peuvent être calculés sur la base d'une valeur d'attribut `CellOrdinal`. Conceptuellement, les cellules sont numérotées dans un jeu de données comme si le jeu de données ont été une *p*-tableau dimensionnel, où *p* est le nombre d’axes. Les cellules sont traitées dans l'ordre ligne-champ.  
  
 Imaginez une requête demandant quatre mesures sur les colonnes et une jointure croisée de deux états (State) avec quatre trimestres (Quarter) sur les lignes. En analysant le résultat du dataset ci-après, on constate que, pour la partie du résultat du dataset affichée en caractères gras, la propriété `CellOrdinal` correspond au jeu {9, 10, 11, 13, 14, 15, 17, 18, 19} puisque les cellules sont comptabilisées dans l'ordre ligne-champ en partant d'une valeur `CellOrdinal` égale à 0 pour la cellule supérieure gauche.  
  
|État|Quarter|Unit Sales|Store Cost|Store Sales|Sales Count|  
|-----------|-------------|----------------|----------------|-----------------|-----------------|  
|California|Q1|16890|14431.09|36175.2|5498|  
||2E TRIMESTRE|18052|15332.02|38396.75|5915|  
||Q3|18370|**15672.83**|**39394.05**|**6014**|  
||Q4|21436|**18094.5**|**45201.84**|**7015**|  
|Oregon|Q1|19287|**16081.07**|**40170.29**|**6184**|  
||2E TRIMESTRE|15079|12678.96|31772.88|4799|  
||Q3|16940|14273.78|35880.46|5432|  
||Q4|16353|13738.68|34453.44|5196|  
|Washington|Q1|30114|25240.08|63282.86|9906|  
||2E TRIMESTRE|29479|24953.25|62496.64|9654|  
||Q3|30538|25958.26|64997.38|10007|  
||Q4|34235|29172.72|73016.34|11217|  
  
 Si l'on applique la formule présentée dans la figure, l'axe k = 0 possède Uk = 4 membres et l'axe k = 1 possède Uk = 8 tuples. P = 2 correspond au nombre total d'axes dans la requête. Si l'on définit la cellule correspondant à {California, Q3, Store Cost} en tant que valeur S0, la somme de départ est i = 0 à 1. Pour i = 0, la valeur ordinale du tuple sur l'axe 0 de {Store Cost} est 1. Pour i = 1, l'ordinal du tuple de {CA, Q3} est 2.  
  
 Pour i = 0, Ei = 1, c’est le cas pour je = 0 la somme est 1 * 1 = 1 et pour je = 1, la somme est 2 (valeur ordinale du tuple) heures 4 (valeur Ei calculée comme 1 \* 4), ou 8. La somme de 1 + 8 est ensuite 9, soit l'ordinal de cette cellule.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant présente la structure de l'élément `Cell`, y compris les valeurs de propriété de cellule VALUE, FORMATTED_VALUE et FORMAT_STRING de chaque cellule.  
  
```  
<CellData>  
   <Cell CellOrdinal="0">  
      <Value xsi:type="xsd:double">16890</Value>  
      <FmtValue>16,890.00</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="1">  
      <Value xsi:type="xsd:int">50</Value>  
      <FmtValue>50</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="2">  
      <Value xsi:type="xsd:double">36175.2</Value>  
      <FmtValue>$36,175.20</FmtValue>  
      <FormatString>Currency</FormatString>  
   </Cell>  
</CellData>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données MDDataSet &#40;XMLA&#41;](../xml-data-types/mddataset-data-type-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
