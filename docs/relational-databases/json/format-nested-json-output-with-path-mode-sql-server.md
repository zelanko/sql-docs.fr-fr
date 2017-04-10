---
title: "Formater la sortie&#160;JSON imbriqu&#233;e avec le mode&#160;PATH (SQL&#160;Server) | Microsoft Docs"
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
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Formater la sortie&#160;JSON imbriqu&#233;e avec le mode&#160;PATH (SQL&#160;Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Pour conserver le contrôle intégral du format de la sortie JSON, spécifiez l’option **PATH** avec la clause **FOR JSON** .  
  
 Le mode**PATH** vous permet de créer des objets wrapper et d’imbriquer des propriétés complexes. Les résultats sont présentés sous la forme de tableau d’objets JSON.  
  
 Voici quelques exemples de clause **FOR JSON** avec l’option **PATH** . Formatez les résultats imbriqués en utilisant des noms de colonne séparés par des points ou des requêtes imbriquées, comme indiqué dans les exemples suivants. Par défaut, les valeurs Null ne sont pas incluses dans la sortie.  
  
## Exemple : noms de colonne séparés par des points  
 La requête suivante met en forme les cinq premières lignes de la table AdventureWorks Person au format JSON.  
  
 **Requête**  
  
```tsql  
SELECT TOP 5   
      BusinessEntityID As Id,  
      FirstName, LastName,  
      Title As 'Info.Title',  
      MiddleName As 'Info.MiddleName'  
  FROM Person.Person  
  FOR JSON PATH  
```  
  
 **Résultat**  
  
```json  
[  
    {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
    {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
    {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
    {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
    {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
]  
```  
  
 La clause FOR JSON PATH utilisera l’alias de colonne ou le nom de colonne pour déterminer le nom de la clé dans la sortie JSON. Si un alias contient des points, la clause FOR JSON PATH crée un objet imbriqué. Notez que les cellules contenant des valeurs NULL ne sont pas générées dans la sortie.  
  
## Exemple : plusieurs tables  
 Si vous faites référence à plusieurs tables dans la requête, les résultats sont représentés sous forme de liste plate, puis FOR JSON PATH imbrique chaque colonne à l’aide de son alias. La requête suivante crée un objet JSON par paire (OrderHeader OrderDetails) jointe dans la requête :  
  
 **Requête**  
  
```tsql  
SELECT TOP 2 SalesOrderNumber AS 'Order.Number',  
       OrderDate AS 'Order.Date',  
       UnitPrice AS 'Product.Price',  
       OrderQty AS 'Product.Quantity'  
FROM Sales.SalesOrderHeader H  
  INNER JOIN Sales.SalesOrderDetail D  
    ON H.SalesOrderID = D.SalesOrderID  
FOR JSON PATH  
```  
  
 **Résultat**  
  
```json  
[  
  {  
    "Order":{  
        "Number":"SO43659",  
        "Date":"2011-05-31T00:00:00"  
      },  
    "Product":{  
         "Price":2024.9940,  
         "Quantity":1  
     }  
  },  
  {  
    "Order":{ "Number":"SO43659“ },  
    "Product":{"Price":2024.9940}  
  }  
]  
```  
  
## Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  