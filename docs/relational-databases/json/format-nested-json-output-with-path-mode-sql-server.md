---
title: "Formater la sortie JSON imbriquée avec le mode PATH (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 12dfc255364a410de1ad5c75f3abf38155d6d70f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/31/2017

---
# <a name="format-nested-json-output-with-path-mode-sql-server"></a>Formater la sortie JSON imbriquée avec le mode PATH (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Pour conserver le contrôle intégral de la sortie de la clause **FOR JSON**, spécifiez l’option **PATH**.  
  
Le mode**PATH** vous permet de créer des objets wrapper et d’imbriquer des propriétés complexes. Les résultats sont présentés sous forme de tableau d'objets JSON.  
  
L’alternative consiste à utiliser l’option **AUTO** pour mettre en forme la sortie automatiquement en fonction de la structure de l’instruction **SELECT**.
 -   Pour plus d’informations sur l’option **AUTO**, consultez [Mettre en forme la sortie JSON automatiquement avec le mode AUTO](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).
 -   Pour obtenir une vue d’ensemble des deux options, consultez [Mettre en forme les résultats de requête au format JSON avec FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).
 
Voici quelques exemples de clause **FOR JSON** avec l’option **PATH** . Formatez les résultats imbriqués en utilisant des noms de colonne séparés par des points ou des requêtes imbriquées, comme indiqué dans les exemples suivants. Par défaut, les valeurs Null ne sont pas incluses dans la sortie de **FOR JSON**.  

## <a name="example---dot-separated-column-names"></a>Exemple : noms de colonne séparés par des points  
La requête suivante met en forme les cinq premières lignes de la table AdventureWorks `Person` au format JSON.  

La clause **FOR JSON PATH** utilise l’alias de colonne ou le nom de colonne pour déterminer le nom de la clé dans la sortie JSON. Si un alias contient des points, l’option PATH crée des objets imbriqués.  

 **Requête**  
  
```sql  
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
    "LastName": "Sanchez",
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
Si vous référencez plusieurs tables dans une requête, **FOR JSON PATH** imbrique chaque colonne à l’aide de son alias. La requête suivante crée un objet JSON par paire (OrderHeader, OrderDetails) jointe dans la requête. 
  
 **Requête**  
  
```sql  
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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la prise en charge intégrée de JSON dans SQL Server  
Pour accéder à un grand nombre de solutions spécifiques, de cas d’usage et de recommandations, consultez les [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et Azure SQL Database, écrits par Jovan Popovic (Microsoft Program Manager).

## <a name="see-also"></a>Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  

