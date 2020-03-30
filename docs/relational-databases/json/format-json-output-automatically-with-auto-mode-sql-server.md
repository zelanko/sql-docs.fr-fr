---
title: Mettre en forme la sortie JSON automatiquement avec le mode AUTO
ms.date: 07/17/2017
ms.prod: sql
ms.reviewer: genemi
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON AUTO
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
author: jovanpop-msft
ms.author: jovanpop
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1472c05c2ac4a9308a0fc941ed706d155203ca03
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "74095810"
---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>Mettre en forme la sortie JSON automatiquement avec le mode AUTO (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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
  
Quand une requête ne référence qu’une seule table, les résultats de la clause FOR JSON AUTO sont similaires à ceux de FOR JSON PATH. Dans ce cas, FOR JSON AUTO ne crée pas d’objets imbriqués. La seule différence est que FOR JSON AUTO génère des alias séparés par des points (par exemple, `Info.MiddleName` dans l’exemple suivant) en tant que clés avec des points, et non comme des objets imbriqués.  
  
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

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>En savoir plus sur JSON dans SQL Server et Azure SQL Database  
  
### <a name="microsoft-videos"></a>Vidéos Microsoft

Pour obtenir une présentation visuelle de la prise en charge intégrée de JSON dans SQL Server et Azure SQL Database, consultez les vidéos suivantes :

-   [SQL Server 2016 et prise en charge de JSON](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Utilisation de JSON dans SQL Server 2016 et Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON : un pont entre les mondes relationnel et NoSQL](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)

## <a name="see-also"></a>Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
