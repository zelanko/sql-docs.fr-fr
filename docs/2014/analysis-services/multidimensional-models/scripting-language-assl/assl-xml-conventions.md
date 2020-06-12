---
title: Conventions XML ASSL | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
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
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b70742b07fd6450b01cf205147a05f40c4b6121
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545671"
---
# <a name="assl-xml-conventions"></a>Conventions ASSL XML
  Le langage de script ASSL (Analysis Services Scripting Language) représente la hiérarchie d'objets comme un ensemble de types d'élément, chacun d'entre eux définissant les éléments enfants qu'il contient.  
  
 Pour représenter la hiérarchie d'objets, ASSL utilise les conventions XML suivantes :  
  
-   Tous les objets et propriétés sont représentés en tant qu’éléments, à l’exception des attributs XML standard tels que « XML : lang ».  
  
-   Les noms d'élément et les valeurs d'énumération suivent la convention d'affectation de noms Microsoft .NET Framework, à savoir, une casse Pascal sans traits de soulignement.  
  
-   La casse de toutes les valeurs est préservée. Les valeurs des énumérations respectent également la casse.  
  
 En plus de cette liste de conventions, Analysis Services suit également certaines conventions en matière de cardinalité, d'héritage, d'espaces, de types de données et de valeurs par défaut.  
  
## <a name="cardinality"></a>Cardinalité  
 Lorsque la cardinalité d'un élément est supérieure à 1, cela signifie qu'il existe une collection d'éléments XML qui englobe cet élément. Le nom de la collection correspond à la forme plurielle des éléments contenus dans la collection. Par exemple, le fragment XML suivant représente la collection `Dimensions` au sein d'un élément `Database` :  
  
 `<Database>`  
  
 `...`  
  
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
 L'héritage est utilisé lorsqu'il existe des objets distincts dont les ensembles de propriétés se chevauchent en dépit de leur différence très marquée. Les cubes virtuels, les cubes liés et les cubes réguliers sont des exemples d'objets qui se chevauchent malgré leurs différences. Pour les objets distincts qui se chevauchent, Analysis Services fait appel à l'attribut `type` standard de l'espace de noms d'instances XML pour indiquer l'héritage. Par exemple, le fragment XML suivant indique comment l'attribut `type` détermine si un élément `Cube` hérite d'un cube régulier ou d'un cube virtuel :  
  
 `<Cubes>`  
  
 `<Cube xsi:type="RegularCube">`  
  
 `<Name>Sales</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `<Cube xsi:type="VirtualCube">`  
  
 `<Name>SalesAndInventory</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `</Cubes>`  
  
 ``  
  
 En règle générale, l'héritage n'est pas utilisé lorsque plusieurs types partagent un même nom de propriété. Par exemple, les propriétés `Name` et `ID` apparaissent dans de nombreux éléments, mais ces propriétés n'ont pas été promues en type abstrait.  
  
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
  
 `Int`  
 Valeur entière comprise entre-231 et 231-1.  
  
 `Long`  
 Valeur entière comprise entre-263 et 263-1.  
  
 `String`  
 Valeur de chaîne conforme aux règles globales suivantes :  
  
-   les caractères de contrôle sont supprimés ;  
  
-   les espaces de début et de fin sont supprimés ;  
  
-   les espaces internes sont conservés.  
  
 Les propriétés `Name` et `ID` imposent des limitations spéciales en matière de validité des caractères dans les éléments de chaîne. Pour plus d’informations sur `Name` les `ID` conventions et, consultez [objets ASSL et caractéristiques](assl-objects-and-object-characteristics.md)de l’objet.  
  
 `DateTime`  
 `DateTime`Structure de l' .NET Framework. Une valeur `DateTime` ne peut pas être NULL. La date la plus reculée prise en charge par le type de données `DataTime` est le 1er janvier 1601, qui est accessible aux programmeurs via `DateTime.MinValue`. La présence de cette date indique qu'il manque une valeur `DateTime`.  
  
 `Boolean`  
 Énumération constituée de seulement deux valeurs, telles que {true, false} ou {0, 1}.  
  
## <a name="default-values"></a>Valeurs par défaut  
 Analysis Services prend en charge les valeurs par défaut répertoriées dans la table suivante :  
  
|Type de données XML|Valeur par défaut|  
|-------------------|-------------------|  
|`Boolean`|False|  
|`String`|"" (chaîne vide)|  
|`Integer` ou `Long`|0 (zéro)|  
|`Timestamp`|12:00:00 AM, 1/1/0001 (correspondant à un .NET Framework `System.DateTime` avec 0 graduations)|  
  
 Un élément qui est présent mais vide est considéré comme ayant une valeur de chaîne null, et non la valeur par défaut.  
  
### <a name="inherited-defaults"></a>Valeurs par défaut héritées  
 Certaines propriétés définies au niveau d'un objet fournissent les valeurs par défaut des mêmes propriétés au niveau des objets enfants ou descendants. Par exemple, `Cube.StorageMode` fournit la valeur par défaut de `Partition.StorageMode`. Les règles qu'Analysis Services applique pour les valeurs par défaut héritées sont les suivantes :  
  
-   Lorsque la propriété de l'objet enfant a la valeur NULL dans l'élément XML, sa valeur par défaut est la valeur héritée. Toutefois, si vous interrogez le serveur à propos de la valeur, le serveur renvoie la valeur NULL de l'élément XML.  
  
-   Il n'est pas possible de déterminer par programme si la propriété d'un objet enfant a été définie directement sur l'objet enfant ou héritée.  
  
 Certains éléments possèdent des valeurs par défaut définies qui s'appliquent lorsque ces éléments sont manquants. Par exemple, dans le fragment XML suivant, les éléments `Dimension` sont équivalents bien qu'un élément `Dimension` contienne un élément `Visible` mais que l'autre élément `Dimension` n'en contient pas.  
  
 `<Dimension>`  
  
 `<Name>Product</Name>`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `<Name>Product</ Name>`  
  
 `<Visible>true</Visible>`  
  
 `</Dimension>`  
  
 Pour plus d’informations sur les valeurs par défaut héritées, consultez [objets ASSL et caractéristiques](assl-objects-and-object-characteristics.md)de l’objet.  
  
  
