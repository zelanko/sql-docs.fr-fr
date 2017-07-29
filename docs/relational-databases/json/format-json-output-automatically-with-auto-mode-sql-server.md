---
title: Mettre en forme automatiquement la sortie JSON avec le mode AUTO (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
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
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 1aa87e3d821e6d111948baa0843edf31d087d739
ms.openlocfilehash: 09e81a8bbc77e9bbf9f76bb669ab53bd549bef85
ms.contentlocale: fr-fr
ms.lasthandoff: 07/18/2017

---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>Mettre en forme la sortie JSON automatiquement avec le mode AUTO (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Pour mettre en forme automatiquement la sortie de la clause **FOR JSON** en fonction de la structure de l’instruction **SELECT**, spécifiez l’option **AUTO**.  
  
Quand vous spécifiez l’option **AUTO**, le format de la sortie JSON est automatiquement déterminé en fonction de l’ordre des colonnes dans la liste SELECT et de leurs tables sources. Vous ne pouvez pas modifier ce format.
 
L’alternative consiste à utiliser l’option **PATH** pour conserver le contrôle sur la sortie.
-   Pour plus d’informations sur l’option **PATH**, consultez [Mettre en forme la sortie JSON imbriquée à l’aide du mode PATH](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).
-   Pour une vue d’ensemble des deux options, consultez [Mettre en forme les résultats de requête au format JSON avec FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).

Une requête qui utilise l’option **FOR JSON AUTO** doit avoir une clause **FROM** .  
  
Voici quelques exemples de la clause **FOR JSON** avec l’option **AUTO** .  
  
## <a name="examples"></a>Exemples

### <a name="example-1"></a>Exemple 1
 **Requête**  
  
Quand une requête ne fait référence qu’à une seule table, les résultats de la clause FOR JSON AUTO sont similaires à ceux de FOR JSON PATH. Dans ce cas, FOR JSON AUTO ne crée pas d’objets imbriqués. La seule différence est que FOR JSON AUTO génère des alias séparés par des points (par exemple, `Info.MiddleName` dans l’exemple suivant) en tant que clés avec des points, et non comme des objets imbriqués.  
  
```sql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON AUTO  
```  
  
 **Résultat**  
  
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

### <a name="example-2"></a>Exemple 2

**Requête**  
  
Lorsque vous joignez des tables, les colonnes de la première table sont générées en tant que propriétés de l’objet racine. Les colonnes de la seconde table sont générées en tant que propriétés d’un objet imbriqué. Le nom de la table ou l’alias de la deuxième table (par exemple, `D` dans l’exemple suivant) est utilisé comme nom du tableau imbriqué.  
  
```sql  
SELECT TOP 2 SalesOrderNumber,  
        OrderDate,  
        UnitPrice,  
        OrderQty  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON AUTO   
```  
  
**Résultat**  
  
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

### <a name="example-3"></a>Exemple 3
 
**Requête**  
Au lieu d’utiliser FOR JSON AUTO, vous pouvez imbriquer une sous-requête FOR JSON PATH dans l’instruction SELECT, comme illustré dans l’exemple suivant. Cet exemple génère le même résultat que l’exemple précédent.  
  
```sql  
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
  
**Résultat**  
  
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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la fonction intégrée prise en charge de JSON dans SQL Server  
Pour un grand nombre de solutions spécifiques, utilisez des cas et des recommandations, consultez le [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et dans la base de données SQL Azure par programme Jovan Popovic Gestionnaire Microsoft.

## <a name="see-also"></a>Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  

