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
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cf3c58c7d71a98bfaa1f27611762bf7fb3fe8725
ms.lasthandoff: 04/11/2017

---
# <a name="index-json-data"></a>Indexer des données JSON
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Les index de base de données permettent d’améliorer les performances de vos opérations de filtrage et de tri. Sans index, SQL Server doit effectuer une analyse de table complète chaque fois que vous interrogez des données.  
  
 JSON n’est pas un type de données intégré dans SQL Server 2016 et SQL Server 2016 ne possède pas d’index JSON personnalisés. Toutefois, vous pouvez optimiser vos requêtes sur des documents JSON à l’aide d’index standard.  
  
## <a name="index-json-properties-by-using-computed-columns"></a>Indexer les propriétés JSON à l’aide des colonnes calculées  
 Lorsque vous stockez des données JSON dans SQL Server, c’est généralement parce que vous souhaitez filtrer ou trier les résultats de requête en fonction des propriétés des documents JSON.  
  
 Dans cet exemple, la table AdventureWorks SalesOrderHeader comprend une colonne « Info » qui contient des informations de commande, par exemple des informations sur le client, le représentant commercial, les adresses de livraison/facturation, etc. Vous souhaitez utiliser les valeurs de la colonne Info pour filtrer les commandes pour un client particulier. Voici la requête que vous devez optimiser à l’aide d’un index.  
  
```tsql  
SELECT SalesOrderNumber,OrderDate,JSON_VALUE(Info,'$.Customer.Name') AS CustomerName
FROM Sales.SalesOrderHeader
WHERE JSON_VALUE(Info,'$.Customer.Name')=N'Aaron Campbell' 
```  
  
 Pour accélérer vos filtres ou les clauses ORDER BY sur une propriété d’un document JSON, vous pouvez utiliser les mêmes index que ceux que vous utilisez pour d’autres colonnes. Toutefois, vous ne pouvez pas directement référencer des propriétés dans les documents JSON. Vous devez d’abord créer une « colonne virtuelle » qui renvoie les valeurs que vous souhaitez utiliser pour le filtrage. Vous devez ensuite créer un index sur cette colonne virtuelle.  
  
 L’exemple suivant crée une colonne calculée qui peut être utilisée pour l’indexation, puis crée un index sur cette colonne. Cet exemple crée une colonne qui affiche le nom du client, celui-ci étant stocké dans le chemin d’accès $.Customer.Name des documents JSON.  
  
```tsql  
ALTER TABLE Sales.SalesOrderHeader
ADD vCustomerName AS JSON_VALUE(Info,'$.Customer.Name')

CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)  
```  
  
 La colonne calculée n’est pas persistante. Elle n’occupe pas d’espace supplémentaire dans la table. Elle est calculée uniquement lorsque l’index doit être recréé.  
  
 Il est important de créer la colonne calculée avec la même expression que celle que vous utilisez dans vos requêtes, à savoir pour cet exemple `JSON_VALUE(Info, '$.Customer.Name')`.  
  
 Vous n’avez pas besoin de réécrire vos requêtes. Si vous utilisez des expressions avec la fonction JSON_VALUE, SQL Server détecte qu’il existe une colonne calculée équivalente avec la même expression et applique un index si possible. Voici le plan d’exécution de la requête utilisée dans cet exemple.  
  
 ![Plan d’exécution](../../relational-databases/json/media/jsonindexblog1.png "Plan d’exécution")  
  
 Au lieu d’une analyse de table complète, SQL Server utilise une recherche d’index dans l’index non cluster et recherche les lignes qui répondent aux conditions spécifiées. Il utilise ensuite une recherche de clés dans la table SalesOrderHeader pour extraire d’autres colonnes référencées dans la requête, à savoir pour cet exemple SalesOrderNumber et OrderDate.  
  
 Vous pouvez éviter cette recherche supplémentaire dans la table en ajoutant les colonnes requises dans l’index JSON. Vous pouvez ajouter ces colonnes en tant que colonnes clés/non clés standard, comme illustré dans l’exemple suivant.  
  
```tsql  
CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)
INCLUDE(SalesOrderNumber,OrderDate)
```  
  
 Dans ce cas, SQL Server ne lit pas les données supplémentaires de la table SalesOrderHeader, car tout ce dont il a besoin est inclus dans l’index JSON non cluster. Il s’agit d’un bon moyen de combiner des données JSON et des données de colonnes dans les requêtes et de créer des index optimaux pour votre charge de travail.  
  
## <a name="json-indexes-are-collation-aware-indexes"></a>Les index JSON prennent en charge le classement  
 La prise en charge du classement est une fonctionnalité importante des index JSON. Le résultat de la fonction JSON_VALUE est une valeur de texte qui hérite son classement de l’expression d’entrée. Par conséquent, les valeurs de l’index sont triées à l’aide des règles de classement définies dans les colonnes sources.  
  
 À titre d’illustration, l’exemple suivant crée une table de collection simple avec une clé primaire et un contenu JSON.  
  
```tsql  
CREATE TABLE JsonCollection
 (
  id INT IDENTITY CONSTRAINT PK_JSON_ID PRIMARY KEY,
  json NVARCHAR(MAX) COLLATE SERBIAN_CYRILLIC_100_CI_AI
  CONSTRAINT [Content should be formatted as JSON]
  CHECK(ISJSON(json)>0)
 ) 
```  
  
 La commande précédente spécifie le classement serbe cyrillique pour la colonne JSON. L’exemple suivant remplit la table et crée un index sur la propriété de nom.  
  
```tsql  
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
  
 Les commandes précédentes créent un index standard sur la colonne calculée vName, qui représente la valeur de la propriété JSON $.name. Dans la page de codes cyrilliques serbes, l’ordre des lettres est « А », « Б », « В », « Г », « Д », « Ђ », « Е », etc. L’ordre des éléments de l’index est compatible avec les règles cyrilliques serbes, car le résultat de la fonction JSON_VALUE hérite son classement de la colonne source. L’exemple suivant interroge cette collection et trie les résultats par nom.  
  
```tsql  
SELECT JSON_VALUE(json,'$.name'),*
FROM JsonCollection
ORDER BY JSON_VALUE(json,'$.name')
```  
  
 Si vous examinez le plan d’exécution, vous pouvez constater qu’il utilise les valeurs triées de l’index non cluster.  
  
 ![Plan d’exécution](../../relational-databases/json/media/jsonindexblog2.png "Plan d’exécution")  
  
 Bien que la requête comporte une clause ORDER BY, le plan d’exécution n’utilise pas d’opérateur de tri. L’index JSON est déjà trié selon les règles cyrilliques serbes. Par conséquent, SQL Server peut utiliser l’index non cluster dans lequel les résultats sont déjà triés.  
  
 Toutefois, si nous modifions le classement de l’ordre par expression, par exemple en plaçant `COLLATE French_100_CI_AS_SC` après la fonction JSON_VALUE, nous obtenons un plan d’exécution de requête différent.  
  
 ![Plan d’exécution](../../relational-databases/json/media/jsonindexblog3.png "Plan d’exécution")  
  
 Étant donné que l’ordre des valeurs de l’index n’est pas compatible avec les règles de classement françaises, SQL Server ne peut pas utiliser l’index pour trier les résultats. Par conséquent, il ajoute un opérateur de tri qui trie les résultats à l’aide des règles de classement françaises.  
  
  

