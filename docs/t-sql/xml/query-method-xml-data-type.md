---
title: "Méthode Query() (Type de données de xml) | Documents Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: db0f9b1ffc4c6ca13084942144e13d64765d7019
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="query-method-xml-data-type"></a>Méthode query() (type de données xml)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Spécifie une requête XQuery sur une instance de la **xml** type de données. Le résultat est de **xml** type. La méthode renvoie une instance XML non typé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>Arguments  
 XQuery  
 Expression XQuery de type chaîne, qui interroge les nœuds XML, tels que des éléments ou des attributs, dans une instance XML.  
  
## <a name="examples"></a>Exemples  
 Cette section fournit des exemples d’utilisation de la méthode query() de la **xml** type de données.  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. Utilisation de la méthode query() sur une variable de type xml  
 L’exemple suivant déclare une variable  **@myDoc**  de **xml** de type et lui assigne une instance XML. Le **query()** méthode est ensuite utilisée pour spécifier une requête XQuery par rapport au document.  
  
 La requête récupère l'élément enfant <`Features`> provenant de l'élément <`ProductDescription`>.  
  
```  
declare @myDoc xml  
set @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc.query('/Root/ProductDescription/Features')  
```  
  
 Voici le résultat obtenu :  
  
```  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>        
```  
  
### <a name="b-using-the-query-method-against-an-xml-type-column"></a>B. Utilisation de la méthode query() sur une colonne de type XML  
 Dans l’exemple suivant, la **query()** méthode est utilisée pour spécifier une requête XQuery sur le **CatalogDescription** colonne de **xml** de type dans le **AdventureWorks** base de données :  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   La colonne CatalogDescription est typé **xml** colonne. En d'autres termes, elle possède une collection de schémas qui lui est associée. Dans le [prologue XQuery](../../xquery/modules-and-prologs-xquery-prolog.md), le **espace de noms** est utilisé pour définir le préfixe qui sera utilisé ultérieurement dans le corps de la requête.  
  
-   Le **query()** méthode construit un document XML, un <`Product`> élément ayant une **ProductModelID** attribut, dans lequel le **ProductModelID** valeur d’attribut est récupérée à partir de la base de données. Pour plus d’informations sur la construction XML, consultez [Construction XML &#40; XQuery &#41; ](../../xquery/xml-construction-xquery.md).  
  
-   Le [méthode exist() (type de données XML)](../../t-sql/xml/exist-method-xml-data-type.md) dans la clause WHERE est utilisée pour rechercher uniquement les lignes qui contient le <`Warranty`> élément dans le document XML. Là encore, la **espace de noms** est utilisé pour définir deux préfixes d’espace de noms.  
  
 Voici le résultat partiel :  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 Remarque : les méthodes query() et exist() déclarent toutes deux le préfixe PD. Quand de tels cas se présentent, vous pouvez utiliser WITH XMLNAMESPACES pour définir au préalable les préfixes et les utiliser dans la requête.  
  
```  
WITH XMLNAMESPACES (  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
SELECT CatalogDescription.query('  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Créer des instances de données XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)   
 [XML Data Modification Language &#40; XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

