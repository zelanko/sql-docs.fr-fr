---
title: "Value(), méthode (Type de données xml) | Documents Microsoft"
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
- value method
- value() method
ms.assetid: 298a7361-dc9a-4902-9b1e-49a093cd831d
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b2cd81e4b96ce5c38a816c50728d794390bb383
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="value-method-xml-data-type"></a>value(), méthode (Type de données xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Exécute une requête XQuery sur le code XML et retourne une valeur de type SQL. Cette méthode retourne une valeur scalaire.  
  
 Vous utilisez généralement cette méthode pour extraire une valeur d’une instance XML stockée dans une **xml** colonne de type, paramètre ou variable. Vous pouvez ainsi spécifier des requêtes SELECT qui combinent ou comparent des données XML avec des données de colonnes non-XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
value (XQuery, SQLType)  
```  
  
## <a name="arguments"></a>Arguments  
 *XQuery*  
 Est la *XQuery* expression, un littéral de chaîne, qui Récupère des données à l’intérieur de l’instance XML. La requête XQuery doit retourner au plus une valeur. Sinon, une erreur est retournée.  
  
 *SQLType*  
 Type SQL préféré (littéral de chaîne) à retourner. Le type de retour de cette méthode correspond à la *SQLType* paramètre. *SQLType* ne peut pas être un **xml** type de données, un type common language runtime (CLR) définis par l’utilisateur, **image**, **texte**, **ntext**, ou **sql_variant** type de données. *SQLType* peut être un SQL, le type de données défini par l’utilisateur.  
  
 Le **value()** utilise le [!INCLUDE[tsql](../../includes/tsql-md.md)] opérateur de convertir implicitement et essaie de convertir le résultat de l’expression XQuery, la représentation sous forme de chaîne sérialisée, du type XSD au type SQL correspondant spécifié par [!INCLUDE[tsql](../../includes/tsql-md.md)] conversion. Pour plus d’informations sur les règles de conversion de type pour CONVERT, consultez [CAST et CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
> [!NOTE]  
>  Pour des raisons de performances, au lieu d’utiliser le **value()** méthode dans un prédicat de comparaison avec une valeur relationnelle, utilisez **exist()** avec **SQL :Column()**. L'exemple D vous en donne l'illustration.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-the-value-method-against-an-xml-type-variable"></a>A. Utilisation de la méthode value() sur une variable de type xml  
 Dans l'exemple suivant, une instance XML est stockée dans une variable de type `xml`. La méthode `value()` récupère la valeur d'attribut `ProductID` à partir du code XML. La valeur est ensuite assignée à une variable `int`.  
  
```  
DECLARE @myDoc xml  
DECLARE @ProdID int  
SET @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
  
SET @ProdID =  @myDoc.value('(/Root/ProductDescription/@ProductID)[1]', 'int' )  
SELECT @ProdID  
```  
  
 La valeur 1 est retournée comme résultat.  
  
 Bien qu'il n'y ait qu'un seul attribut `ProductID` dans l'instance XML, les règles de types statiques exigent que vous spécifiiez de manière explicite que l'expression de chemin d'accès retourne un singleton. Par conséquent, le `[1]` supplémentaire est spécifié à la fin de l'expression de chemin d'accès. Pour plus d’informations sur les types statiques, consultez [XQuery et le typage statique](../../xquery/xquery-and-static-typing.md).  
  
### <a name="b-using-the-value-method-to-retrieve-a-value-from-an-xml-type-column"></a>B. Utilisation de la méthode value() pour récupérer une valeur à partir d'une colonne de type xml  
 La requête suivante porte sur une **xml** colonne de type (`CatalogDescription`) dans le `AdventureWorks` base de données. La requête récupère des valeurs d'attributs `ProductModelID` à partir de chaque instance XML stockée dans la colonne.  
  
```  
SELECT CatalogDescription.value('             
    declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";             
       (/PD:ProductDescription/@ProductModelID)[1]', 'int') AS Result             
FROM Production.ProductModel             
WHERE CatalogDescription IS NOT NULL             
ORDER BY Result desc             
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Le mot clé `namespace` est utilisé pour définir un préfixe d'espace de noms.  
  
-   Conformément aux exigences de type statique, `[1]` est ajouté à la fin de l'expression de chemin d'accès dans la méthode `value()` afin d'indiquer de manière explicite que l'expression de chemin d'accès retourne un singleton.  
  
 Voici le résultat partiel :  
  
```  
-----------  
35           
34           
...  
```  
  
### <a name="c-using-the-value-and-exist-methods-to-retrieve-values-from-an-xml-type-column"></a>C. Utilisation des méthodes value() et exist() pour récupérer des valeurs à partir d'une colonne de type xml  
 L’exemple suivant illustre l’utilisation à la fois le `value()` (méthode) et le [méthode exist()](../../t-sql/xml/exist-method-xml-data-type.md) de la **xml** type de données. La méthode `value()` est utilisée pour récupérer des valeurs d'attributs `ProductModelID` à partir du code XML. La méthode `exist()` de la clause `WHERE` est utilisée pour filtrer les lignes de la table.  
  
 La requête récupère des ID de modèle de produit à partir d'instances XML qui incluent des informations de garantie (l'élément <`Warranty`>) comme caractéristiques. La condition de la clause `WHERE` utilise la méthode `exist()` pour récupérer uniquement les lignes qui satisfont cette condition.  
  
```  
SELECT CatalogDescription.value('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
           (/PD:ProductDescription/@ProductModelID)[1] ', 'int') as Result  
FROM  Production.ProductModel  
WHERE CatalogDescription.exist('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   La colonne `CatalogDescription` est une colonne XML typée. Cela signifie qu'une collection de schémas lui est associée. Dans le [prologue XQuery](../../xquery/modules-and-prologs-xquery-prolog.md), la déclaration d’espace de noms est utilisée pour définir le préfixe utilisé plus loin dans le corps de la requête.  
  
-   Si la méthode `exist()` retourne un `1` (True), cela indique que l'instance XML contient l'élément enfant <`Warranty`> comme caractéristique.  
  
-   La méthode `value()` de la clause `SELECT` récupère ensuite les valeurs d'attributs `ProductModelID` comme entiers.  
  
 Voici le résultat partiel :  
  
```  
Result       
-----------  
19           
23           
...  
```  
  
### <a name="d-using-the-exist-method-instead-of-the-value-method"></a>D. Utilisation de la méthode exist() au lieu de la méthode value()  
 Pour des raisons de performances, au lieu d'utiliser la méthode `value()` dans un prédicat pour comparer avec une valeur relationnelle, utilisez `exist()` avec `sql:column()`. Exemple :  
  
```  
CREATE TABLE T (c1 int, c2 varchar(10), c3 xml)  
GO  
  
SELECT c1, c2, c3   
FROM T  
WHERE c3.value( '/root[1]/@a', 'integer') = c1  
GO  
```  
  
 Cela peut être écrit de la manière suivante :  
  
```  
SELECT c1, c2, c3   
FROM T  
WHERE c3.exist( '/root[@a=sql:column("c1")]') = 1  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Créer des instances de données XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)   
 [XML Data Modification Language &#40; XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

