---
title: sql:variable() Fonction (XQuery) Microsoft Docs
description: Apprenez à utiliser la fonction XQuery Extension sql:variable() pour exposer une variable qui contient une valeur relationnelle SQL à l’intérieur d’une expression XQuery.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sql:variable() function
- sql:variable function
ms.assetid: 6e2e5063-c1cf-4b5a-b642-234921e3f4f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 8241e15643eb4aa25912451ddfed94699954797f
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388602"
---
# <a name="xquery-extension-functions---sqlvariable"></a>Fonctions d’extension XQuery : sql:variable()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Expose une variable qui contient une valeur relationnelle SQL dans une expression XQuery.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sql:variable("variableName") as xdt:anyAtomicType?  
```  
  
## <a name="remarks"></a>Notes  
 Comme décrit dans le sujet [Binding Relational Data Inside XML](../t-sql/xml/binding-relational-data-inside-xml-data.md), vous pouvez utiliser cette fonction lorsque vous utilisez [des méthodes de type de données XML](../t-sql/xml/xml-data-type-methods.md) pour exposer une valeur relationnelle à l’intérieur de XQuery.  
  
 Par exemple, la [méthode de requête()](../t-sql/xml/query-method-xml-data-type.md) est utilisée pour spécifier une requête contre une instance XML qui est stockée dans une variable ou une colonne de type de données **xml.** En outre, vous pouvez parfois souhaiter que la requête utilise des valeurs d'une variable ou d'un paramètre [!INCLUDE[tsql](../includes/tsql-md.md)] afin de rassembler des données relationnelles et XML. Pour ce faire, vous utilisez la fonction **sql:variable.**  
  
 La valeur SQL sera cartographiée à une valeur XQuery correspondante et son type sera un type de base XQuery qui est équivalent au type SQL correspondant.  
  
 Vous ne pouvez vous référer qu’à une instance **xml** dans le contexte de l’expression source d’une déclaration d’insertion XML-DML ; sinon vous ne pouvez pas vous référer à des valeurs de type **xml** ou d’un type courant de temps d’exécution de langue (CLR).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-the-sqlvariable-function-to-bring-a-transact-sql-variable-value-into-xml"></a>R. Utilisation de la fonction sql:variable() pour insérer une valeur variable Transact-SQL dans XML  
 L'exemple suivant construit une instance XML composée des éléments suivants :  
  
-   une valeur (`ProductID`) issue d'une colonne non-XML. La [fonction sql:column()](../xquery/xquery-extension-functions-sql-column.md) est utilisée pour lier cette valeur dans le XML.  
  
-   une valeur (`ListPrice`) issue d'une colonne non-XML d'une autre table. Là encore, `sql:column()` permet de lier cette valeur au document XML ;  
  
-   une valeur (`DiscountPrice`) issue d'une variable [!INCLUDE[tsql](../includes/tsql-md.md)]. La méthode `sql:variable()` permet de lier cette valeur au document XML ;  
  
-   Une valeur`ProductModelName`( ) à partir d’une colonne de type **xml,** pour rendre la requête plus intéressante.  
  
 Voici la requête :  
  
```sql
DECLARE @price money  
  
SET @price=2500.00  
SELECT ProductID, Production.ProductModel.ProductModelID,CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
       <Product   
           ProductID="{ sql:column("Production.Product.ProductID") }"  
           ProductModelID= "{ sql:column("Production.Product.ProductModelID") }"  
           ProductModelName="{/pd:ProductDescription[1]/@ProductModelName }"  
           ListPrice="{ sql:column("Production.Product.ListPrice") }"  
           DiscountPrice="{ sql:variable("@price") }"  
        />')   
FROM Production.Product   
JOIN Production.ProductModel  
ON Production.Product.ProductModelID = Production.ProductModel.ProductModelID  
WHERE ProductID=771  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   La requête XQuery dans la méthode `query()` construit le document XML.  
  
-   Le `namespace` mot clé est utilisé pour définir un préfixe namespace dans le [XQuery Prolog](../xquery/modules-and-prologs-xquery-prolog.md). Cette opération est réalisée car la valeur d'attribut `ProductModelName` est extraite de la colonne de type `CatalogDescription xml`, à laquelle un schéma est associé.  
  
 Voici le résultat obtenu :  
  
```xml
<Product ProductID="771" ProductModelID="19"   
         ProductModelName="Mountain 100"   
         ListPrice="3399.99" DiscountPrice="2500" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’extension DE SERVEUR SQL XQuery](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Comparez XML typé à XML non typé](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML Data &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Créer des instances de données XML](../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml Méthodes de type de données](../t-sql/xml/xml-data-type-methods.md)   
 [Langage de modification de données XML &#40;XML DML&#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
