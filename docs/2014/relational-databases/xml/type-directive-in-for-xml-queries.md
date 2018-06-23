---
title: Directive TYPE dans les requêtes FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
caps.latest.revision: 40
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3e5a3ffe184513bce9f331f5d905a0587897e64a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152993"
---
# <a name="type-directive-in-for-xml-queries"></a>Directive TYPE dans les requêtes FOR XML
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prise en charge pour le [xml &#40;Transact-SQL&#41; ](/sql/t-sql/xml/xml-transact-sql) vous permet éventuellement de demander que le résultat d’une requête FOR XML soit renvoyé en tant que `xml` type de données en spécifiant la directive TYPE. Cela vous permet de traiter le résultat d'une requête FOR XML sur le serveur. Par exemple, vous pouvez spécifier une requête XQuery par rapport à elle, affecter le résultat à une `xml` variable de type, ou d’écriture [requêtes FOR XML imbriquées](use-nested-for-xml-queries.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Retourne le type de données XML des données d’instance pour le client à la suite de différentes constructions de serveur telles que les requêtes FOR XML qui utilisent la directive TYPE, ou dans lesquelles le `xml` type de données est utilisé pour renvoyer les valeurs de données d’instance XML à partir de colonnes de la table SQL et de sortie paramètres. Dans le code de l'application cliente, le fournisseur ADO.NET demande à ce que ces informations de type de données XML soient envoyées dans un encodage binaire à partir du serveur. Toutefois, si vous utilisez FOR XML sans la directive TYPE, les données XML reviennent en tant que type chaîne. Dans tous les cas, le fournisseur client est toujours en mesure de gérer toute forme XML. Notez qu'une clause FOR XML de premier niveau sans directive TYPE ne peut pas être utilisée avec les curseurs.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent l'utilisation de la directive TYPE avec des requêtes FOR XML.  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a>Extraction des résultats de la requête FOR XML en tant que type xml  
 La requête suivante extrait des informations de contact client de la table `Contacts` . Étant donné que la directive `TYPE` est spécifiée sous la forme `FOR XML`, le résultat est renvoyé en tant que type `xml`.  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 Voici le résultat partiel :  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a>Affectation des résultats de la requête FOR XML à une variable de type xml  
 Dans l’exemple suivant, un résultat FOR XML est attribué à un `xml` variable de type `@x`. La requête récupère les informations de contact, telles que la `BusinessEntityID`, `FirstName`, `LastName`et d’autres numéros de téléphone à partir de la `AdditionalContactInfo` colonne de `xml``TYPE`. Étant donné que la clause `FOR XML` spécifie la directive `TYPE`, le document XML est renvoyé en tant que type `xml` et affecté à une variable.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a>Interrogation des résultats d'une requête FOR XML  
 Les requêtes FOR XML renvoient des données XML. Par conséquent, vous pouvez appliquer `xml` tels que les méthodes de type `query()` et `value()`, au résultat XML renvoyé par les requêtes FOR XML.  
  
 Dans la requête suivante, le `query()` méthode de la `xml` type de données est utilisé pour interroger le résultat de la `FOR XML` requête. Pour plus d’informations, consultez [Méthode query&#40;&#41; &#40;type de données xml&#41;](/sql/t-sql/xml/query-method-xml-data-type).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 Interne `SELECT … FOR XML` requête renvoie un `xml` résultat auquel de type externe `SELECT` s’applique le `query()` méthode à la `xml` type. Notez la directive `TYPE` spécifiée.  
  
 Voici le résultat obtenu :  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 Dans la requête suivante, la méthode `value()` du type de données `xml` permet d'extraire une valeur du résultat XML renvoyé par la requête `SELECT…FOR XML`. Pour plus d’informations, consultez [Méthode value&#40;&#41; &#40;type de données xml&#41;](/sql/t-sql/xml/value-method-xml-data-type).  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 L'expression de chemin d'accès XQuery dans la méthode `value()` extrait le premier numéro de téléphone d'un contact client dont `BusinessEntityID` a pour valeur `1`.  
  
> [!NOTE]  
>  Si la directive TYPE n’est pas spécifiée, le résultat de la requête FOR XML est retourné en tant que type `nvarchar(max)`.  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a>Utilisation des résultats de la requête FOR XML dans INSERT, UPDATE et DELETE (Transact-SQL DML)  
 L'exemple suivant montre comment des requêtes FOR XML peuvent être utilisées dans des instructions DML (Data Manipulation Language, langage de manipulation de données). Dans l’exemple, le `FOR XML` retourne une instance de `xml` type. L'instruction `INSERT` insère ce document XML dans une table.  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [FOR XML &#40;SQL Server&#41;](../xml/for-xml-sql-server.md)  
  
  
