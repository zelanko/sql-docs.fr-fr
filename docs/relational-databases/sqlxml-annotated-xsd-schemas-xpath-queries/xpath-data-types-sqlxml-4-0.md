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
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "75247092"
---
# <a name="xpath-data-types-sqlxml-40"></a>Types de données XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath, et XML Schema (XSD) ont des types de données très différents. Par exemple, XPath n'affiche aucun type de données integer ou date tandis que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et XSD en possèdent un grand nombre. XSD utilise une précision à la nanoseconde pour les valeurs temporelles ; [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche au maximum une précision de 1/300ème de seconde. Par conséquent, le mappage d'un type de données à un autre n'est pas toujours possible. Pour plus d’informations sur les types de données cartographiques [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux types de données XSD, voir Data Type [Coercions et l’annotation sql:datatype &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 XPath a trois types de données: **chaîne**, **nombre**, et **boolean**. Le type de données **de nombre** est toujours un point flottant à double précision IEEE 754. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de données **flottant(53)** est le plus proche du **numéro**XPath . Cependant, **flotteur(53)** n’est pas exactement IEEE 754. Par exemple, ni la valeur NaN (Not-a-Number,), ni une valeur infinie n'est employée. Tenter de convertir une chaîne nonnumérique en **nombre** et essayer de diviser par zéro aboutit à une erreur.  
  
## <a name="xpath-conversions"></a>Conversions XPath  
 Lorsque vous utilisez une requête XPath, telle que `OrderDetail[@UnitPrice > "10.0"]`, les conversions de type de données implicites et explicites peuvent modifier la signification de la requête de manière subtile. Par conséquent, il est primordial de comprendre la manière dont les types de données Xpath sont implémentés. La spécification linguistique XPath, XML Path Language (XPath) version 1.0 W3C Proposition Recommendation 8 Octobre 1999, peut être trouvé sur le site Web W3C à http://www.w3.org/TR/1999/PR-xpath-19991008.html.  
  
 Les opérateurs XPath sont divisés en quatre catégories :  
  
-   Opérateurs booléens (et, ou)  
  
-   Opérateurs relationnels (,\< \<>, >)  
  
-   Opérateurs d'égalité (=, !=)  
  
-   Opérateurs arithmétiques (+, -, *, div, mod)  
  
 Chaque catégorie d'opérateur convertit ses opérandes de manière distincte. Les opérateurs XPath convertissent implicitement leurs opérandes si cela est nécessaire. Les opérateurs arithmétiques convertissent leurs opérands en **nombre,** et donnent une valeur de nombre. Les opérateurs de Boolean convertissent leurs opérands en **boolean,** et aboutissent à une valeur Boolean. Les opérateurs relationnels et d'égalité génèrent une valeur booléenne. Toutefois, ils suivent des règles de conversion différentes en fonction des types de données d'origine de leurs opérandes comme le montre le tableau ci-après.  
  
|Opérande|Opérateur relationnel|Opérateur d'égalité|  
|-------------|-------------------------|-----------------------|  
|Les deux opérandes sont des éléments node-set.|VRAI si et seulement s’il ya un nœud dans un ensemble et un nœud dans le deuxième ensemble de telle sorte que la comparaison de leurs valeurs **de chaîne** est VRAI.|Idem.|  
|L’un est un nœud-set, l’autre une **chaîne**.|VRAI si et seulement s’il ya un nœud dans le nœud-ensemble de telle sorte que lorsqu’il est converti en **nombre**, la comparaison de celui-ci avec la **chaîne** convertie en **nombre** est VRAI.|VRAI si et seulement s’il ya un nœud dans le nœud-set de telle sorte que lorsqu’il est converti en **chaîne**, la comparaison de celui-ci avec la **chaîne** est VRAI.|  
|L’un est un nœud-set, l’autre un **nombre**.|VRAI si et seulement s’il ya un nœud dans le nœud-ensemble de telle sorte que lorsqu’il est converti en **nombre**, la comparaison de celui-ci avec le **nombre** est VRAI.|Idem.|  
|L’un est un nœud-set, l’autre un **boolean**.|VRAI si et seulement s’il ya un nœud dans le nœud-set de telle sorte que lorsqu’il est converti en **boolean,** puis en **nombre**, la comparaison de celui-ci avec le **boolean** converti en **nombre** est VRAI.|VRAI si et seulement s’il ya un nœud dans le nœud-set de telle sorte que lorsqu’il est converti en **boolean**, la comparaison de celui-ci avec le **boolean** est VRAI.|  
|Ni l'un ni l'autre n'est un élément node-set.|Convertir les deux opérandes en **nombre** et ensuite comparer.|Convertissez les deux opérandes en un type commun, puis comparez-les. Convertir **en boolean** si l’un ou l’autre est **boolean**, **nombre** si l’un ou l’autre est **numéro**; autrement, convertir en **chaîne**.|  
  
> [!NOTE]  
>  Parce que les opérateurs relationnels XPath convertissent toujours leurs opérands en **nombre,** les comparaisons **de chaînes** ne sont pas possibles. Pour inclure les comparaisons de dates, SQL Server 2000 offre cette variation à la spécification XPath : lorsqu’un opérateur relationnel compare une **chaîne** à une **chaîne,** un nœud réglé à une **chaîne,** ou un ensemble de nœuds à valeur de cordes à un ensemble de nœuds à cordes, une comparaison **de cordes** (pas une comparaison **de nombre)** est effectuée.  
  
## <a name="node-set-conversions"></a>Conversions des éléments node-set  
 Les conversions des éléments node-set ne sont pas toujours intuitives. Un nœud-set est converti en **une chaîne** en prenant la valeur de chaîne de seulement le premier nœud dans l’ensemble. Un nœud-ensemble est converti en nombre en **le** convertissant en **chaîne,** puis en convertissant **la chaîne** en **nombre**. Un nœud-set est converti en **boolean** en testant son existence.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne procède à aucune sélection positionnelle sur les éléments node-set : par exemple, la requête XPath `Customer[3]` désigne le troisième client ; ce type de sélection positionnelle n'est pas pris en charge dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, les conversions**string** de nœud-réglées-à-corde ou de nœud-définie-à-nombre comme décrit par la spécification XPath ne sont pas implémentées.**number** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise une sémantique « quelconque » partout où la recommandation XPath spécifie la « première » sémantique. Par exemple, sur la base des spécifications W3C `Order[OrderDetail/@UnitPrice > 10.0]` XPath, la requête XPath sélectionne ces commandes avec le premier **OrderDetail** qui a un **UnitPrice** supérieur à 10.0. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette requête XPath sélectionne ces commandes avec n’importe quel **OrderDetail** qui a un **UnitPrice** supérieur à 10.0.  
  
 La conversion au **boolean** génère un test d’existence; par conséquent, la `Products[@Discontinued=true()]` requête XPath est équivalente à l’expression SQL "Products.Discontinued n’est pas nul", et non l’expression SQL "Products.Discontinued -1". Pour rendre la requête équivalente à la dernière expression SQL, d’abord convertir le nœud-ensemble à un type**non-boolean,** tel que **le nombre**. Par exemple : `Products[number(@Discontinued) = true()]`.  
  
 Du fait que la plupart des opérateurs sont définis pour être vrais (TRUE) s'ils le sont pour un nœud quelconque ou l'un des nœuds de l'élément node-set, ces opérations prennent toujours la valeur FALSE si l'élément node-set est vide. Ainsi donc, si A est vide, `A = B` et `A != B` ont tous les deux la valeur FALSE et `not(A=B)` et `not(A!=B)` ont la valeur TRUE.  
  
 Habituellement, un attribut ou un élément qui cartographie une colonne existe si la valeur de cette colonne dans la base de données n’est pas **nulle**. Les éléments mappés aux lignes existent si tous leurs enfants existent.  
  
> [!NOTE]  
>  Des éléments annotés avec **l’est-constant** existent toujours. Par conséquent, XPath prédite ne peut pas être utilisé sur des éléments **est-constant.**  
  
 Lorsqu’un ensemble de nœuds est converti en **chaîne** ou **en nombre,** son type XDR (le cas échéant) est inspecté dans le schéma annoté et ce type est utilisé pour déterminer la conversion qui est nécessaire.  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>Mappage des types de données XDR et XPath  
 Le type de données XPath d’un nœud est dérivé du type de données XDR dans le schéma, comme indiqué dans le tableau suivant (le nœud **EmployeeID** est utilisé à des fins illustratives).  
  
|Type de données XDR|Équivalent<br /><br /> Type de données XPath|Conversion SQL Server utilisée|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|N/A|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8|nombre|CONVERT(float(53), EmployeeID)|  
|id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid|string|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|N/A (aucun type de données XPath n'équivaut au type de données XDR fixed14.4)|CONVERT(money, EmployeeID)|  
|Date|string|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|time<br /><br /> time.tz|string|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 Les conversions de date et d’heure sont conçues pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fonctionner si la valeur est stockée dans la base de données à l’aide du type de données **de date ou** **d’une chaîne**. Notez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]que le type de données **datetime** n’utilise pas **de fuseau horaire** et a une précision plus faible que le type de données **de temps** XML. Pour inclure le type de données **fuseau** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] horaire ou une précision supplémentaire, stockez les données à l’aide **d’un** type de chaîne.  
  
 Lorsque vous convertissez un nœud du type de données XDR en type de données XPath, une conversion supplémentaire est parfois nécessaire (d'un type de données XPath vers un autre type de données XPath). Par exemple, imaginez la requête XPath suivante :  
  
```  
(@m + 3) = 4  
```  
  
 S’il @m s’agit du type de données **XDR fixe14.4,** la conversion du type de données XDR au type de données XPath est effectuée à l’aide de :  
  
```  
CONVERT(money, m)  
```  
  
 Dans cette conversion, `m` le nœud est converti de **fixe14.4** à **l’argent**. Toutefois, l'ajout de la valeur 3 nécessite une autre conversion :  
  
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
||X est inconnu|X est **chaîne**|X est **le numéro**|X est **boolean**|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN(X) > 0|X != 0|-|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>R. Convertir un type de données dans une requête XPath  
 Dans la requête XPath suivante spécifiée contre un schéma XSD annoté, la requête sélectionne tous les nœuds **employés** avec la valeur d’attribut **EmployeeID** de E-1, où "E-" est le préfixe spécifié à l’aide **de l’annotation sql:id-prefix.**  
  
 `Employee[@EmployeeID="E-1"]`  
  
 Le prédicat dans la requête équivaut à l'expression SQL suivante :  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 Parce que **EmployeeID** est l’un des **id** (**idref**, **idrefs**, **nmtoken**, **nmtokens**, et ainsi de suite) les valeurs de type de données dans le schéma XSD, **EmployeeID** est converti au type de données XPath **chaîne** en utilisant les règles de conversion décrites précédemment.  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 Le préfixe  « E - » est ajouté à la chaîne et le résultat est ensuite comparé avec `N'E-1'`.  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. Effectuer plusieurs conversions de types de données dans une requête XPath.  
 Examinez la requête XPath suivante définie par rapport à un schéma XSD annoté : `OrderDetail[@UnitPrice * @OrderQty > 98]`  
  
 Cette requête XPath renvoie tous les éléments ** \<de>OrderDetail** satisfaisant le prédicat `@UnitPrice * @OrderQty > 98`. Si **l’UnitPrice** est annoté avec un type de données **fixe14.4** dans le schéma annoté, ce prédicat est équivalent à l’expression SQL :  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 Lors de la conversion des valeurs dans la requête XPath, la première conversion convertit le type de données XDR en type de données XPath. Étant donné que le type de données XSD **d’UnitPrice** est **fixé14,4**, tel que décrit dans le tableau précédent, il s’agit de la première conversion qui est utilisée :  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Étant donné que les opérateurs arithmétiques convertissent leurs opérandes au type **de** données XPath, la deuxième conversion (d’un type de données XPath à un autre type de données XPath) est appliquée dans laquelle la valeur est convertie en **flotteur(53)** **(flotteur(53)** est proche du type de **données** XPath:  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 En supposant que l’attribut **OrderQty** n’a pas de type de données XSD, **OrderQty** est converti en un **type de** données XPath numéro dans une seule conversion :  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 De même, la valeur 98 est convertie au **type de** données XPath numéro :  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  Si le type de données XSD appliqué au schéma est incompatible avec le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous-jacent dans la base de données, ou si une conversion de type de données XPath impossible est réalisée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner une erreur. Par exemple, si **l’attribut EmployeeID** est annoté avec l’annotation **id-prefix,** le `Employee[@EmployeeID=1]` XPath génère une erreur, parce que **EmployeeID** a **l’annotation id-prefix** et ne peut pas être converti en **nombre**.  
  
  
