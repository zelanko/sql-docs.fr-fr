---
title: FOR XML (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, about FOR XML clause
- PATH FOR XML mode, construction
- EXPLICIT FOR XML mode
- RAW FOR XML mode
- retrieving XML data
- XML [SQL Server], FOR XML clause
- AUTO FOR XML mode
- XML [SQL Server], construction
ms.assetid: 2b6b5c61-c5bd-49d2-8c0c-b7cf15857906
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c7676d046a504a6f230df7a1352e791802ce7b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288270"
---
# <a name="for-xml-sql-server"></a>FOR XML (SQL Server)
  Une requête SELECT retourne les résultats sous la forme d'un ensemble de lignes. Vous pouvez si vous le souhaitez récupérer les résultats d'une requête SQL sous forme de code XML en spécifiant la clause FOR XML dans la requête. La clause FOR XML peut être utilisée dans les requêtes de premier niveau et dans les sous-requêtes. La clause FOR XML de premier niveau ne peut être utilisée que dans l'instruction SELECT. Dans les sous-requêtes, FOR XML peut être utilisée dans les instructions INSERT, UPDATE et DELETE. Elle peut être également utilisée dans les instructions d'assignation.  
  
 Dans une clause FOR XML, vous spécifiez l'un des modes suivants :  
  
-   RAW  
  
-   AUTO  
  
-   EXPLICIT  
  
-   PATH  
  
 Le mode RAW génère un seul élément \<row> par ligne dans l’ensemble de lignes qui est retourné par l’instruction SELECT. Vous pouvez générer une hiérarchie XML en écrivant des requêtes FOR XML imbriquées.  
  
 Le mode AUTO génère l'imbrication dans le code XML résultant en utilisant une heuristique basée sur la manière dont l'instruction SELECT est spécifiée. Vous n'avez qu'un contrôle minimal sur la forme du code XML généré. Les requêtes FOR XML imbriquées peuvent être écrites de façon à générer une hiérarchie XML au-delà de la forme XML générée par l'heuristique du mode AUTO.  
  
 Le mode EXPLICIT permet de contrôler davantage la forme du code XML. Vous pouvez combiner des attributs et des éléments à volonté afin de décider de la forme du code XML. Un format spécifique est nécessaire pour l'ensemble de lignes généré suite à l'exécution de requête. Le format d'ensemble de lignes est ensuite mappé au format XML. L'avantage du mode EXPLICIT est qu'il permet de combiner des attributs et des éléments à volonté, de créer des wrappers et des propriétés complexes imbriquées et de créer des valeurs séparées par des espaces (par exemple, l'attribut OrderID peut avoir une liste d'ID d'ordre) ainsi que du contenu mixte.  
  
 Toutefois, l'écriture de requêtes en mode EXPLICIT peut être une opération pénible. Vous pouvez utiliser certaines des nouvelles fonctionnalités FOR XML, telles que l'écriture de requêtes FOR XML en mode RAW/AUTO/PATH et la directive TYPE, au lieu d'utiliser le mode EXPLICIT pour générer les hiérarchies. Les requêtes FOR XML imbriquées peuvent produire tout code XML que vous générez à l'aide du mode EXPLICIT. Pour plus d’informations, consultez [Utiliser des requêtes FOR XML imbriquées](use-nested-for-xml-queries.md) et [Directive TYPE dans les requêtes FOR XML](type-directive-in-for-xml-queries.md).  
  
 Le mode PATH, associé à la capacité des requêtes FOR XML imbriquées, offre la flexibilité du mode EXPLICIT sous une forme plus simple.  
  
 Ces modes ne s'appliquent qu'aux requêtes pour lesquelles ils sont définis. Ils n'affectent pas les résultats des requêtes suivantes.  
  
 La clause FOR XML n'est pas valide en cas de sélection comportant une clause FOR BROWSE.  
  
## <a name="example"></a>Exemple  
 L’instruction `SELECT` suivante récupère des informations des tables `Sales.Customer` et `Sales.SalesOrderHeader` de la base de données `AdventureWorks2012` . Cette requête spécifie le mode `AUTO` dans la clause `FOR XML` :  
  
```  
USE AdventureWorks2012  
GO  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status  
FROM Sales.Customer Cust   
INNER JOIN Sales.SalesOrderHeader OrderHeader  
ON Cust.CustomerID = OrderHeader.CustomerID  
FOR XML AUTO  
```  
  
## <a name="the-for-xml-clause-and-server-names"></a>La clause FOR XML et les noms de serveurs  
 Quand une instruction SELECT avec une clause FOR XML spécifie un nom en quatre parties dans la requête, le nom du serveur n'est pas renvoyé dans le document XML résultant quand la requête est exécutée sur l'ordinateur local. Cependant, le nom du serveur est renvoyé sous forme de nom en quatre parties quand la requête s'exécute sur un serveur.  
  
 Par exemple, envisagez la requête suivante :  
  
```  
SELECT TOP 1 LastName  
FROM ServerName.AdventureWorks2012.Person.Person  
FOR XML AUTO  
```  
  
 Quand `ServerName` est un serveur local, la requête renvoie :  
  
```  
<AdventureWorks2012.Person.Person LastName="Achong" />  
```  
  
 Quand `ServerName` est un serveur réseau, la requête renvoie :  
  
```  
<ServerName.AdventureWorks2012.Person.Person LastName="Achong" />  
```  
  
 Cette ambiguïté peut être levée à condition de spécifier cet alias :  
  
```  
SELECT TOP 1 LastName  
FROM ServerName.AdventureWorks2012.Person.Person x  
FOR XML AUTO   
```  
  
 Cette requête donne le résultat suivant :  
  
```  
<x LastName="Achong"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe de base de la clause FOR XML](basic-syntax-of-the-for-xml-clause.md)   
 [Utiliser le mode RAW avec FOR XML](use-raw-mode-with-for-xml.md)   
 [UTiliser le mode AUTO avec FOR XML](use-auto-mode-with-for-xml.md)   
 [Utiliser le mode EXPLICIT avec FOR XML](use-explicit-mode-with-for-xml.md)   
 [Utiliser le mode PATH avec FOR XML](use-path-mode-with-for-xml.md)   
 [OPENXML &#40;SQL Server&#41;](openxml-sql-server.md)   
 [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)  
  
  
