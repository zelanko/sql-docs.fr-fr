---
title: Mettre en forme automatiquement la sortie JSON avec le mode AUTO (SQL Server) | Microsoft Docs
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
helpviewer_keywords:
- FOR JSON AUTO
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3a04977311f1f04171caa1de0d15373d0b3cdf15
ms.lasthandoff: 04/11/2017

---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>Mettre en forme la sortie JSON automatiquement avec le mode AUTO (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Pour mettre en forme automatiquement la sortie de la clause **FOR JSON** en fonction de la structure de l’instruction **SELECT**, spécifiez l’option **AUTO**.  
  
Avec l’option **AUTO** , le format de la sortie JSON est automatiquement déterminé en fonction de l’ordre des colonnes dans la liste SELECT et de leurs tables sources. Vous ne pouvez pas modifier ce format.
 
 L’alternative consiste à utiliser l’option **PATH** pour conserver le contrôle sur la sortie.
 -   Pour plus d’informations sur l’option **PATH**, consultez [Mettre en forme la sortie JSON imbriquée à l’aide du mode PATH](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).
 -   Pour une vue d’ensemble des deux options, consultez [Mettre en forme les résultats de requête au format JSON avec FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).
  
 Une requête qui utilise l’option **FOR JSON AUTO** doit avoir une clause **FROM** .  
  
 Voici quelques exemples de la clause **FOR JSON** avec l’option **AUTO** .  
  
## <a name="examples"></a>Exemples  
 **Requête 1**  
  
Les résultats de la clause FOR JSON AUTO sont similaires à ceux de FOR JSON PATH lorsqu’une seule table est utilisée dans la requête. Dans ce cas, FOR JSON AUTO ne crée pas d’objets imbriqués. La seule différence est que FOR JSON AUTO génère des alias séparés par des points (par exemple, `Info.MiddleName` dans l’exemple suivant) en tant que clés avec des points, et non comme des objets imbriqués.  
  
```tsql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON AUTO  
```  
  
 **Résultat 1**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sánchez",
    "Info.MiddleName": "J"
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info.MiddleName": "Lee"
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
    "Info.Title": "Ms.",
    "Info.MiddleName": "A"
}]
```  
  
 **Requête 2**  
  
 Lorsque vous joignez des tables, les colonnes de la première table sont générées en tant que propriétés de l’objet racine. Les colonnes de la seconde table sont générées en tant que propriétés d’un objet imbriqué. Le nom de la table ou l’alias de la deuxième table (par exemple, `D` dans l’exemple suivant) est utilisé comme nom du tableau imbriqué.  
  
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
  
 **Résultat 2**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO43659",
    "D": [{
        "UnitPrice": 34.40
    }, {
        "UnitPrice": 134.24,
        "OrderQty": 5
    }]
}]
```  
 
 **Requête 3**  
 Au lieu d’utiliser FOR JSON AUTO, vous pouvez imbriquer une sous-requête FOR JSON PATH dans l’instruction SELECT, comme illustré dans l’exemple suivant. Cet exemple génère le même résultat que l’exemple précédent.  
  
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
  
 **Résultat 3**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO4390",
    "D": [{
        "UnitPrice": 24.99
    }]
}]
```  
  
## <a name="see-also"></a>Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

