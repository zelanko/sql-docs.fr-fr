---
description: Valider, interroger et modifier les données JSON avec des fonctions intégrées (SQL Server)
title: Valider, interroger et modifier les données JSON avec des fonctions intégrées
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- JSON, built-in functions
- functions (JSON)
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 76644f677a03f34312e6731f5a973167313ad22a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424091"
---
# <a name="validate-query-and-change-json-data-with-built-in-functions-sql-server"></a>Valider, interroger et modifier les données JSON avec des fonctions intégrées (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

La prise en charge intégrée de JSON inclut les fonctions intégrées suivantes décrites brièvement dans cette rubrique.  
  
-   [ISJSON](#ISJSON) teste si une chaîne contient un JSON valide.  
  
-   [JSON_VALUE](#VALUE) extrait une valeur scalaire à partir d’une chaîne JSON.  
  
-   [JSON_QUERY](#QUERY) extrait un objet ou un tableau à partir d’une chaîne JSON.  
  
-   [JSON_MODIFY](#MODIFY) met à jour la valeur d’une propriété dans une chaîne JSON et renvoie la chaîne JSON mise à jour.  
 
## <a name="json-text-for-the-examples-on-this-page"></a>Texte JSON des exemples de cette page

Les exemples de cette page utilisent le texte JSON similaire au contenu illustré dans l’exemple suivant :

```json
{
  "id": "WakefieldFamily",
  "parents": [
      { "familyName": "Wakefield", "givenName": "Robin" },
      { "familyName": "Miller", "givenName": "Ben" }
  ],
  "children": [
      {
        "familyName": "Merriam",
        "givenName": "Jesse",
        "gender": "female",
        "grade": 1,
        "pets": [
            { "givenName": "Goofy" },
            { "givenName": "Shadow" }
        ]
      },
      { 
        "familyName": "Miller",
         "givenName": "Lisa",
         "gender": "female",
         "grade": 8 }
  ],
  "address": { "state": "NY", "county": "Manhattan", "city": "NY" },
  "creationDate": 1431620462,
  "isRegistered": false
}
```

Ce document JSON, qui contient des éléments complexes imbriqués, est stocké dans l’exemple de table suivant :

```sql
CREATE TABLE Families (
   id int identity constraint PK_JSON_ID primary key,
   doc nvarchar(max)
)
``` 

##  <a name="validate-json-text-by-using-the-isjson-function"></a><a name="ISJSON"></a> Valider le texte JSON en utilisant la fonction ISJSON  
 La fonction **ISJSON** teste si une chaîne contient un JSON valide.  
  
L’exemple suivant retourne des lignes dans lesquelles la colonne JSON contient du texte JSON valide. Notez que, sans contrainte JSON explicite, vous pouvez entrer n’importe quel texte dans la colonne NVARCHAR :  
  
```sql  
SELECT *
FROM Families
WHERE ISJSON(doc) > 0 
```  

Pour plus d’informations, consultez [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md).  
  
##  <a name="extract-a-value-from-json-text-by-using-the-json_value-function"></a><a name="VALUE"></a> Extraire une valeur d’un texte JSON en utilisant la fonction JSON_VALUE  
La fonction **JSON_VALUE** extrait une valeur scalaire à partir d’une chaîne JSON. La requête suivante retourne les documents, pour lesquels le champ JSON `id` a la valeur `AndersenFamily`, triés selon les champs JSON `city` et `state` :

```sql  
SELECT JSON_VALUE(f.doc, '$.id')  AS Name, 
       JSON_VALUE(f.doc, '$.address.city') AS City,
       JSON_VALUE(f.doc, '$.address.county') AS County
FROM Families f 
WHERE JSON_VALUE(f.doc, '$.id') = N'AndersenFamily'
ORDER BY JSON_VALUE(f.doc, '$.address.city') DESC, JSON_VALUE(f.doc, '$.address.state') ASC
```  

Les résultats de cette requête sont présentés dans le tableau suivant :

| Nom | City | County |
| --- | --- | --- |
| AndersenFamily | NY | Manhattan |

Pour plus d’informations, consultez [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md).  
  
##  <a name="extract-an-object-or-an-array-from-json-text-by-using-the-json_query-function"></a><a name="QUERY"></a> Extraire un objet ou un tableau d’un texte JSON en utilisant la fonction JSON_QUERY  

La fonction **JSON_QUERY** extrait un objet ou un tableau à partir d’une chaîne JSON. L’exemple suivant montre comment renvoyer un fragment JSON dans les résultats de la requête.  
  
```sql
SELECT JSON_QUERY(f.doc, '$.address') AS Address,
       JSON_QUERY(f.doc, '$.parents') AS Parents,
       JSON_QUERY(f.doc, '$.parents[0]') AS Parent0
FROM Families f 
WHERE JSON_VALUE(f.doc, '$.id') = N'AndersenFamily'
```  
Les résultats de cette requête sont présentés dans le tableau suivant :

| Adresse | Parents | Parent0 |
| --- | --- | --- |
| { "state": "NY", "county": "Manhattan", "city": "NY" } | [{ "familyName": "Wakefield", "givenName": "Robin" }, {"familyName": "Miller", "givenName": "Ben" } ]| { "familyName": "Wakefield", "givenName": "Robin" } |

Pour plus d’informations, consultez [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  

## <a name="parse-nested-json-collections"></a>Analyser les collections JSON imbriquées

La fonction `OPENJSON` vous permet de transformer un sous-tableau JSON en ensemble de lignes, puis de le joindre à l’élément parent. Par exemple, vous pouvez retourner tous les documents de la famille, puis les « joindre » à leurs objets `children` stockés sous forme de tableau JSON interne :

```sql
SELECT JSON_VALUE(f.doc, '$.id')  AS Name, 
       JSON_VALUE(f.doc, '$.address.city') AS City,
       c.givenName, c.grade
FROM Families f
        CROSS APPLY OPENJSON(f.doc, '$.children')
            WITH(grade int, givenName nvarchar(100))  c
```

Les résultats de cette requête sont présentés dans le tableau suivant :

| Nom | City | givenName | grade |
| --- | --- | --- | --- |
| AndersenFamily | NY | Jesse | 1 |
| AndersenFamily | NY | Lisa | 8 |

Nous obtenons deux lignes comme résultat, car une ligne parente est jointe à deux lignes enfants produites par l’analyse de deux éléments du sous-tableau des enfants. La fonction `OPENJSON` analyse un fragment `children` de la colonne `doc` et retourne les valeurs `grade` et `givenName` de chaque élément sous la forme d’un ensemble de lignes. Cet ensemble de lignes peut être joint au document parent.
 
## <a name="query-nested-hierarchical-json-sub-arrays"></a>Interroger des sous-tableaux JSON hiérarchiques imbriqués

Vous pouvez appliquer plusieurs appels `CROSS APPLY OPENJSON` afin d’interroger des structures JSON imbriquées. Le document JSON utilisé dans cet exemple comporte un tableau imbriqué appelé `children`, où chaque enfant comporte un tableau imbriqué de `pets`. La requête suivante analyse les enfants de chaque document, retourne chaque objet de tableau sous forme de ligne, puis analyse le tableau `pets` :

```sql
SELECT  familyName,
    c.givenName AS childGivenName,
    c.firstName AS childFirstName,
    p.givenName AS petName 
FROM Families f 
    CROSS APPLY OPENJSON(f.doc) 
        WITH (familyName nvarchar(100), children nvarchar(max) AS JSON)
        CROSS APPLY OPENJSON(children) 
        WITH (givenName nvarchar(100), firstName nvarchar(100), pets nvarchar(max) AS JSON) as c
            OUTER APPLY OPENJSON (pets)
            WITH (givenName nvarchar(100))  as p
```

Le premier appel `OPENJSON` retourne un fragment du tableau `children` à l’aide de la clause AS JSON. Ce fragment de tableau est fourni à la deuxième fonction `OPENJSON` qui retourne les valeurs `givenName`, `firstName` de chaque enfant, ainsi que le tableau de `pets`. Le tableau de `pets` est fourni à la troisième fonction `OPENJSON` qui retourne la valeur `givenName` de l’animal.
Les résultats de cette requête sont présentés dans le tableau suivant :

| familyName | childGivenName | childFirstName | petName |
| --- | --- | --- | --- |
| AndersenFamily | Jesse | Merriam | Goofy |
| AndersenFamily | Jesse | Merriam | Shadow |
| AndersenFamily | Lisa | Miller| `NULL` |

Le document racine est joint avec deux lignes `children` retournées par le premier appel `OPENJSON(children)` qui fait deux lignes (ou tuples). Ensuite, chaque ligne est jointe aux nouvelles lignes générées par `OPENJSON(pets)` à l’aide de l’opérateur `OUTER APPLY`. Jesse a deux animaux, donc `(AndersenFamily, Jesse, Merriam)` est joint avec deux lignes générées pour Goofy et Shadow. Lisa n’a pas d’animaux, donc aucune ligne n’est retournée par `OPENJSON(pets)` pour ce tuple. En revanche, étant donné que nous utilisons `OUTER APPLY`, nous obtenons `NULL` dans la colonne. Si nous mettons `CROSS APPLY` au lieu de `OUTER APPLY`, Lisa n’est pas retournée dans le résultat, car il n’y a pas de lignes d’animaux pouvant être jointes à ce tuple.

##  <a name="compare-json_value-and-json_query"></a><a name="JSONCompare"></a> Comparer JSON_VALUE et JSON_QUERY  
La principale différence entre **JSON_VALUE** et **JSON_QUERY** est que **JSON_VALUE** retourne une valeur scalaire, tandis que **JSON_QUERY** retourne un objet ou un tableau.  
  
Considérons l’exemple de texte JSON suivant :  
  
```json  
{
    "a": "[1,2]",
    "b": [1, 2],
    "c": "hi"
}  
```  
  
Dans cet exemple de texte JSON, les membres de données « a » et « c » sont des valeurs de chaîne, tandis que le membre de données « b » est un tableau. **JSON_VALUE** et **JSON_QUERY** retournent les résultats suivants :  
  
|Chemin d’accès|**JSON_VALUE** retourne|**JSON_QUERY** retourne|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL ou erreur|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL ou erreur|  
|**$.b**|NULL ou erreur|[1,2]|  
|**$.b[0]**|1|NULL ou erreur|  
|**$.c**|hi|NULL ou erreur|  
  
## <a name="test-json_value-and-json_query-with-the-adventureworks-sample-database"></a>Tester JSON_VALUE et JSON_QUERY avec la base de données exemple AdventureWorks  
Testez les fonctions intégrées décrites dans cette rubrique en exécutant les exemples suivants avec la base de données exemple AdventureWorks. Pour savoir où récupérer la base de données AdventureWorks et comment ajouter des données JSON à des fins de test en exécutant un script, consultez [Tester la prise en charge de JSON intégrée](json-data-sql-server.md#test-drive-built-in-json-support-with-the-adventureworks-sample-database).
  
Dans les exemples suivants, la colonne `Info` de la table `SalesOrder_json` contient un texte JSON.  
  
### <a name="example-1---return-both-standard-columns-and-json-data"></a>Exemple 1 : Renvoyer les colonnes standard et les données JSON  
La requête suivante retourne des valeurs des deux colonnes relationnelles standard et d’une colonne JSON.  
  
```sql  
SELECT SalesOrderNumber, OrderDate, Status, ShipDate, Status, AccountNumber, TotalDue,
 JSON_QUERY(Info,'$.ShippingInfo') ShippingInfo,
 JSON_QUERY(Info,'$.BillingInfo') BillingInfo,
 JSON_VALUE(Info,'$.SalesPerson.Name') SalesPerson,
 JSON_VALUE(Info,'$.ShippingInfo.City') City,
 JSON_VALUE(Info,'$.Customer.Name') Customer,
 JSON_QUERY(OrderItems,'$') OrderItems
FROM Sales.SalesOrder_json
WHERE ISJSON(Info) > 0
```  
  
### <a name="example-2--aggregate-and-filter-json-values"></a>Exemple 2 : Agréger et filtrer des valeurs JSON  
La requête suivante agrège les sous-totaux par nom de client (stocké dans JSON) et état (stocké dans une colonne ordinaire). Elle filtre ensuite les résultats par ville (stockés dans JSON) et OrderDate (stockés dans une colonne ordinaire).  
  
```sql  
DECLARE @territoryid INT;
DECLARE @city NVARCHAR(32);

SET @territoryid=3;

SET @city=N'Seattle';

SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total
FROM Sales.SalesOrder_json
WHERE TerritoryID=@territoryid
 AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city
 AND OrderDate > '1/1/2015'
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status
HAVING SUM(SubTotal)>1000
```  
  
##  <a name="update-property-values-in-json-text-by-using-the-json_modify-function"></a><a name="MODIFY"></a> Mettre à jour les valeurs de propriété dans un texte JSON en utilisant la fonction JSON_MODIFY  
La fonction **JSON_MODIFY** met à jour la valeur d’une propriété dans une chaîne JSON et retourne la chaîne JSON mise à jour.  
  
L’exemple suivant met à jour la valeur d’une propriété JSON dans une variable contenant du texte JSON.  
  
```sql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')    
```  
  
 Pour plus d’informations, consultez [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md).  
  
## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>En savoir plus sur JSON dans SQL Server et Azure SQL Database  
  
### <a name="microsoft-videos"></a>Vidéos Microsoft

Pour obtenir une présentation visuelle de la prise en charge intégrée de JSON dans SQL Server et Azure SQL Database, consultez les vidéos suivantes :

-   [SQL Server 2016 et prise en charge de JSON](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Utilisation de JSON dans SQL Server 2016 et Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON : un pont entre les mondes relationnel et NoSQL](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>Voir aussi  
 [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)   
 [Expressions de chemin JSON &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  
