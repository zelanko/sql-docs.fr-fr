---
title: "Utiliser des requ&#234;tes FOR XML imbriqu&#233;es dans ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "clause FOR XML, requêtes FOR XML imbriquées"
  - "requêtes [XML dans SQL Server], ASP.NET et"
  - "requêtes FOR XML imbriquées dans ASP.NET"
  - "ASP.NET [SQL Server]"
ms.assetid: 691ac7dd-afc5-4760-932c-2b1dcd9394ed
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Utiliser des requ&#234;tes FOR XML imbriqu&#233;es dans ASP.NET
  Dans cet exemple, une application ASP.NET retourne des données XML à un navigateur en exécutant une procédure stockée dans SQL Server. La procédure stockée génère des données XML à l'aide de requêtes imbriquées. Une instruction SELECT similaire est présentée dans la rubrique [Génération de frères à l’aide d’une requête imbriquée en mode AUTO](../../relational-databases/xml/generate-siblings-with-a-nested-auto-mode-query.md). Cet exemple illustre une façon d'utiliser des requêtes FOR XML imbriquées pour générer des données XML centrées sur l'élément dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Exemple  
  
```  
CREATE PROC GetSalesOrderInfo AS  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
      FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
      for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE, ELEMENTS)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
GO  
```  
  
 Voici l'application .aspx. Elle exécute la procédure stockée et renvoie les données XML dans le navigateur :  
  
```  
<%@LANGUAGE=C# Debug=true %>  
<%@import Namespace="System.Xml"%>  
<%@import namespace="System.Data.SqlClient" %><%  
Response.Expires = -1;  
Response.ContentType = "text/xml";  
%>  
  
<%  
using(System.Data.SqlClient.SqlConnection c = new System.Data.SqlClient.SqlConnection("Data Source=server;Database=AdventureWorks;Integrated Security=SSPI;"))  
using(System.Data.SqlClient.SqlCommand cmd = c.CreateCommand())  
{  
   cmd.CommandText = "GetSalesOrderInfo";  
   cmd.CommandType = CommandType.StoredProcedure;  
   cmd.Connection.Open();  
   System.Xml.XmlReader r = cmd.ExecuteXmlReader();  
   System.Xml.XmlTextWriter w = new System.Xml.XmlTextWriter(Response.Output);  
   w.WriteStartElement("Root");  
   r.MoveToContent();  
   while(! r.EOF)  
   {  
      w.WriteNode(r, true);  
   }  
   w.WriteEndElement();  
   w.Flush();  
}  
%>  
```  
  
##### Pour tester l'application  
  
1.  Créez la procédure stockée dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
2.  Enregistrez l'application .aspx dans le répertoire c:\inetpub\wwwroot (GetSalesOrderInfo.aspx).  
  
3.  Exécutez l'application ((http://server/GetSalesOrderInfo.aspx).  
  
## Voir aussi  
 [Utiliser des requêtes FOR XML imbriquées](../../relational-databases/xml/use-nested-for-xml-queries.md)  
  
  