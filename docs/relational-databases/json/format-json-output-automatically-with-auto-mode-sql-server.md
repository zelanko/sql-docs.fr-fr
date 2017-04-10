---
title: "Mettre en forme la sortie JSON automatiquement avec le mode AUTO (SQL Server) | Microsoft Docs"
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
  - "FOR JSON AUTO"
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 15
---
# Mettre en forme la sortie JSON automatiquement avec le mode AUTO (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Pour mettre en forme la sortie JSON automatiquement en fonction de la structure de l’instruction **SELECT** , spécifiez l’option  **AUTO** avec la clause **FOR JSON** .  
  
 Avec l’option **AUTO** , le format de la sortie JSON est automatiquement déterminé en fonction de l’ordre des colonnes dans la liste SELECT et de leurs tables sources. Vous ne pouvez pas modifier ce format.  
  
 Une requête qui utilise l’option **FOR JSON AUTO** doit avoir une clause **FROM** .  
  
 Voici quelques exemples de la clause **FOR JSON** avec l’option **AUTO** .  
  
## Exemples  
 **Requête 1**  
  
 Les résultats de la clause FOR JSON AUTO sont similaires à ceux de FOR JSON PATH si une seule table est utilisée dans la requête. Dans ce cas, FOR JSON AUTO ne crée pas d’objets imbriqués. La seule différence est que les alias séparés par des points seront générés en tant que clés avec des points (autrement dit, FOR JSON AUTO n’utilisera pas d’alias de colonne pour la mise en forme).  
  
```tsql  
SELECT TOP 5   
      BusinessEntityID As Id,  
      FirstName, LastName,  
      Title As 'Info.Title',  
      MiddleName As 'Info.MiddleName'  
  FROM Person.Person  
  FOR JSON AUTO  
```  
  
 **Résultat 1**  
  
```json  
[  
      {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info.MiddleName":"J"},  
      {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info.MiddleName":"Lee"},  
      {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
      {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
      {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info.Title":"Ms.","Info.MiddleName":"A"}  
]  
```  
  
 **Requête 2**  
  
 Lorsque vous joignez des tables, les colonnes de la première table sont générées en tant que propriétés de l’objet racine. Les colonnes de la seconde table sont générées en tant que propriétés d’un objet imbriqué. Le nom de table ou l’alias de la deuxième table est utilisé comme nom du tableau imbriqué.  
  
```tsql  
SELECT TOP 2 SalesOrderNumber,  
       OrderDate,  
       UnitPrice,  
       OrderQty  
FROM Sales.SalesOrderHeader H  
  INNER JOIN Sales.SalesOrderDetail D  
    ON H.SalesOrderID = D.SalesOrderID  
FOR JSON AUTO  
```  
  
 **Résultat 2**  
  
```json  
[  
  {  
       "SalesOrderNumber":"SO43659",  
        "OrderDate":"2011-05-31T00:00:00",  
        "D":[  
            {"UnitPrice":24.99, "OrderQty":1  }  
         ]  
  },  
  {  
       "SalesOrderNumber":"SO43659" ,  
       "D":[  
          { "UnitPrice":34.40  },  
          { "UnitPrice":134.24, "OrderQty":5 }  
        ]  
  }  
]  
  
```  
  
## Exemples - Générer une sortie JSON imbriquée  
 Au lieu d’utiliser FOR JSON AUTO, vous pouvez écrire des requêtes FOR JSON imbriquées dans la partie SELECT de la requête principale avec la clause FOR JSON PATH, comme illustré dans les exemples suivants.  
  
 **Requête 1**  
  
```tsql  
SELECT TOP 2  
   SalesOrderNumber,  
   OrderDate,  
   (SELECT UnitPrice, OrderQty  
     FROM Sales.SalesOrderDetail AS D  
     WHERE H.SalesOrderID = D.SalesOrderID  
    FOR JSON PATH) AS D  
FROM Sales.SalesOrderHeader AS H  
FOR JSON PATH  
```  
  
 **Résultat 1**  
  
```json  
[  
  {  
       "SalesOrderNumber":"SO43659",  
        "OrderDate":"2011-05-31T00:00:00",  
        "D":[  
            { "UnitPrice":24.99,  "OrderQty":1 }  
         ]  
  },  
  {  
       "SalesOrderNumber":"SO4390" ,  
       "D":[  
            { "UnitPrice":24.99 }  
        ]  
  }  
]  
  
```  
  
## Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  