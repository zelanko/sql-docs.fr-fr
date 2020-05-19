---
title: Types de données XPath (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3cd2e8af1630fed8dd996a951e904bef0266b300
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702982"
---
# <a name="xpath-data-types-sqlxml-40"></a>Types de données XPath (SQLXML 4.0)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath et le schéma XML (XSD) ont des types de données très différents. Par exemple, XPath n'affiche aucun type de données integer ou date tandis que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et XSD en possèdent un grand nombre. XSD utilise une précision à la nanoseconde pour les valeurs temporelles ; [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche au maximum une précision de 1/300ème de seconde. Par conséquent, le mappage d'un type de données à un autre n'est pas toujours possible. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le mappage des types de données aux types de données XSD, consultez [forçages de type de données et annotation sql : DataType &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 XPath possède trois types de données : `string`, `number` et `boolean`. Le type de données `number` est toujours une valeur à virgule flottante double précision IEEE 754. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `float(53)` type de données est le plus proche de XPath `number` . Toutefois, le type `float(53)` n'est pas exactement une valeur IEEE 754. Par exemple, ni la valeur NaN (Not-a-Number,), ni une valeur infinie n'est employée. Toute tentative de conversion d'une chaîne non numérique en type `number` et de division par zéro entraîne une erreur.  
  
## <a name="xpath-conversions"></a>Conversions XPath  
 Lorsque vous utilisez une requête XPath, telle que `OrderDetail[@UnitPrice > "10.0"]`, les conversions de type de données implicites et explicites peuvent modifier la signification de la requête de manière subtile. Par conséquent, il est primordial de comprendre la manière dont les types de données Xpath sont implémentés. La spécification du langage XPath, XML Path Language (XPath) version 1,0 W3C proposed Recommendation 8 octobre 1999, est disponible sur le site Web du W3C à l’adresse http://www.w3.org/TR/1999/PR-xpath-19991008.html .  
  
 Les opérateurs XPath sont divisés en quatre catégories :  
  
-   Opérateurs booléens (et, ou)  
  
-   Opérateurs relationnels ( \< , >, \< =, >=)  
  
-   Opérateurs d'égalité (=, !=)  
  
-   Opérateurs arithmétiques (+, -, *, div, mod)  
  
 Chaque catégorie d'opérateur convertit ses opérandes de manière distincte. Les opérateurs XPath convertissent implicitement leurs opérandes si cela est nécessaire. Les opérateurs arithmétiques convertissent leurs opérandes en type `number` et génèrent une valeur numérique. Les opérateurs booléens convertissent leurs opérandes en `boolean` et génèrent une valeur booléenne. Les opérateurs relationnels et d'égalité génèrent une valeur booléenne. Toutefois, ils suivent des règles de conversion différentes en fonction des types de données d'origine de leurs opérandes comme le montre le tableau ci-après.  
  
|Opérande|Opérateur relationnel|Opérateur d'égalité|  
|-------------|-------------------------|-----------------------|  
|Les deux opérandes sont des éléments node-set.|TRUE si et uniquement s'il existe un nœud dans un jeu et un nœud dans le deuxième jeu justifiant que la comparaison de leurs valeurs `string` soit TRUE.|Idem.|  
|L'un est un élément node-set, l'autre est de type `string`.|TRUE si et uniquement s'il existe un nœud dans l'élément node-set de sorte que, en cas de conversion en type `number`, sa comparaison avec la valeur `string` convertie en `number` est TRUE.|TRUE si et uniquement s'il existe un nœud dans l'élément node-set de sorte que, en cas de conversion en type `string`, sa comparaison avec la valeur `string` est TRUE.|  
|L'un est un élément node-set, l'autre est de type `number`.|TRUE si et uniquement s'il existe un nœud dans l'élément node-set de sorte que, en cas de conversion en type `number`, sa comparaison avec la valeur `number` est TRUE.|Idem.|  
|L'un est un élément node-set, l'autre est de type `boolean`.|TRUE si et uniquement s'il existe un nœud dans l'élément node-set de sorte que, en cas de conversion en type `boolean`, puis en type `number`, sa comparaison avec la valeur `boolean` convertie en `number` est TRUE.|TRUE si et uniquement s'il existe un nœud dans l'élément node-set de sorte que, en cas de conversion en type `boolean`, sa comparaison avec la valeur `boolean` est TRUE.|  
|Ni l'un ni l'autre n'est un élément node-set.|Convertissez les deux opérandes en type `number`, puis comparez-les.|Convertissez les deux opérandes en un type commun, puis comparez-les. Convertissez en type `boolean` si l'une des valeurs est de type `boolean`, en `number` si l'une des valeurs est de type `number` ; sinon, effectuez une conversion en type `string`.|  
  
> [!NOTE]  
>  Parce que les opérateurs relationnels XPath convertissent toujours leurs opérandes en `number`, les comparaisons de valeurs `string` ne sont pas possibles. Pour inclure des comparaisons de date, SQL Server 2000 propose la variante suivante par rapport à la recommandation XPath : lorsqu'un opérateur relationnel compare une valeur `string` à une autre valeur `string`, un élément node-set à une valeur `string`, ou deux éléments node-set à valeur de chaîne entre eux, une comparaison de la valeur `string` (et non une comparaison de `number`) a lieu.  
  
## <a name="node-set-conversions"></a>Conversions des éléments node-set  
 Les conversions des éléments node-set ne sont pas toujours intuitives. Un élément node-set est converti en type `string` par extraction de la valeur de chaîne du premier nœud du jeu uniquement. Pour être converti en type `number`, un élément node-set est d'abord converti en type `string`, puis le type `string` est converti en type `number`. Pour convertir un élément node-set en type `boolean`, vous devez d'abord le tester pour vérifier s'il existe.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne procède à aucune sélection positionnelle sur les éléments node-set : par exemple, la requête XPath `Customer[3]` désigne le troisième client ; ce type de sélection positionnelle n'est pas pris en charge dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, les conversions d'élément node-set en `string` ou d'élément node-set en `number`, telles que décrites dans la recommandation XPath, ne sont pas implémentées. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise une sémantique « quelconque » partout où la recommandation XPath spécifie la « première » sémantique. Par exemple, en fonction de la spécification XPath du W3C, la requête XPath `Order[OrderDetail/@UnitPrice > 10.0]` sélectionne les commandes avec le premier **OrderDetail** dont la valeur **UnitPrice** est supérieure à 10,0. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cette requête XPath sélectionne les commandes avec un **OrderDetail** dont la valeur **UnitPrice** est supérieure à 10,0.  
  
 La conversion en valeur `boolean` implique un test de vérification d'existence ; la requête XPath `Products[@Discontinued=true()]` équivaut donc à l'expression SQL « Products.Discontinued is not null » et non à l'expression SQL « Products.Discontinued = 1 ». Pour que la requête équivaille à la dernière expression SQL, convertissez avant tout l'élément node-set en type non `boolean`, tel que `number`. Par exemple : `Products[number(@Discontinued) = true()]`.  
  
 Du fait que la plupart des opérateurs sont définis pour être vrais (TRUE) s'ils le sont pour un nœud quelconque ou l'un des nœuds de l'élément node-set, ces opérations prennent toujours la valeur FALSE si l'élément node-set est vide. Ainsi donc, si A est vide, `A = B` et `A != B` ont tous les deux la valeur FALSE et `not(A=B)` et `not(A!=B)` ont la valeur TRUE.  
  
 En règle générale, un attribut ou un élément mappé à une colonne existe si la valeur de cette colonne dans la base de données n'est pas `null`. Les éléments mappés aux lignes existent si tous leurs enfants existent.  
  
> [!NOTE]  
>  Les éléments annotés avec `is-constant` existent toujours. Par conséquent, les prédicats XPath ne peuvent être utilisés dans des éléments `is-constant`.  
  
 Lorsque vous convertissez un élément node-set en type `string` ou `number`, son type XDR (le cas échéant) est examiné dans le schéma annoté et utilisé pour déterminer la conversion requise.  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>Mappage des types de données XDR et XPath  
 Le type de données XPath d’un nœud est dérivé du type de données XDR dans le schéma, comme indiqué dans le tableau suivant (le nœud **EmployeeID** est utilisé à des fins d’illustration).  
  
|Type de données XDR|Équivalent<br /><br /> Type de données XPath|Conversion SQL Server utilisée|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|N/A|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8|nombre|CONVERT(float(53), EmployeeID)|  
|id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid|string|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|N/A (aucun type de données XPath n'équivaut au type de données XDR fixed14.4)|CONVERT(money, EmployeeID)|  
|date|string|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|time<br /><br /> time.tz|string|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 Les conversions de date et d’heure sont conçues pour fonctionner, que la valeur soit stockée dans la base de données à l’aide du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` type de données ou d’un `string` . Notez que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` type de données n’utilise pas `timezone` et a une précision inférieure à celle du `time` type de données XML. Pour inclure le type de données `timezone` ou apporter une précision supplémentaire, stockez les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec un type `string`.  
  
 Lorsque vous convertissez un nœud du type de données XDR en type de données XPath, une conversion supplémentaire est parfois nécessaire (d'un type de données XPath vers un autre type de données XPath). Par exemple, imaginez la requête XPath suivante :  
  
```  
(@m + 3) = 4  
```  
  
 Si @m est du `fixed14.4` type de données XDR, la conversion du type de données XDR en type de données XPath s’effectue à l’aide de :  
  
```  
CONVERT(money, m)  
```  
  
 Dans le cadre de cette conversion, le nœud `m` passe du type `fixed14.4` au type `money`. Toutefois, l'ajout de la valeur 3 nécessite une autre conversion :  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 L'expression XPath est évaluée comme suit :  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 Comme le montre le tableau ci-dessous, il s'agit de la même conversion que celle appliquée à d'autres expressions XPath (telles que des littéraux ou des expressions composées).  
  
||||||  
|-|-|-|-|-|  
||X est inconnu|X est de type `string`|X est de type `number`|X est de type `boolean`|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN (X) > 0|X != 0|-|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>R. Convertir un type de données dans une requête XPath  
 Dans la requête XPath suivante spécifiée par rapport à un schéma XSD annoté, la requête sélectionne tous les nœuds **Employee** avec la valeur d’attribut **EmployeeID** de E-1, où « e- » est le préfixe spécifié à l’aide de l' `sql:id-prefix` annotation.  
  
 `Employee[@EmployeeID="E-1"]`  
  
 Le prédicat dans la requête équivaut à l'expression SQL suivante :  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 **EmployeeID** étant l’une des `id` valeurs de `idref` type de données (,,,, etc. `idrefs` `nmtoken` `nmtokens` ) dans le schéma XSD, **EmployeeID** est converti en `string` type de données XPath à l’aide des règles de conversion décrites précédemment.  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 Le préfixe  « E - » est ajouté à la chaîne et le résultat est ensuite comparé avec `N'E-1'`.  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. Effectuer plusieurs conversions de types de données dans une requête XPath.  
 Examinez la requête XPath suivante définie par rapport à un schéma XSD annoté : `OrderDetail[@UnitPrice * @OrderQty > 98]`  
  
 Cette requête XPath retourne tous les éléments ** \< OrderDetail>** qui satisfont le prédicat `@UnitPrice * @OrderQty > 98` . Si **UnitPrice** est annoté avec un `fixed14.4` type de données dans le schéma annoté, ce prédicat équivaut à l’expression SQL :  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 Lors de la conversion des valeurs dans la requête XPath, la première conversion convertit le type de données XDR en type de données XPath. Étant donné que le type de données XSD de **UnitPrice** est `fixed14.4` , comme décrit dans le tableau précédent, il s’agit de la première conversion utilisée :  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Du fait que les opérateurs arithmétiques convertissent leurs opérandes en type de données XPath `number`, la deuxième conversion (d'un type de données XPath à un autre) est appliquée là où la valeur est convertie en `float(53)` (`float(53)` est très proche du type de données XPath `number`) :  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 En supposant que l’attribut **OrderQty** n’a pas de type de données XSD, **OrderQty** est converti en `number` type de données XPath en une seule conversion :  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 La valeur 98 est également convertie en type de données XPath `number` :  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  Si le type de données XSD appliqué au schéma est incompatible avec le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous-jacent dans la base de données, ou si une conversion de type de données XPath impossible est réalisée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner une erreur. Par exemple, si l’attribut **EmployeeID** est annoté avec `id-prefix` annotation, le XPath `Employee[@EmployeeID=1]` génère une erreur, car **EmployeeID** possède l' `id-prefix` annotation et ne peut pas être converti en `number` .  
  
  
