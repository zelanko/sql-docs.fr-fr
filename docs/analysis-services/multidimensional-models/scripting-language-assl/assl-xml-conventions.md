---
title: Conventions ASSL XML | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- whitespace [Analysis Services Scripting Language]
- trailing whitespace
- XSD data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- cardinality [Analysis Services Scripting Language]
- white space [Analysis Services Scripting Language]
- ASSL, XML conventions
- defaults [Analysis Services Scripting Language]
- leading whitespace
- Analysis Services Scripting Language, XML conventions
- XML [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
- inherited defaults [Analysis Services Scripting Language]
ms.assetid: bce4edad-4420-41ce-9672-8c00c5c0dec6
caps.latest.revision: "24"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3b7e4c800454a2e2eddac81a2420b5a6d6436c70
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="assl-xml-conventions"></a>Conventions ASSL XML
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Analysis Services Scripting Language (ASSL) représente la hiérarchie des objets sous la forme d’un ensemble de types d’éléments, chacun d’eux définit les éléments enfants qu’ils peuvent contenir.  
  
 Pour représenter la hiérarchie d'objets, ASSL utilise les conventions XML suivantes :  
  
-   Tous les objets et propriétés sont représentés en tant qu'éléments, à l'exception des attributs XML standard tels que « xml:lang ».  
  
-   Les noms d’éléments et les valeurs d’énumération suivent la convention d’affectation de noms Microsoft .NET Framework de Pascal sans traits de soulignement de casse.  
  
-   La casse de toutes les valeurs est préservée. Les valeurs des énumérations respectent également la casse.  
  
 En plus de cette liste de conventions, Analysis Services suit également certaines conventions en matière de cardinalité, d'héritage, d'espaces, de types de données et de valeurs par défaut.  
  
## <a name="cardinality"></a>Cardinalité  
 Lorsque la cardinalité d'un élément est supérieure à 1, cela signifie qu'il existe une collection d'éléments XML qui englobe cet élément. Le nom de la collection correspond à la forme plurielle des éléments contenus dans la collection. Par exemple, le fragment XML suivant représente le **Dimensions** collection dans un **base de données** élément :  
  
 `<Database>`  
  
 `…`  
  
 `<Dimensions>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `</Dimensions>`  
  
 `</Database>`  
  
 ``  
  
 L'ordre d'apparition des éléments n'a pas d'importance.  
  
## <a name="inheritance"></a>Héritage  
 L'héritage est utilisé lorsqu'il existe des objets distincts dont les ensembles de propriétés se chevauchent en dépit de leur différence très marquée. Les cubes virtuels, les cubes liés et les cubes réguliers sont des exemples d'objets qui se chevauchent malgré leurs différences. Pour les objets distincts qui se chevauchent, Analysis Services utilise la norme **type** attribut à partir de la Namespace d’Instance XML pour indiquer l’héritage. Par exemple, le fragment XML suivant montre comment la **type** attribut identifie si un **Cube** élément hérite d’un cube régulier ou d’un cube virtuel :  
  
 `<Cubes>`  
  
 `<Cube xsi:type=”RegularCube”>`  
  
 `<Name>Sales</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `<Cube xsi:type=”VirtualCube”>`  
  
 `<Name>SalesAndInventory</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `</Cubes>`  
  
 ``  
  
 En règle générale, l'héritage n'est pas utilisé lorsque plusieurs types partagent un même nom de propriété. Par exemple, le **nom** et **ID** propriétés s’affichent dans de nombreux éléments, mais ces propriétés n’ont pas été promues à un type abstrait.  
  
## <a name="whitespace"></a>Espaces  
 Les espaces contenus dans la valeur d'un élément sont conservés. Toutefois, les espaces de début et de fin sont toujours supprimés. Par exemple, les éléments suivants comportent le même texte, mais le nombre d'espaces contenus dans le texte varie d'un élément à un autre, si bien que leurs valeurs sont considérées comme étant différentes :  
  
 `<Description>My text<Description>`  
  
 `<Description>My  text<Description>`  
  
 ``  
  
 Toutefois, les éléments suivants ne se distinguent qu'au niveau des espaces de début et de fin. Ils sont donc considérés comme des valeurs équivalentes :  
  
 `<Description>My text<Description>`  
  
 `<Description>  My text  <Description>`  
  
 ``  
  
## <a name="data-types"></a>Types de données  
 Analysis Services utilise les types de données XSD (XML Schema definition language) standard suivants :  
  
 **Int**  
 Valeur entière comprise entre -231 et 231 – 1.  
  
 **Long**  
 Valeur entière comprise entre -263 et 263 – 1.  
  
 **String**  
 Valeur de chaîne conforme aux règles globales suivantes :  
  
-   les caractères de contrôle sont supprimés ;  
  
-   les espaces de début et de fin sont supprimés ;  
  
-   les espaces internes sont conservés.  
  
 **Nom** et **ID** propriétés ont des limitations spéciales sur les caractères valides dans les éléments de chaîne. Pour plus d’informations sur **nom** et **ID** conventions, consultez [objets ASSL et caractéristiques des objets](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
 **DateTime**  
 A **DateTime** structure à partir de .NET Framework. A **DateTime** ne peut pas être NULL. La date la plus basse prise en charge par le **DataTime** type de données est le 1er janvier 1601, qui est disponible pour les programmeurs en tant que **DateTime.MinValue**. La date la plus bas pris en charge indique qu’un **DateTime** valeur est manquante.  
  
 **Booléen**  
 Énumération constituée de seulement deux valeurs, telles que {true, false} ou {0, 1}.  
  
## <a name="default-values"></a>Valeurs par défaut  
 Analysis Services prend en charge les valeurs par défaut répertoriées dans la table suivante :  
  
|Type de données XML|Valeur par défaut|  
|-------------------|-------------------|  
|**Booléen**|False|  
|**String**|"" (chaîne vide)|  
|**Entier** ou **Long**|0 (zéro)|  
|**Horodateur**|12:00:00 AM, 1/1/0001 (correspondant à un .NET Frameworks **System.DateTime** avec 0 battement)|  
  
 Un élément qui est présent mais vide est considéré comme ayant une valeur de chaîne null, et non la valeur par défaut.  
  
### <a name="inherited-defaults"></a>Valeurs par défaut héritées  
 Certaines propriétés définies au niveau d'un objet fournissent les valeurs par défaut des mêmes propriétés au niveau des objets enfants ou descendants. Par exemple, **Cube.StorageMode** fournit la valeur par défaut **Partition.StorageMode**. Les règles qu'Analysis Services applique pour les valeurs par défaut héritées sont les suivantes :  
  
-   Lorsque la propriété de l'objet enfant a la valeur NULL dans l'élément XML, sa valeur par défaut est la valeur héritée. Toutefois, si vous interrogez le serveur à propos de la valeur, le serveur renvoie la valeur NULL de l'élément XML.  
  
-   Il n'est pas possible de déterminer par programme si la propriété d'un objet enfant a été définie directement sur l'objet enfant ou héritée.  
  
 Certains éléments possèdent des valeurs par défaut définies qui s'appliquent lorsque ces éléments sont manquants. Par exemple, le **Dimension** dans le fragment XML suivant, les éléments sont équivalents bien qu’un **Dimension** élément contient un **Visible** l’élément, mais l’autre **Dimension** n’est pas le cas de l’élément.  
  
 `<Dimension>`  
  
 `<Name>Product</Name>`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `<Name>Product</ Name>`  
  
 `<Visible>true</Visible>`  
  
 `</Dimension>`  
  
 Pour plus d’informations sur les valeurs par défaut héritées, consultez [objets ASSL et caractéristiques des objets](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
  
