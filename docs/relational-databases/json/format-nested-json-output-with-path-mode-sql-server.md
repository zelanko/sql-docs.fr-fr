---
title: "Formater la sortie JSON imbriquée avec le mode PATH (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6deec926bf016b43ee1476a09cbe2b75c3166239
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="format-nested-json-output-with-path-mode-sql-server"></a>Formater la sortie JSON imbriquée avec le mode PATH (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Pour conserver le contrôle intégral de la sortie de la clause **FOR JSON**, spécifiez l’option **PATH**.  
  
 Le mode**PATH** vous permet de créer des objets wrapper et d’imbriquer des propriétés complexes. Les résultats sont présentés sous forme de tableau d'objets JSON.  
  
L’alternative consiste à utiliser l’option **AUTO** pour mettre en forme la sortie automatiquement en fonction de la structure de l’instruction **SELECT**.
 -   Pour plus d’informations sur l’option **AUTO**, consultez [Mettre en forme la sortie JSON automatiquement avec le mode AUTO](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).
 -   Pour obtenir une vue d’ensemble des deux options, consultez [Mettre en forme les résultats de requête au format JSON avec FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).
 
Voici quelques exemples de clause **FOR JSON** avec l’option **PATH** . Formatez les résultats imbriqués en utilisant des noms de colonne séparés par des points ou des requêtes imbriquées, comme indiqué dans les exemples suivants. Par défaut, les valeurs Null ne sont pas incluses dans la sortie de **FOR JSON**.  

## <a name="example---dot-separated-column-names"></a>Exemple : noms de colonne séparés par des points  
 La requête suivante met en forme les cinq premières lignes de la table AdventureWorks Person au format JSON.  

La clause FOR JSON PATH utilise l’alias de colonne ou le nom de colonne pour déterminer le nom de la clé dans la sortie JSON. Si un alias contient des points, l’option PATH crée des objets imbriqués.  

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
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sánchez",
    "Info": {
        "MiddleName": "J"
    }
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info": {
        "MiddleName": "Lee"
    }
}, {
    "Id": 3,
    "FirstName": "Roberto",
    "LastName": "Tamburello"
}, {
    "Id": 4,
    "FirstName": "Rob",
    "LastName": "Walters"
}, {
    "Id": 5,
    "FirstName": "Gail",
    "LastName": "Erickson",
    "Info": {
        "Title": "Ms.",
        "MiddleName": "A"
    }
}]
```  
   
## <a name="example---multiple-tables"></a>Exemple : plusieurs tables  
 Si vous référencez plusieurs tables dans une requête, FOR JSON PATH imbrique chaque colonne à l’aide de son alias. La requête suivante crée un objet JSON par paire (OrderHeader, OrderDetails) jointe dans la requête. 
  
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
[{
    "Order": {
        "Number": "SO43659",
        "Date": "2011-05-31T00:00:00"
    },
    "Product": {
        "Price": 2024.9940,
        "Quantity": 1
    }
}, {
    "Order": {
        "Number": "SO43659"
    },
    "Product": {
        "Price": 2024.9940
    }
}]
```  
  
## <a name="see-also"></a>Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

