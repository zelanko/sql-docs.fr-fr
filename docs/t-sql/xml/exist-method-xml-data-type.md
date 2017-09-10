---
title: "Méthode (Type de données xml) exist() | Documents Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- exist() method
- exist method
ms.assetid: a55b75e0-0a17-4787-a525-9b095410f7af
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0e152abc34c459d82f451c5ded02d30f5fb76b23
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="exist-method-xml-data-type"></a>Méthode exist() (type de données xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un **bits** qui représente une des conditions suivantes :  
  
-   1 : représente True, si l'expression XQuery dans une requête renvoie un résultat non vide. En d'autres termes, elle renvoie au moins un nœud XML.  
  
-   0 : représente False, si elle renvoie un résultat vide.  
  
-   NULL si le **xml** instance de type de données sur laquelle la requête a été exécutée contient la valeur NULL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
exist (XQuery)   
```  
  
## <a name="arguments"></a>Arguments  
 XQuery  
 Expression XQuery, représentant un littéral de chaîne.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]  
>  Le **exist()** méthode retourne 1 pour l’expression XQuery qui retourne un résultat non vide. Si vous spécifiez la **true()** ou **false()** fonctionne à l’intérieur la **exist()** (méthode), la **exist()** méthode retourne 1, parce que les fonctions **true()** et **false()** retournent des valeurs booléennes True et False, respectivement. De fait, elles retournent un résultat non vide. Par conséquent, **exist()** retourne 1 (True), comme indiqué dans l’exemple suivant :  
  
```  
declare @x xml;  
set @x='';  
select @x.exist('true()');   
```  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants montrent comment spécifier le **exist()** (méthode).  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-variable"></a>Exemple : Spécification de la méthode exist() par rapport à une variable de type xml  
 Dans l’exemple suivant, @x est un **xml** variable de type (xml non typé) et @f est une variable de type integer qui stocke la valeur retournée par la **exist()** (méthode). Le **exist()** méthode retourne la valeur True (1) si la valeur de date stockée dans l’instance XML est `2002-01-01`.  
  
```  
declare @x xml;  
declare @f bit;  
set @x = '<root Somedate = "2002-01-01Z"/>';  
set @f = @x.exist('/root[(@Somedate cast as xs:date?) eq xs:date("2002-01-01Z")]');  
select @f;  
```  
  
 Comparaison des dates dans le **exist()** (méthode), notez les points suivants :  
  
-   Le code `cast as xs:date?` est utilisé pour effectuer un cast de la valeur à **xs : date** type à des fins de comparaison.  
  
-   La valeur de la  **@Somedate**  attribut est non typé. Dans la comparaison de cette valeur, il est implicitement converti dans le type sur le côté droit de la comparaison, la **xs : date** type.  
  
-   Au lieu de **effectué tant que xs :date()**, vous pouvez utiliser la **xs :date()** fonction constructeur. Pour plus d’informations, consultez [fonctions constructeur &#40; XQuery &#41; ](../../xquery/constructor-functions-xquery.md).  
  
 L'exemple suivant est similaire au précédent, sauf qu'il possède un élément <`Somedate`>.  
  
```  
DECLARE @x xml;  
DECLARE @f bit;  
SET @x = '<Somedate>2002-01-01Z</Somedate>';  
SET @f = @x.exist('/Somedate[(text()[1] cast as xs:date ?) = xs:date("2002-01-01Z") ]')  
SELECT @f;  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Le **text()** méthode retourne un nœud de texte qui contient la valeur non typée `2002-01-01`. (Le type XQuery est **xdt : untypedAtomic**.) Vous devez explicitement convertir cette valeur typée de **x** à **xsd : date**, car la conversion implicite n’est pas pris en charge dans ce cas.  
  
### <a name="example-specifying-the-exist-method-against-a-typed-xml-variable"></a>Exemple : Spécification de la méthode exist() par rapport à une variable xml typée  
 L’exemple suivant illustre l’utilisation de la **exist()** méthode par rapport à un **xml** variable de type. Il s'agit d'une variable XML typée, car elle spécifie le nom de la collection d'espaces de noms de schéma, `ManuInstructionsSchemaCollection`.  
  
 Dans l’exemple, un document est affecté à cette variable d’instructions de fabrication, puis le **exist()** méthode est utilisée pour rechercher si le document comprend une <`Location`> élément dont **LocationID** valeur d’attribut est 50.  
  
 Le **exist()** méthode spécifiée par rapport à la @x variable renvoie 1 (vrai) si les instructions de fabrication comprend un <`Location`> élément ayant `LocationID=50`. Sinon, la méthode renvoie 0 (False).  
  
```  
DECLARE @x xml (Production.ManuInstructionsSchemaCollection);  
SELECT @x=Instructions  
FROM Production.ProductModel  
WHERE ProductModelID=67;  
--SELECT @x  
DECLARE @f int;  
SET @f = @x.exist(' declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    /AWMI:root/AWMI:Location[@LocationID=50]  
');  
SELECT @f;  
```  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-column"></a>Exemple : Spécification de la méthode exist() par rapport à une colonne de type xml  
 La requête suivante extrait les ID de modèle de produit dont les descriptions de catalogue ne comprennent pas les spécifications, en l'occurrence l'élément <`Specifications`> :  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
    declare namespace  pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /pd:ProductDescription[not(pd:Specifications)]'  
    ) = 1;  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   La clause WHERE sélectionne uniquement les lignes de la **ProductDescription** table qui satisfont la condition spécifiée par rapport à la **CatalogDescription xml** colonne de type.  
  
-   Le **exist()** méthode dans la clause WHERE renvoie 1 (vrai) si le code XML n’inclut aucune <`Specifications`> élément. Notez l’utilisation de la [fonction not() (XQuery)](../../xquery/functions-on-boolean-values-not-function.md).  
  
-   Le [fonction SQL :Column() (XQuery)](../../xquery/xquery-extension-functions-sql-column.md) fonction est utilisée pour extraire la valeur d’une colonne non-XML.  
  
-   Cette requête renvoie un ensemble de lignes vide.  
  
 La requête spécifie **query()** et **exist()** méthodes du type de données xml et ces deux méthodes déclarent les mêmes espaces de noms dans le prologue de la requête. Dans ce cas, vous pouvez recourir à WITH XMLNAMESPACES pour déclarer le préfixe puis l'utiliser dans la requête.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[not(pd:Specifications)]'  
    ) = 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Créer des instances de données XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)   
 [XML Data Modification Language &#40; XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

