---
title: Façonner des données XML avec des requêtes FOR XML imbriquées | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], nested FOR XML
- XML [SQL Server], FOR XML queries
ms.assetid: 8dc42c05-16e8-4b7b-a5d3-550b55acae26
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22522a2bfabc3406e8e3e1331a0518a38b930c8a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68000676"
---
# <a name="shape-xml-with-nested-for-xml-queries"></a>Façonner des données XML avec des requêtes FOR XML imbriquées
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  L'exemple suivant interroge la table `Production.Product` pour extraire les valeurs `ListPrice` et `StandardCost` d'un produit spécifique. Pour rendre la requête intéressante, les deux prix sont renvoyés dans un élément <`Price`> et chaque élément <`Price`> possède un attribut `PriceType`.  
  
## <a name="example"></a>Exemple  
 Voici la forme attendue du document XML :  
  
```  
<xsd:schema xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet2" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet2" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.Product" type="xsd:anyType" />  
</xsd:schema>  
<Production.Product xmlns="urn:schemas-microsoft-com:sql:SqlRowSet2" ProductID="520">  
  <Price xmlns="" PriceType="ListPrice">133.34</Price>  
  <Price xmlns="" PriceType="StandardCost">98.77</Price>  
</Production.Product>  
```  
  
 Voici la requête FOR XML imbriquée :  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Product.ProductID,   
          (SELECT 'ListPrice' as PriceType,   
                   CAST(CAST(ListPrice as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE),  
          (SELECT  'StandardCost' as PriceType,   
                   CAST(CAST(StandardCost as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE)  
FROM Production.Product  
WHERE ProductID=520  
for XML AUTO, TYPE, XMLSCHEMA  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   L’instruction SELECT externe construit l’élément <`Product`> qui possède un attribut **ProductID** et deux éléments enfants <`Price`>.  
  
-   Les deux instructions SELECT internes construisent deux éléments <`Price`>, possédant chacun un attribut **PriceType** et des données XML qui renvoient le prix du produit.  
  
-   La directive XMLSCHEMA figurant dans l'instruction SELECT externe génère le schéma XSD en ligne qui décrit la forme du document XML obtenu.  
  
 Pour rendre la requête intéressante, vous pouvez écrire la requête FOR XML puis écrire une requête XQuery par rapport au résultat afin de redéfinir la forme du document XML, comme le montre la requête suivante :  
  
```  
SELECT ProductID,   
 ( SELECT p2.ListPrice, p2.StandardCost  
   FROM Production.Product p2   
   WHERE Product.ProductID = p2.ProductID  
   FOR XML AUTO, ELEMENTS XSINIL, type ).query('  
                                   for $p in /p2/*  
                                   return   
                                    <Price PriceType = "{local-name($p)}">  
                                     { data($p) }  
                                    </Price>  
                                  ')  
FROM Production.Product  
WHERE ProductID = 520  
FOR XML AUTO, TYPE  
```  
  
 L’exemple précédent utilise la méthode **query()** du type de données **xml** pour interroger le document XML renvoyé par la requête FOR XML interne et construire le résultat attendu.  
  
 Voici le résultat obtenu :  
  
```  
<Production.Product ProductID="520">  
  <Price PriceType="ListPrice">133.3400</Price>  
  <Price PriceType="StandardCost">98.7700</Price>  
</Production.Product>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des requêtes FOR XML imbriquées](../../relational-databases/xml/use-nested-for-xml-queries.md)  
  
  
