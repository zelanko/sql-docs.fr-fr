---
title: Prise en charge de FOR XML pour le type de données XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], XML
- xml data type [SQL Server], FOR XML clause
ms.assetid: 365de07d-694c-4c8b-b671-8825be27f87c
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 14010ca375afdf5166f737a27e33f8ed3fc42c49
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327339"
---
# <a name="for-xml-support-for-the-xml-data-type"></a>Prise en charge de FOR XML pour le type de données XML
  Si une requête FOR XML spécifie une colonne de `xml` type dans la clause SELECT, les valeurs de colonne sont mappées comme éléments dans le code XML retourné, quelle que soit la directive ELEMENTS. Toute déclaration XML dans la colonne de type `xml` n'est pas sérialisée.  
  
 Par exemple, la requête suivante récupère des informations de contact client, telles que la `BusinessEntityID`, `FirstName`, et `LastName` colonnes et les numéros de téléphone à partir de la `AdditionalContactInfo` colonne de `xml` type.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 Étant donné que la requête ne spécifie pas la directive ELEMENTS, les valeurs de colonne sont retournées en tant qu’attributs, sauf pour les valeurs d’informations de contact supplémentaires récupérées à partir de la `xml` colonne de type. Celles-ci sont retournées en tant qu'éléments.  
  
 Voici le résultat partiel :  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</PhoneNumber>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</PhoneNumber>`  
  
```  
</Person.Person>  
...  
```  
  
 Si vous spécifiez un alias de colonne pour la colonne XML générée par la requête XQuery, cet alias est utilisé pour ajouter un élément wrapper autour du code XML généré par la requête XQuery. Par exemple, la requête suivante spécifie `MorePhoneNumbers` comme alias de colonne :  
  
```  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 Le code XML retourné par la requête XQuery est enveloppé dans l'élément <`MorePhoneNumbers`>, comme illustré dans le résultat partiel suivant :  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</MorePhoneNumbers>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</MorePhoneNumbers>`  
  
```  
</Person.Person>  
...  
```  
  
 Si vous spécifiez la directive ELEMENTS dans la requête, BusinessEntityID, LastName et FirstName seront retournés en tant qu'éléments dans le code XML résultant.  
  
 L’exemple suivant montre que la logique de traitement FOR XML ne sérialise aucune déclaration XML dans les données XML à partir d’un `xml` colonne de type :  
  
```  
create table t(i int, x xml)  
go  
insert into t values(1, '<?xml version="1.0" encoding="UTF-8" ?>  
                             <Root SomeID="10" />')  
select i, x  
from   t  
for xml auto;  
```  
  
 Voici l'ensemble de résultats. Dans ce résultat, la déclaration XML <`?xml version="1.0" encoding="UTF-8" ?`> n'est pas sérialisée.  
  
```  
<root>  
  <t i="1">  
    <x>  
      <Root SomeID="10" />  
    </x>  
  </t>  
</root>  
```  
  
## <a name="returning-xml-from-a-user-defined-function"></a>Retour de code XML à partir d'une fonction définie par l'utilisateur  
 Il est possible d'utiliser des requêtes FOR XML pour retourner du code XML à partir d'une fonction définie par l'utilisateur qui retourne l'un des éléments suivants :  
  
-   une table avec une seule colonne de type `xml` ;  
  
-   Une instance de la `xml` type  
  
 Par exemple, la fonction définie par l’utilisateur suivante retourne une table avec une seule colonne de `xm`livre de type :  
  
```  
USE AdventureWorks2012;  
GO  
CREATE FUNCTION dbo.MyUDF (@ProudctModelID int)  
RETURNS @T TABLE  
  (  
     ProductDescription xml  
  )  
AS  
BEGIN  
  INSERT @T  
     SELECT CatalogDescription.query('  
declare namespace PD="http://www.adventure-works.com/schemas/products/description";  
                    //PD:ProductDescription  ')  
     FROM Production.ProductModel  
     WHERE ProductModelID = @ProudctModelID  
  RETURN  
END;  
```  
  
 Vous pouvez exécuter la fonction définie par l'utilisateur et interroger la table retournée par celle-ci. Dans cet exemple, le code XML retourné en interrogeant la table est affecté à un `xml` variable de type.  
  
```  
declare @x xml;  
set @x = (SELECT * FROM MyUDF(19));  
select @x;  
```  
  
 Voici un autre exemple de fonction définie par l'utilisateur. Cette fonction définie par l'utilisateur retourne une instance du type `xml`. Dans cet exemple, la fonction définie par l'utilisateur retourne une instance XML typée car l'espace de noms du schéma est spécifié.  
  
```  
DROP FUNCTION dbo.MyUDF;  
GO  
CREATE FUNCTION MyUDF (@ProductModelID int)   
RETURNS xml ([Production].[ProductDescriptionSchemaCollection])  
AS  
BEGIN  
  declare @x xml  
  set @x =   ( SELECT CatalogDescription  
          FROM Production.ProductModel  
          WHERE ProductModelID = @ProductModelID )  
  return @x  
END;  
```  
  
 Le code XML retourné par la fonction définie par l'utilisateur peut être assigné à une variable de type `xml` comme suit :  
  
```  
declare @x xml;  
SELECT @x= dbo.MyUDF4 (19) ;  
select @x;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge FOR XML des différents types de données SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
