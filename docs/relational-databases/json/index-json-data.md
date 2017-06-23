---
title: "Indexer des données JSON | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, indexing JSON data
- indexing JSON data
ms.assetid: ced241e1-ff09-4d6e-9f04-a594a9d2f25e
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 3ed7a51b28d2b17b3239f971d0f4f684bec145cd
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="index-json-data"></a>Indexer des données JSON
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Dans SQL Server 2016, JSON n’est pas un type de données intégré, et SQL Server n’a pas d’index JSON personnalisés. Vous pouvez optimiser vos requêtes sur des documents JSON, toutefois, à l’aide d’index standard. 

Index de base de données améliorent les performances des opérations de filtrage et de tri. Sans index, SQL Server doit effectuer une analyse de table complète chaque fois que vous interrogez des données.  
  
## <a name="index-json-properties-by-using-computed-columns"></a>Indexer les propriétés JSON à l’aide des colonnes calculées  
Lorsque vous stockez des données JSON dans SQL Server, en général, vous souhaitez filtrer ou trier les résultats de requête par une ou plusieurs *propriétés* des documents JSON.  

### <a name="example"></a>Exemple 
Dans cet exemple, supposons qu’AdventureWorks `SalesOrderHeader` table a un `Info` colonne qui contient des informations au format JSON de commandes. Par exemple, il contient des informations sur le client, commercial, les adresses de livraison et de facturation et ainsi de suite. Vous souhaitez utiliser des valeurs à partir de la `Info` colonne à filtrer les commandes pour un client.

### <a name="query-to-optimize"></a>Pour optimiser les requêtes
Voici un exemple du type de requête que vous souhaitez optimiser à l’aide d’un index.  
  
```sql  
SELECT SalesOrderNumber,
    OrderDate,
    JSON_VALUE(Info, '$.Customer.Name') AS CustomerName
FROM Sales.SalesOrderHeader
WHERE JSON_VALUE(Info, '$.Customer.Name') = N'Aaron Campbell' 
```  

### <a name="example-index"></a>Index de l’exemple
Si vous souhaitez accélérer vos filtres ou `ORDER BY` clauses sur une propriété d’un document JSON, vous pouvez utiliser les mêmes index que vous utilisez déjà sur d’autres colonnes. Toutefois, vous ne pouvez pas *directement* référencer des propriétés dans les documents JSON.
    
1.  Vous devez d’abord créer une « colonne virtuelle » qui renvoie les valeurs que vous souhaitez utiliser pour le filtrage.
2.  Vous devez ensuite créer un index sur cette colonne virtuelle.  
  
L’exemple suivant crée une colonne calculée qui peut être utilisée pour l’indexation. Il crée ensuite un index sur la nouvelle colonne calculée. Cet exemple crée une colonne qui affiche le nom du client, qui est stocké dans le `$.Customer.Name` chemin d’accès dans les données JSON. 
  
```sql  
ALTER TABLE Sales.SalesOrderHeader
ADD vCustomerName AS JSON_VALUE(Info,'$.Customer.Name')

CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)  
```  
### <a name="more-info-about-the-computed-column"></a>Plus d’informations sur la colonne calculée 
La colonne calculée n’est pas persistante. Elle est calculée uniquement lorsque l’index doit être recréé. Elle n’occupe pas d’espace supplémentaire dans la table.   
  
Il est important que vous créez la colonne calculée avec la même expression que vous prévoyez d’utiliser dans vos requêtes - dans cet exemple, l’expression est `JSON_VALUE(Info, '$.Customer.Name')`.  
  
Vous n’avez pas besoin de réécrire vos requêtes. Si vous utilisez des expressions avec le `JSON_VALUE` fonction, comme indiqué dans l’exemple de requête ci-dessus, SQL Server détecte qu’il existe une colonne calculée équivalente avec la même expression et applique un index si possible.

### <a name="execution-plan-for-this-example"></a>Plan d’exécution pour cet exemple
Voici le plan d’exécution de la requête dans cet exemple.  
  
![Plan d’exécution](../../relational-databases/json/media/jsonindexblog1.png "Plan d’exécution")  
  
Au lieu d’une analyse de table complète, SQL Server utilise une recherche d’index dans l’index non cluster et recherche les lignes qui répondent aux conditions spécifiées. Ensuite, il utilise une recherche de clés dans le `SalesOrderHeader` table pour extraire les autres colonnes sont référencées dans cet exemple, la requête `SalesOrderNumber` et `OrderDate`.  
 
### <a name="optimize-the-index-further-with-included-columns"></a>Optimiser davantage l’index avec colonnes incluses
Vous pouvez éviter cette recherche supplémentaire dans la table si vous ajoutez les colonnes requises dans l’index. Vous pouvez ajouter ces colonnes en tant que colonnes incluses standard, comme indiqué dans l’exemple suivant, qui étend la `CREATE INDEX` exemple ci-dessus.  
  
```sql  
CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)
INCLUDE(SalesOrderNumber,OrderDate)
```  
  
Dans ce cas SQL Server ne doit pas nécessairement lire les données supplémentaires à partir de la `SalesOrderHeader` de table, car tout ce dont il a besoin est inclus dans l’index JSON non cluster. Il s’agit d’un bon moyen pour combiner des données JSON et de colonnes dans les requêtes et créer des index optimaux pour votre charge de travail.  
  
## <a name="json-indexes-are-collation-aware-indexes"></a>Les index JSON prennent en charge le classement  
Une fonctionnalité importante des index sur les données JSON est que les index sont en charge le classement. Le résultat de la `JSON_VALUE` fonction que vous utilisez lorsque vous créez la colonne calculée est une valeur de texte qui hérite son classement de l’expression d’entrée. Par conséquent, les valeurs de l’index sont triées à l’aide des règles de classement définies dans les colonnes sources.  
  
À titre d’illustration, l’exemple suivant crée une table de collection simple avec une clé primaire et un contenu JSON.  
  
```sql  
CREATE TABLE JsonCollection
 (
  id INT IDENTITY CONSTRAINT PK_JSON_ID PRIMARY KEY,
  json NVARCHAR(MAX) COLLATE SERBIAN_CYRILLIC_100_CI_AI
  CONSTRAINT [Content should be formatted as JSON]
  CHECK(ISJSON(json)>0)
 ) 
```  
  
La commande précédente spécifie le classement serbe cyrillique pour la colonne JSON. L’exemple suivant remplit la table et crée un index sur la propriété de nom.  
  
```sql  
INSERT INTO JsonCollection
VALUES
(N'{"name":"Иво","surname":"Андрић"}'),
(N'{"name":"Андрија","surname":"Герић"}'),
(N'{"name":"Владе","surname":"Дивац"}'),
(N'{"name":"Новак","surname":"Ђоковић"}'),
(N'{"name":"Предраг","surname":"Стојаковић"}'),
(N'{"name":"Михајло","surname":"Пупин"}'),
(N'{"name":"Борислав","surname":"Станковић"}'),
(N'{"name":"Владимир","surname":"Грбић"}'),
(N'{"name":"Жарко","surname":"Паспаљ"}'),
(N'{"name":"Дејан","surname":"Бодирога"}'),
(N'{"name":"Ђорђе","surname":"Вајферт"}'),
(N'{"name":"Горан","surname":"Бреговић"}'),
(N'{"name":"Милутин","surname":"Миланковић"}'),
(N'{"name":"Никола","surname":"Тесла"}')
GO
  
ALTER TABLE JsonCollection
ADD vName AS JSON_VALUE(json,'$.name')

CREATE INDEX idx_name
ON JsonCollection(vName)
```  
  
Les commandes précédentes créent un index standard sur la colonne calculée `vName`, qui représente la valeur de l’objet JSON `$.name` propriété. Dans la page de codes cyrilliques serbes, l’ordre des lettres est « А », « Б », « В », « Г », « Д », « Ђ », « Е », etc. L’ordre des éléments de l’index est compatible avec les règles cyrilliques serbes, car le résultat de la `JSON_VALUE` fonction hérite son classement de la colonne source. L’exemple suivant interroge cette collection et trie les résultats par nom.  
  
```sql  
SELECT JSON_VALUE(json,'$.name'),*
FROM JsonCollection
ORDER BY JSON_VALUE(json,'$.name')
```  
  
 Si vous examinez le plan d’exécution, vous pouvez constater qu’il utilise les valeurs triées de l’index non cluster.  
  
 ![Plan d’exécution](../../relational-databases/json/media/jsonindexblog2.png "Plan d’exécution")  
  
 Bien que la requête comporte une `ORDER BY` clause, le plan d’exécution n’utilise pas un opérateur de tri. L’index JSON est déjà trié selon les règles cyrilliques serbes. Par conséquent, SQL Server peut utiliser l’index non cluster dans lequel les résultats sont déjà triés.  
  
 Toutefois, si nous modifions le classement de la `ORDER BY` expression, par exemple, si nous avons `COLLATE French_100_CI_AS_SC` après le `JSON_VALUE` fonction, nous obtenons un plan d’exécution de requête différent.  
  
 ![Plan d’exécution](../../relational-databases/json/media/jsonindexblog3.png "Plan d’exécution")  
  
 Étant donné que l’ordre des valeurs de l’index n’est pas compatible avec les règles de classement françaises, SQL Server ne peut pas utiliser l’index pour trier les résultats. Par conséquent, il ajoute un opérateur de tri qui trie les résultats à l’aide des règles de classement françaises.  
 
## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la fonction intégrée prise en charge de JSON dans SQL Server  
Pour un grand nombre de solutions spécifiques, utilisez des cas et des recommandations, consultez le [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et dans la base de données SQL Azure par programme Jovan Popovic Gestionnaire Microsoft.

