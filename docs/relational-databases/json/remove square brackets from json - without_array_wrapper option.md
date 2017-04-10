---
title: "Supprimer les crochets de la sortie JSON avec l’option WITHOUT_ARRAY_WRAPPER (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WITHOUT_ARRAY_WRAPPER"
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Supprimer les crochets de la sortie JSON avec l’option WITHOUT_ARRAY_WRAPPER (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Pour supprimer les crochets qui entourent par défaut la sortie JSON de la clause **FOR JSON**, spécifiez l’option **WITHOUT_ARRAY_WRAPPER**. Utilisez cette option pour générer un seul objet JSON en sortie.  
  
 Si vous ne spécifiez pas cette option, la sortie JSON est placée entre crochets.  
  
## Exemples  
 L’exemple suivant montre la sortie de la clause **FOR JSON** avec et sans l’option **WITHOUT_ARRAY_WRAPPER**.  
  
 **Requête**  
  
```tsql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **Résultat** avec l’option **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{ "year":2015, "month":12, "day":15 }  
```  
  
 **Résultat** sans l’option **WITHOUT_ARRAY_WRAPPER**  
  
```json  
[ { "year":2015, "month":12, "day":15 } ]  
```  
  
 Voici un autre exemple de clause **FOR JSON** avec l’option **WITHOUT_ARRAY_WRAPPER**.  
  
 **Requête**  
  
```tsql  
SELECT TOP 1 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **Résultat** avec l’option **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{  
    "SalesOrderNumber":"SO43660",  
    "OrderDate":"2011-05-31T00:00:00",  
    "Status":5  
}  
```  
  
 **Résultat** sans l’option **WITHOUT_ARRAY_WRAPPER**  
  
```json  
[  
    {  
        "SalesOrderNumber":"SO43660",  
        "OrderDate":"2011-05-31T00:00:00",  
        "Status":5  
    }  
]  
```  
  
## Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  