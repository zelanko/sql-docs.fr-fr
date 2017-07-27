---
title: "Valider, interroger et modifier les données JSON avec des fonctions intégrées (SQL Server) | Microsoft Docs"
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
- JSON, built-in functions
- functions (JSON)
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1aa87e3d821e6d111948baa0843edf31d087d739
ms.openlocfilehash: 017f0c1a33ea00e675115d91e6654ec7730b4bd3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/18/2017

---
# <a name="validate-query-and-change-json-data-with-built-in-functions-sql-server"></a>Valider, interroger et modifier les données JSON avec des fonctions intégrées (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

La prise en charge intégrée de JSON inclut les fonctions intégrées suivantes décrites brièvement dans cette rubrique.  
  
-   [ISJSON](#ISJSON) teste si une chaîne contient un JSON valide.  
  
-   [JSON_VALUE](#VALUE) extrait une valeur scalaire à partir d’une chaîne JSON.  
  
-   [JSON_QUERY](#QUERY) extrait un objet ou un tableau à partir d’une chaîne JSON.  
  
-   [JSON_MODIFY](#MODIFY) met à jour la valeur d’une propriété dans une chaîne JSON et renvoie la chaîne JSON mise à jour.  
 
## <a name="json-text-for-the-examples-on-this-page"></a>Texte JSON des exemples de cette page
Les exemples de cette page utilisent le texte JSON suivant, qui contient un élément complexe.

```sql 
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }' 
``` 

##  <a name="ISJSON"></a> Valider le texte JSON en utilisant la fonction ISJSON  
 La fonction **ISJSON** teste si une chaîne contient un JSON valide.  
  
L’exemple suivant retourne des lignes dans lesquelles la colonne `json_col` contient un JSON valide.  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  

Pour plus d’informations, consultez [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md).  
  
##  <a name="VALUE"></a> Extraire une valeur d’un texte JSON en utilisant la fonction JSON_VALUE  
La fonction **JSON_VALUE** extrait une valeur scalaire à partir d’une chaîne JSON.  
  
L’exemple suivant extrait la valeur de la propriété JSON imbriquée `town` dans une variable locale.  
  
```sql  
SET @town = JSON_VALUE(@jsonInfo, '$.info.address.town')  
```  
  
Pour plus d’informations, consultez [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md).  
  
##  <a name="QUERY"></a> Extraire un objet ou un tableau d’un texte JSON en utilisant la fonction JSON_QUERY  
La fonction **JSON_QUERY** extrait un objet ou un tableau à partir d’une chaîne JSON.  
 
L’exemple suivant montre comment renvoyer un fragment JSON dans les résultats de la requête.  
  
```sql  
SELECT FirstName, LastName, JSON_QUERY(jsonInfo,'$.info.address') AS Address
FROM Person.Person
ORDER BY LastName
```  
  
Pour plus d’informations, consultez [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  
  
##  <a name="JSONCompare"></a> Comparer JSON_VALUE et JSON_QUERY  
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
  
|Chemin d'accès|**JSON_VALUE** retourne|**JSON_QUERY** retourne|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL ou erreur|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL ou erreur|  
|**$.b**|NULL ou erreur|[1,2]|  
|**$.b[0]**|1|NULL ou erreur|  
|**$.c**|hi|NULL ou erreur|  
  
## <a name="test-jsonvalue-and-jsonquery-with-the-adventureworks-sample-database"></a>Tester JSON_VALUE et JSON_QUERY avec la base de données exemple AdventureWorks  
Testez les fonctions intégrées décrites dans cette rubrique en exécutant les exemples suivants avec la base de données exemple AdventureWorks, qui contient les données JSON. Pour obtenir la base de données exemple AdventureWorks, [cliquez ici](http://www.microsoft.com/en-us/download/details.aspx?id=49502).  
  
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
  
##  <a name="MODIFY"></a> Mettre à jour les valeurs de propriété dans un texte JSON en utilisant la fonction JSON_MODIFY  
La fonction **JSON_MODIFY** met à jour la valeur d’une propriété dans une chaîne JSON et retourne la chaîne JSON mise à jour.  
  
L’exemple suivant met à jour la valeur d’une propriété JSON dans une variable contenant du texte JSON.  
  
```sql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')    
```  
  
 Pour plus d’informations, consultez [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md).  
  
## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la fonction intégrée prise en charge de JSON dans SQL Server  
Pour un grand nombre de solutions spécifiques, utilisez des cas et des recommandations, consultez le [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et dans la base de données SQL Azure par programme Jovan Popovic Gestionnaire Microsoft.
  
## <a name="see-also"></a>Voir aussi  
 [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)   
 [Expressions de chemin JSON &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  

