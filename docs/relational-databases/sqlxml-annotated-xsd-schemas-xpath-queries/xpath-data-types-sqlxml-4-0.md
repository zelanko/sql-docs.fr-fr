---
title: Types de données XPath (SQLXML)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 089b2b006d0159c63e480c8627762ac37dec98b8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75247092"
---
# <a name="xpath-data-types-sqlxml-40"></a>Types de données XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath et le schéma XML (XSD) ont des types de données très différents. Par exemple, XPath n'affiche aucun type de données integer ou date tandis que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et XSD en possèdent un grand nombre. XSD utilise une précision à la nanoseconde pour les valeurs temporelles ; [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche au maximum une précision de 1/300ème de seconde. Par conséquent, le mappage d'un type de données à un autre n'est pas toujours possible. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le mappage des types de données aux types de données XSD, consultez [forçages de type de données et annotation sql : datatype &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 XPath a trois types de données : **chaîne**, **nombre**et **booléen**. Le type de données Number est toujours un **nombre** à virgule flottante double précision IEEE 754. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de données **float (53)** est le plus proche du **nombre**XPath. Toutefois, **float (53)** n’est pas exactement IEEE 754. Par exemple, ni la valeur NaN (Not-a-Number,), ni une valeur infinie n'est employée. Toute tentative de conversion d’une chaîne non numérique en **nombre** et d’une tentative de division par zéro provoque une erreur.  
  
## <a name="xpath-conversions"></a>Conversions XPath  
 Lorsque vous utilisez une requête XPath, telle que `OrderDetail[@UnitPrice > "10.0"]`, les conversions de type de données implicites et explicites peuvent modifier la signification de la requête de manière subtile. Par conséquent, il est primordial de comprendre la manière dont les types de données Xpath sont implémentés. La spécification du langage XPath, XML Path Language (XPath) version 1,0 W3C proposed Recommendation 8 octobre 1999, est disponible sur le site Web http://www.w3.org/TR/1999/PR-xpath-19991008.htmldu W3C à l’adresse.  
  
 Les opérateurs XPath sont divisés en quatre catégories :  
  
-   Opérateurs booléens (et, ou)  
  
-   Opérateurs relationnels (\<, >, \<=, >=)  
  
-   Opérateurs d'égalité (=, !=)  
  
-   Opérateurs arithmétiques (+, -, *, div, mod)  
  
 Chaque catégorie d'opérateur convertit ses opérandes de manière distincte. Les opérateurs XPath convertissent implicitement leurs opérandes si cela est nécessaire. Les opérateurs arithmétiques convertissent leurs opérandes en **nombres**et génèrent une valeur numérique. Les opérateurs booléens convertissent leurs opérandes en **booléen**et génèrent une valeur booléenne. Les opérateurs relationnels et d'égalité génèrent une valeur booléenne. Toutefois, ils suivent des règles de conversion différentes en fonction des types de données d'origine de leurs opérandes comme le montre le tableau ci-après.  
  
|Opérande|Opérateur relationnel|Opérateur d'égalité|  
|-------------|-------------------------|-----------------------|  
|Les deux opérandes sont des éléments node-set.|TRUE si et seulement s’il existe un nœud dans un jeu et un nœud dans le deuxième jeu, de telle sorte que la comparaison de leurs valeurs de **chaîne** est true.|Idem.|  
|L’un est un ensemble de nœuds, l’autre une **chaîne**.|TRUE si et seulement s’il existe un nœud dans l’élément node-set de sorte que, lorsqu’il est converti en **Number**, sa comparaison avec la **chaîne** convertie en **Number** est true.|TRUE si et seulement s’il existe un nœud dans l’élément node-set de sorte que, en cas de conversion en **chaîne**, la comparaison avec la **chaîne** est true.|  
|L’un est un ensemble de nœuds, l’autre un **nombre**.|TRUE si et seulement s’il existe un nœud dans l’élément node-set de sorte que, lorsqu’il est converti en **Number**, sa comparaison avec le **nombre** est true.|Idem.|  
|L’un est un ensemble de nœuds, l’autre un **booléen**.|TRUE si et seulement s’il existe un nœud dans l’élément node-set de sorte que, en cas de conversion en valeur **booléenne** , puis en **nombre**, la comparaison avec la **valeur booléenne** convertie en **nombre** est true.|TRUE si et seulement s’il existe un nœud dans l’élément node-set de sorte que, en cas de conversion en **valeur booléenne**, la comparaison avec la valeur **booléenne** est true.|  
|Ni l'un ni l'autre n'est un élément node-set.|Convertissez les deux opérandes en **nombre** , puis comparez-les.|Convertissez les deux opérandes en un type commun, puis comparez-les. Convertit en **valeur booléenne** si l’un des deux est **Boolean**, **Number** si l’un ou l’autre est **Number**; Sinon, convertir en **chaîne**.|  
  
> [!NOTE]  
>  Étant donné que les opérateurs relationnels XPath convertissent toujours leurs opérandes en **nombre**, les comparaisons de **chaînes** ne sont pas possibles. Pour inclure des comparaisons de dates, SQL Server 2000 offre cette variation à la spécification XPath : lorsqu’un opérateur relationnel compare une **chaîne** à une **chaîne, un**ensemble de nœuds à une **chaîne**ou un node-Valued node-set à un ensemble de nœuds à valeur de chaîne, une comparaison de **chaînes** (et non une comparaison de **nombres** ) est effectuée.  
  
## <a name="node-set-conversions"></a>Conversions des éléments node-set  
 Les conversions des éléments node-set ne sont pas toujours intuitives. Une définition de nœud est convertie en **chaîne** en utilisant uniquement la valeur de chaîne du premier nœud du jeu. Une définition de nœud est convertie en **nombre** en la convertissant en **chaîne**, puis en convertissant la **chaîne** en **nombre**. Une définition de nœud est convertie en valeur **booléenne** en testant son existence.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne procède à aucune sélection positionnelle sur les éléments node-set : par exemple, la requête XPath `Customer[3]` désigne le troisième client ; ce type de sélection positionnelle n'est pas pris en charge dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, les conversions node-set-to-**String** ou node-set-to-**Number** , comme décrit dans la spécification XPath, ne sont pas implémentées. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise une sémantique « quelconque » partout où la recommandation XPath spécifie la « première » sémantique. Par exemple, en fonction de la spécification XPath du W3C, la `Order[OrderDetail/@UnitPrice > 10.0]` requête XPath sélectionne les commandes avec le premier **OrderDetail** dont la valeur **UnitPrice** est supérieure à 10,0. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette requête XPath sélectionne les commandes avec un **OrderDetail** dont la valeur **UnitPrice** est supérieure à 10,0.  
  
 La conversion en **valeur booléenne** génère un test d’existence ; par conséquent, la requête `Products[@Discontinued=true()]` XPath équivaut à l’expression SQL « Products. Discontinued is not null », et non à l’expression SQL « Products. Discontinued = 1 ». Pour que la requête soit équivalente à la dernière expression SQL, convertissez d’abord node-set en type non**booléen** , tel que **Number**. Par exemple : `Products[number(@Discontinued) = true()]`.  
  
 Du fait que la plupart des opérateurs sont définis pour être vrais (TRUE) s'ils le sont pour un nœud quelconque ou l'un des nœuds de l'élément node-set, ces opérations prennent toujours la valeur FALSE si l'élément node-set est vide. Ainsi donc, si A est vide, `A = B` et `A != B` ont tous les deux la valeur FALSE et `not(A=B)` et `not(A!=B)` ont la valeur TRUE.  
  
 En général, un attribut ou un élément qui est mappé à une colonne existe si la valeur de cette colonne dans la base de données n’est pas **null**. Les éléments mappés aux lignes existent si tous leurs enfants existent.  
  
> [!NOTE]  
>  Les éléments annotés avec **is-constant** existent toujours. Par conséquent, les prédicats XPath ne peuvent pas être utilisés sur des éléments **is-constants** .  
  
 Lorsqu’un élément node-set est converti en **chaîne** ou en **nombre**, son type XDR (le cas échéant) est inspecté dans le schéma annoté et ce type est utilisé pour déterminer la conversion requise.  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>Mappage des types de données XDR et XPath  
 Le type de données XPath d’un nœud est dérivé du type de données XDR dans le schéma, comme indiqué dans le tableau suivant (le nœud **EmployeeID** est utilisé à des fins d’illustration).  
  
|Type de données XDR|Équivalent<br /><br /> Type de données XPath|Conversion SQL Server utilisée|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|NON APPLICABLE|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8|nombre|CONVERT(float(53), EmployeeID)|  
|id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid|string|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|N/A (aucun type de données XPath n'équivaut au type de données XDR fixed14.4)|CONVERT(money, EmployeeID)|  
|Date|string|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|time<br /><br /> time.tz|string|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 Les conversions de date et d’heure sont conçues pour fonctionner, que la valeur soit stockée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]la base de données à l’aide du type de données **DateTime** ou d’une **chaîne**. Notez que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de données **DateTime** n’utilise pas **TimeZone** et a une précision inférieure à celle du type de données **Time** XML. Pour inclure le type de données **TimeZone** ou une précision supplémentaire, stockez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les données dans à l’aide d’un type **chaîne** .  
  
 Lorsque vous convertissez un nœud du type de données XDR en type de données XPath, une conversion supplémentaire est parfois nécessaire (d'un type de données XPath vers un autre type de données XPath). Par exemple, imaginez la requête XPath suivante :  
  
```  
(@m + 3) = 4  
```  
  
 Si @m est du type de données XDR **fixe 14,4** , la conversion du type de données XDR en type de données XPath s’effectue à l’aide de :  
  
```  
CONVERT(money, m)  
```  
  
 Dans cette conversion, le nœud `m` est converti de **14,4** en **argent**. Toutefois, l'ajout de la valeur 3 nécessite une autre conversion :  
  
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
||X est inconnu|X est une **chaîne**|X est un **nombre**|X est **booléen**|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN (X) > 0|X != 0|-|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>R. Convertir un type de données dans une requête XPath  
 Dans la requête XPath suivante spécifiée par rapport à un schéma XSD annoté, la requête sélectionne tous les nœuds **Employee** avec la valeur d’attribut **EmployeeID** de E-1, où « e- » est le préfixe spécifié à l’aide de l’annotation **SQL : id-prefix** .  
  
 `Employee[@EmployeeID="E-1"]`  
  
 Le prédicat dans la requête équivaut à l'expression SQL suivante :  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 **EmployeeID** étant l’un des types de données **ID** (**IDREF**, **IDREFS**, **NMTOKEN**, **NMTOKENS**, etc.) dans le schéma XSD, **EmployeeID** est converti en type de données XPath **String** à l’aide des règles de conversion décrites précédemment.  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 Le préfixe  « E - » est ajouté à la chaîne et le résultat est ensuite comparé avec `N'E-1'`.  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. Effectuer plusieurs conversions de types de données dans une requête XPath.  
 Examinez la requête XPath suivante définie par rapport à un schéma XSD annoté : `OrderDetail[@UnitPrice * @OrderQty > 98]`  
  
 Cette requête XPath retourne tous les ** \<éléments OrderDetail>** qui satisfont le `@UnitPrice * @OrderQty > 98`prédicat. Si **UnitPrice** est annoté avec un type de données **14,4 fixe** dans le schéma annoté, ce prédicat équivaut à l’expression SQL :  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 Lors de la conversion des valeurs dans la requête XPath, la première conversion convertit le type de données XDR en type de données XPath. Étant donné que le type de données XSD de **UnitPrice** est **fixé à 14,4**, comme décrit dans le tableau précédent, il s’agit de la première conversion utilisée :  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Étant donné que les opérateurs arithmétiques convertissent leurs opérandes en type de données XPath **Number** , la deuxième conversion (d’un type de données XPath à un autre type de données XPath) est appliquée dans laquelle la valeur est convertie en valeur **float (53)** (**float (53)** est proche du type de données XPath **Number** ) :  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 En supposant que l’attribut **OrderQty** n’a pas de type de données XSD, **OrderQty** est converti en un type de données XPath **Number** en une seule conversion :  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 De même, la valeur 98 est convertie en type de données XPath **Number** :  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  Si le type de données XSD appliqué au schéma est incompatible avec le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous-jacent dans la base de données, ou si une conversion de type de données XPath impossible est réalisée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner une erreur. Par exemple, si l’attribut **EmployeeID** est annoté avec l’annotation **id-prefix** , le XPath `Employee[@EmployeeID=1]` génère une erreur, car **EmployeeID** a l’annotation **id-prefix** et ne peut pas être convertie en **Number**.  
  
  
