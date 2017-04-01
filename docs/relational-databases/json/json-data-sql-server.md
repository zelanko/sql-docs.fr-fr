---
title: "Donn&#233;es JSON (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "JSON"
  - "JSON, prise en charge intégrée"
ms.assetid: c9a4e145-33c3-42b2-a510-79813e67806a
caps.latest.revision: 47
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 44
---
# Donn&#233;es JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  JSON est un format de données textuelles répandu qui est utilisé pour échanger des données dans des applications mobiles et web modernes. JSON est aussi utilisé pour stocker des données non structurées dans des fichiers journaux ou des bases de données NoSQL comme Microsoft Azure DocumentDB. Nombreux sont les services web REST qui retournent des résultats sous forme de texte JSON ou qui acceptent des données au format JSON. La plupart des services Azure, tels que Azure Search, Azure Storage et Azure DocumentDb, ont des points de terminaison REST qui retournent ou utilisent des données JSON. JSON est aussi le principal format d’échange de données entre les pages web et les serveurs web utilisant des appels AJAX.  
  
 Voici un exemple de texte JSON :  
  
```json  
[   
   { "name": "John", "skills":["SQL","C#","Azure"] },  
   { "name": "Jane", "surname": "Doe" }  
]  
```  
  
 SQL Server intègre des fonctions et des opérateurs qui vous permettent d’effectuer les opérations suivantes :  
  
-   analyser du texte JSON et lire ou modifier des valeurs ;  
  
-   transformer des tableaux d’objets JSON au format table ;  
  
-   utiliser une requête Transact SQL sur les objets JSON convertis ;  
  
-   mettre en forme les résultats des requêtes Transact-SQL au format JSON.  
  
 ![Overview of built-in JSON support](../../relational-databases/json/media/jsonslides1overview.png "Overview of built-in JSON support")  
  
 Voici les principales fonctionnalités offertes par SQL Server.  
  
 **Extraire les valeurs de texte JSON et les utiliser dans les requêtes.** Si vous avez stocké du texte JSON dans des tables de base de données, vous pouvez utiliser les fonctions intégrées pour lire ou modifier les valeurs présentes dans le texte JSON.  
  
-   la fonction **JSON_VALUE** permet d’extraire une valeur scalaire d’une chaîne JSON ;  
  
-   la fonction **JSON_QUERY** permet d’extraire un objet ou un tableau ;  
  
-   la fonction **ISJSON** permet de déterminer si une chaîne contient des données JSON valides.  
  
 Dans l’exemple suivant, la requête utilise à la fois les données relationnelles et les données JSON (stockées dans la colonne jsonCol) d’une table :  
  
```tsql  
  
SELECT Name, Surname,     
    JSON_VALUE(jsonCol, '$.info.address.PostCode') as PostCode,  
    JSON_VALUE(jsonCol, '$.info.address."Address Line 1"') +  ' ' + JSON_VALUE(jsonCol, '$.info.address."Address Line 2"') AS Address,  
    JSON_QUERY(jsonCol, '$.info.skills') as Skills  
FROM PeopleCollection  
WHERE ISJSON(jsonCol) > 0   
  AND JSON_VALUE(jsonCol, '$.info.address.town') = 'Belgrade'  
  AND Status = 'Active'  
ORDER BY JSON_VALUE(@jsonInfo, '$.info.address.PostCode')  
  
```  
  
 Les applications et les outils ne font aucune différence entre les valeurs tirées de colonnes de table scalaire et les valeurs tirées de colonnes JSON. Vous pouvez utiliser des valeurs de texte JSON dans n’importe quelle partie de requête Transact-SQL (notamment les clauses WHERE, ORDER BY, GROUP BY, les agrégats de fenêtre, etc.). Les fonctions JSON utilisent une syntaxe de type JavaScript pour faire référence aux valeurs contenues dans du texte JSON. Pour plus d’informations, consultez [Validate, Query, and Change JSON Data with Built-in Functions &#40;SQL Server&#41;](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md) (Valider, interroger et modifier les données JSON à l’aide des fonctions intégrées &#40;SQL Server&#41;) [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md) et [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  
  
 **Modifier les valeurs JSON.** Si vous avez besoin de modifier des parties de texte JSON, vous pouvez utiliser la fonction **JSON_MODIFY** pour mettre à jour une valeur de propriété de chaîne JSON et retourner la chaîne JSON mise à jour. L’exemple suivant met à jour la valeur d’une propriété dans une variable contenant du texte JSON.  
  
```tsql  
SET @jsonInfo = JSON_MODIFY(@jsonInfo, '$.info.address[0].town', 'London')  
```  
  
 **Convertir des collections JSON en ensemble de lignes.** Vous n’avez pas besoin d’un langage de requête personnalisé pour interroger les données JSON dans SQL Server. Pour interroger des données JSON, vous pouvez utiliser le langage T-SQL standard. Si vous devez créer une requête ou un rapport sur des données JSON, vous pouvez facilement convertir les données JSON en lignes et colonnes en appelant la fonction d’ensemble de lignes **OPENJSON**. La fonction **OPENJSON** permet d’importer des données JSON dans SQL Server ou de convertir des données JSON en lignes et colonnes. Pour plus d’informations, consultez [Convert JSON Data to Rows and Columns with OPENJSON &#40;SQL Server&#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md) (Convertir des données JSON en lignes et colonnes avec OPENJSON &#40;SQL Server&#41;).  
  
 L’exemple suivant appelle **OPENJSON** , qui transforme le tableau d’objets stocké dans la variable **@json** en ensemble de lignes qui peut être interrogé à l’aide de l’instruction SQL SELECT standard :  
  
```tsql  
SET @json =  
N'[  
      { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },  
      { "id" : 5,"info": { "name": "Jane", "surname": "Smith" }, "dob": "2005-11-04T12:00:00" }  
]'  
  
SELECT *  
FROM OPENJSON(@json)  
 WITH (id int 'strict $.id',  
       firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',  
       age int, dateOfBirth datetime2 '$.dob')  
  
```  
  
 **Résultats**  
  
|id|firstName|lastName|age|dateOfBirth|  
|--------|---------------|--------------|---------|-----------------|  
|2|John|Smith|25||  
|5|Jane|Smith||2005-11-04T12:00:00|  
  
 **OPENJSON** transforme le tableau d’objets JSON en table, dans laquelle chaque objet est représenté par une ligne, et des paires clé-valeur sont retournées sous forme de cellules. **OPENJSON** convertit les valeurs JSON en types spécifiés. **OPENJSON** peut gérer à la fois les paires clé-valeur plates et les objets imbriqués organisés en hiérarchie. Vous n’êtes pas obligé de retourner tous les champs contenus dans le texte JSON. **OPENJSON** retourne des valeurs NULL s’il n’existe pas de valeurs JSON. Vous pouvez éventuellement spécifier un chemin après la spécification du type pour faire référence à une propriété imbriquée ou à une propriété avec un autre nom. Le préfixe facultatif **strict** figurant dans le chemin indique que des valeurs doivent exister dans le texte JSON pour les propriétés spécifiées. Pour plus d’informations, consultez [Convert JSON Data to Rows and Columns with OPENJSON &#40;SQL Server&#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md) (Convertir des données JSON en lignes et colonnes avec OPENJSON &#40;SQL Server&#41;) et [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
 **Convertir des données SQL Server au format JSON ou exporter des données JSON.** Mettez les données SQL Server ou les résultats des requêtes au format JSON en ajoutant la clause **FOR JSON** à une instruction **SELECT** . Utilisez FOR JSON pour déléguer la mise en forme de la sortie JSON produite par vos applications clientes à SQL Server. Pour plus d’informations, consultez [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
 L’exemple suivant utilise le mode PATH avec la clause FOR JSON.  
  
```tsql  
SELECT id, firstName AS "info.name", lastName AS "info.surname", age, dateOfBirth as dob  
FROM People  
FOR JSON PATH  
```  
  
 La   
clause     **FOR JSON** met les résultats SQL sous forme de texte JSON qui peut être fourni à n’importe quelle application capable de comprendre JSON. L’option PATH utilise des alias séparés par des points dans la clause SELECT pour imbriquer des objets dans les résultats de requête.  
  
 **Résultats**  
  
```json  
[  
      { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },  
      { "id" : 5,"info": { "name": "Jane", "surname": "Smith" }, "dob": "2005-11-04T12:00:00" }  
]  
```  
  
 Pour plus d’informations, consultez [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md) et [Clause FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md).  
  
## Cas d’utilisation  
 SQL Server met à disposition un modèle hybride pour stocker et traiter les données relationnelles et JSON en utilisant le langage Transact-SQL standard. Il vous permet d’organiser des regroupements de vos documents JSON par tables, d’établir des relations entre eux, de combiner des colonnes scalaires fortement typées stockées dans des tables contenant des paires clé-valeur flexibles dans des colonnes JSON et d’interroger les valeurs scalaires et JSON dans une ou plusieurs tables en utilisant la syntaxe Transact-SQL complète. Le texte JSON est généralement stocké dans des colonnes varchar ou nvarchar et est indexé sous forme de texte brut. Sachant qu’une fonctionnalité ou un composant SQL Server qui prend en charge le texte prend aussi en charge JSON, il n’y a quasiment aucune contrainte dans l’interaction entre JSON et les autres fonctionnalités SQL Server. Vous pouvez stocker du texte JSON dans des tables en mémoire ou temporelles, vous pouvez appliquer des prédicats de sécurité au niveau des lignes sur du texte JSON, et ainsi de suite. Si vous avez des charges de travail JSON pures dans lesquelles vous voulez utiliser un langage de requête personnalisé pour le traitement des documents JSON, songez à Microsoft Azure [DocumentDB](https://azure.microsoft.com/services/documentdb/).  
  
 Voici quelques cas d’utilisation qui vous montrent comment utiliser la prise en charge JSON intégrée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Retourner les données d’une table SQL Server au format JSON  
 Si vous avez un service web qui tire des données de la couche Base de données et les retourne au format JSON ou que vous disposez d’infrastructures ou de bibliothèques JavaScript qui acceptent des données au format JSON, vous pouvez mettre en forme les résultats directement dans une requête SQL. Au lieu d’écrire du code ou d’inclure une bibliothèque pour convertir des résultats de requêtes tabulaires et sérialiser ensuite des objets au format JSON, vous pouvez utiliser FOR JSON pour déléguer la mise en forme des données JSON à SQL Server.  
  
 Par exemple, vous pouvez générer une sortie JSON conforme à la spécification OData. Le service web attend une demande et une réponse dans le format suivant.  
  
-   Demande : `/Northwind/Northwind.svc/Products(1)?$select=ProductID,ProductName`  
  
-   Réponse : `{"@odata.context":"http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity","ProductID":1,"ProductName":"Chai"}`  
  
 Cette URL OData représente une demande pour les colonnes ProductID et ProductName pour le produit associé à l’ID 1. Vous pouvez utiliser FOR JSON pour mettre en forme la sortie comme prévu dans SQL Server.  
  
```tsql  
SELECT 'http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity' AS '@odata.context',   
ProductID, Name as ProductName   
FROM Production.Product  
WHERE ProductID = 1  
FOR JSON AUTO  
  
```  
  
 Le résultat de cette requête est un texte JSON entièrement conforme à la spécification OData. La mise en forme et l’échappement sont gérés par SQL Server. SQL Server peut mettre en forme les résultats de requêtes dans n’importe quel format, notamment OData JSON ou GeoJSON - consultez [Returning spatial data in GeoJSON format](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/returning-spatial-data-in-geojson-format-part-1) (Retourner des données spatiales au format GeoJSON).  
  
## Analyser des données JSON à l’aide de requêtes SQL  
 Si vous devez filtrer ou agréger des données JSON pour générer des rapports, vous pouvez utiliser OPENJSON pour transformer les données JSON au format relationnel. Utilisez ensuite le langage et les fonctions intégrées [!INCLUDE[tsql](../../includes/tsql-md.md)] standard pour préparer les rapports.  
  
```tsql  
SELECT Tab.Id, SalesOrderJsonData.Customer, SalesOrderJsonData.Date  
FROM   SalesOrderRecord AS Tab  
         CROSS APPLY  
    OPENJSON (Tab.json, N'$.Orders.OrdersArray')  
          WITH (  
             Number   varchar(200) N'$.Order.Number',   
             Date     datetime     N'$.Order.Date',  
             Customer varchar(200) N'$.AccountNumber',   
             Quantity int          N'$.Item.Quantity'  
          )  
 AS SalesOrderJsonData  
WHERE JSON_VALUE(Tab.json, '$.Status') = N'Closed'  
ORDER BY JSON_VALUE(Tab.json, '$.Group'), Tab.DateModified  
  
```  
  
 Vous pouvez utiliser des colonnes de table standard et des valeurs de texte JSON dans une même requête. Vous pouvez ajouter des index dans l’expression JSON_VALUE (Tab.json,'$.Status') pour améliorer les performances des requêtes.  
  
## Importer des données JSON dans des tables SQL Server  
 Si vous devez charger des données JSON dans SQL Server à partir d’un service externe, vous pouvez utiliser OPENJSON pour importer les données dans SQL Server au lieu d’analyser les données dans la couche application.  
  
```tsql  
INSERT INTO SalesReport  
SELECT SalesOrderJsonData.*  
FROM OPENJSON (@jsonVariable, N'$.Orders.OrdersArray')  
          WITH (  
             Number   varchar(200) N'$.Order.Number',   
             Date     datetime     N'$.Order.Date',  
             Customer varchar(200) N'$.AccountNumber',   
             Quantity int          N'$.Item.Quantity'  
          )  
 AS SalesOrderJsonData;  
  
```  
  
 Le contenu de la variable JSON peut être fourni par un service REST externe, envoyé en tant que paramètre à partir d’une infrastructure JavaScript côté client ou chargé à partir de fichiers externes. Vous pouvez facilement insérer, mettre à jour ou fusionner les résultats du texte JSON dans une table SQL Server. Pour plus d’informations sur ce scénario, consultez [Importing JSON data in SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/09/22/openjson-the-easiest-way-to-import-json-text-into-table/)(Importation de données JSON dans SQL Server), [Upsert JSON documents in SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/03/upsert-json-documents-in-sql-server-2016)(Upsert de documents JSON dans SQL Server 2016) et [Loading GeoJSON data into SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/)(Chargement de données GeoJSON dans SQL Server 2016).  
  
## Chargement de fichiers JSON dans SQL Server  
 Les informations stockées dans les fichiers peuvent être mises au format JSON standard ou JSON délimité par des lignes. SQL Server peut importer le contenu de fichiers JSON, l’analyser à l’aide des fonctions OPENJSON ou JSON_VALUE, puis le charger dans des tables.  
  
 Si vos fichiers JSON sont stockés dans des fichiers locaux, des lecteurs réseau partagés ou à un emplacement de stockage de fichiers Azure File auxquels SQL Server a accès, vous pouvez recourir à l’importation en bloc pour charger vos données JSON dans SQL Server. Pour plus d’informations sur ce scénario, consultez [Importing JSON files into SQL Server using OPENROWSET (BULK)](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2015/10/07/importing-json-files-into-sql-server-using-openrowset-bulk.aspx) [Importation de fichiers JSON dans SQL Server à l’aide de OPENROWSET (BULK)].  
  
 Si vos fichiers au format JSON délimité par des lignes sont stockés dans Azure Blob Storage ou le système de fichiers Hadoop, vous pouvez utiliser Polybase pour charger le texte JSON, l’analyser dans du code Transact-SQL et le charger dans des tables.  
  
## Tester la prise en charge de JSON intégrée  
 **Tester la prise en charge de JSON à partir de l’exemple de base de données AdventureWorks.** Pour obtenir l’exemple de base de données AdventureWorks, téléchargez au minimum le fichier de base de données et le fichier d’exemples et de scripts [ici](https://www.microsoft.com/en-us/download/details.aspx?id=49502). Après avoir restauré l’exemple de base de données dans une instance de SQL Server 2016, décompressez le fichier d’exemples et ouvrez le fichier « JSON Sample Queries procedures views and indexes.sql » à partir du dossier JSON. Exécutez les scripts de ce fichier pour remettre certaines données existantes au format JSON, exécutez des exemples de rapports et de requêtes sur les données JSON, indexez les données JSON, puis importez et exportez les données JSON.  
  
 Voici ce que vous pouvez faire avec les scripts inclus dans le fichier.  
  
1.  Dénormaliser le schéma existant pour créer des colonnes de données JSON.  
  
    1.  Stockez les informations de SalesReasons, SalesOrderDetails, SalesPerson, Customer et des autres tables contenant des informations relatives aux commandes dans les colonnes JSON de la table SalesOrder_json.  
  
    2.  Stockez les informations des tables EmailAddresses/PersonPhone dans la table Person_json en tant que tableaux d’objets JSON.  
  
2.  Créer des procédures et des vues qui interrogent les données JSON.  
  
3.  Indexer les données JSON : créez des index sur les propriétés JSON et des index de recherche en texte intégral.  
  
4.  Importer et exporter les données JSON : créez et exécutez des procédures qui exportent le contenu des tables Person et SalesOrder sous forme de résultats JSON, puis importez et mettez à jour les tables Person et SalesOrder à l’aide de l’entrée JSON.  
  
5.  Exécuter des exemples de requêtes : exécutez des requêtes qui appellent les procédures stockées et les vues créées aux étapes 2 et 4.  
  
6.  Nettoyer les scripts : n’exécutez pas cette partie si vous voulez conserver les procédures stockées et les vues créées aux étapes 2 et 4.  
  
## En savoir plus sur la prise en charge JSON intégrée  
  
### Rubriques de cette section  
 [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
 Utilisez la clause FOR JSON pour déléguer la mise en forme de la sortie JSON produite par vos applications clientes à SQL Server.  
  
 [Convert JSON Data to Rows and Columns with OPENJSON &#40;SQL Server&#41; [Convertir des données JSON en lignes et colonnes avec OPENJSON &#40;SQL Server&#41;]](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)  
 Utilisez OPENJSON pour importer des données JSON dans SQL Server ou pour convertir des données JSON dans un format relationnel pour une application ou un service qui ne peut actuellement pas utiliser directement les données JSON, comme notamment SQL Server Integration Services.  
  
 [Validate, Query, and Change JSON Data with Built-in Functions &#40;SQL Server&#41; [Valider, interroger et modifier les données JSON avec les fonctions intégrées &#40;SQL Server&#41;]](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md)  
 Utilisez ces fonctions intégrées pour valider du texte JSON et extraire une valeur scalaire, un objet ou un tableau.  
  
 [JSON Path Expressions &#40;SQL Server&#41; [Expressions de chemin JSON &#40;SQL Server&#41;]](../../relational-databases/json/json-path-expressions-sql-server.md)  
 Utilisez une expression de chemin pour spécifier le texte JSON que vous voulez utiliser.  
  
 [Indexer des données JSON](../../relational-databases/json/index-json-data.md)  
 Utilisez des colonnes calculées pour créer des index qui prennent en charge le classement sur les propriétés des documents JSON.  
  
 [Forum Aux Questions concernant JSON dans SQL Server](../Topic/Frequently%20Asked%20Questions%20about%20JSON%20in%20SQL%20Server.md)  
 Trouvez des réponses aux questions courantes sur la prise en charge JSON intégrée à SQL Server.  
  
### Billets de blog Microsoft  
  
-   [Billets de blog de Jovan Popovic, gestionnaire de programmes Microsoft](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
### Rubriques d’informations de référence  
  
-   [Clause FOR &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md) (FOR JSON)  
  
-   [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
-   [Fonctions JSON &#40;Transact-SQL&#41;](../../t-sql/functions/json-functions-transact-sql.md)  
  
    -   [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)  
  
    -   [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)  
  
    -   [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)  
  
    -   [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)  
  
  