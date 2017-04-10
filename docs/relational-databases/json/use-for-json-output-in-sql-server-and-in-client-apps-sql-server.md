---
title: "Utiliser la sortie de FOR JSON dans SQL&#160;Server et les applications clientes (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON, utilisation dans les applications clientes"
  - "FOR JSON, utilisation dans SQL Server"
ms.assetid: 302e5397-b499-4ea3-9a7f-c24ccad698eb
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Utiliser la sortie de FOR JSON dans SQL&#160;Server et les applications clientes (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Les exemples suivants montrent comment utiliser la clause **FOR JSON** ou sa sortie dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les applications clientes.  
  
## Utiliser la sortie de FOR JSON dans des variables SQL Server  
 La sortie de la clause FOR JSON est de type NVARCHAR(MAX). Elle peut donc être affectée à une variable, comme indiqué dans l’exemple suivant.  
  
```tsql  
DECLARE @x NVARCHAR(MAX) = (SELECT TOP 10 * FROM Sales.SalesOrderHeader FOR JSON AUTO)  
```  
  
## Utiliser la sortie de FOR JSON dans des fonctions SQL Server définies par l’utilisateur  
 Vous pouvez créer des fonctions définies par l’utilisateur qui convertissent les jeux de résultats au format JSON et renvoient cette sortie JSON. l’exemple suivant crée une fonction définie par l’utilisateur, qui extrait certaines lignes de détails de commande et les organise en un tableau JSON.  
  
```tsql  
CREATE FUNCTION GetSalesOrderDetails(@salesOrderId int)  
RETURNS NVARCHAR(MAX)  
AS  
BEGIN  
  RETURN (SELECT UnitPrice, OrderQty  
          FROM Sales.SalesOrderDetail  
          WHERE SalesOrderID = @salesOrderId  
          FOR JSON AUTO)  
END  
```  
  
 Vous pouvez utiliser cette fonction dans un lot ou une requête, comme indiqué dans l’exemple suivant.  
  
```tsql  
DECLARE @x NVARCHAR(MAX) = dbo.GetSalesOrderDetails(43659)  
PRINT dbo.GetSalesOrderDetails(43659)  
SELECT TOP 10 H.*, dbo.GetSalesOrderDetails(H.SalesOrderId) AS Details  
FROM Sales.SalesOrderHeader H  
```  
  
## Fusionner les données parentes et enfants dans une seule table  
 Dans l’exemple suivant, chaque ensemble de lignes enfants est présenté sous la forme d’un tableau JSON et devient la valeur de la colonne Détails de la table parente.  
  
```tsql  
select top 10 SalesOrderId, OrderDate,  
     (select top 3 UnitPrice, OrderQty  
        from Sales.SalesOrderDetail D  
        where H.SalesOrderId = D.SalesOrderID  
        for json auto) as Details  
into SalesOrder  
from Sales.SalesOrderHeader H  
```  
  
## Mettre à jour les données dans les colonnes JSON  
 l’exemple suivant montre comment mettre à jour la valeur des colonnes qui contiennent le texte JSON.  
  
```tsql  
UPDATE SalesOrder  
SET Details =  
    (SELECT TOP 1 UnitPrice, OrderQty  
      FROM Sales.SalesOrderDetail D  
      WHERE D.SalesOrderId = SalesOrder.SalesOrderId  
     FOR JSON AUTO)  
```  
  
## Utiliser la sortie de FOR JSON dans une application cliente C#  
 l’exemple suivant montre comment récupérer la sortie JSON d’une requête dans un objet StringBuilder d’une application cliente C#. Supposons que la variable queryWithForJson contienne le texte d’une instruction SELECT avec une clause FOR JSON.  
  
```csharp  
var cmd = new SqlCommand(queryWithForJson, conn);  
conn.Open();  
var jsonResult = new StringBuilder();  
var reader = cmd.ExecuteReader();  
if (!reader.HasRows)  
{  
    jsonResult.Append("[]");  
}  
else  
{  
    while (reader.Read())  
    {  
        jsonResult.Append(reader.GetValue(0).ToString());  
    }  
}  
```  
  
## Voir aussi  
 [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  