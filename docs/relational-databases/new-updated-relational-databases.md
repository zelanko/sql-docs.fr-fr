---
title: "Mise à jour - Documentation des bases de données relationnelles | Microsoft Docs"
description: "Affichage d’extraits de contenu mis à jour de la documentation récemment modifiée des bases de données relationnelles."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: relational-databases
ms.date: 02/03/2018
ms.openlocfilehash: 38f9ee55137c54adddb07fbe9f3b74dd43d51a3a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Contenu nouveau et récemment mis à jour : documentation des bases de données relationnelles



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **03-12-2017** &nbsp; au &nbsp; **03-02-2018**
- *Domaine :* &nbsp; **bases de données relationnelles**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Stocker des documents JSON dans SQL Server ou SQL Database](json/store-json-documents-in-sql-tables.md)
2. [Évaluation des vulnérabilités SQL](security/sql-vulnerability-assessment.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Initialisation des fichiers de base de données](#TitleNum_1)
2. [Base de données tempdb](#TitleNum_2)
3. [Données JSON dans SQL Server](#TitleNum_3)
4. [Leçon 1 : connexion au moteur de base de données](#TitleNum_4)
5. [Gérer la taille du fichier journal des transactions](#TitleNum_5)
6. [bcp_bind](#TitleNum_6)
7. [Guide de conception d’index SQL Server](#TitleNum_7)
8. [sp_execute_external_script (Transact-SQL)](#TitleNum_8)
9. [Créer des clés primaires](#TitleNum_9)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-database-file-initializationdatabasesdatabase-instant-file-initializationmd"></a>1. &nbsp; [Initialisation des fichiers de base de données](databases/database-instant-file-initialization.md)

*Mise à jour : 23-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Suivant](#TitleNum_2))

<!-- Source markdown line 81.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c5f2aa53a8b43d4c43e0602cf945cb7c7028a27d 04c261c6588af1f53cda2fce3e9a86167c50b686  (PR=4702  ,  Filename=database-instant-file-initialization.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=3206a31870f8febab7d1718fa59fe0590d4d45db) -->



```
Database Instant File Initialization: disabled. For security and performance considerations see the topic 'Database Instant File Initialization' in SQL Server Books Online. This is an informational message only. No user action is required.
```

**S’applique à :** SQL Server (de SQL Server 2012 SP4, SQL Server 2014 SP2 et SQL Server 2016 jusqu’à SQL Server 2017)

**Considérations relatives à la sécurité**

Quand vous utilisez l’initialisation instantanée de fichiers (IFI), comme le contenu du disque supprimé n’est remplacé qu’au moment où de nouvelles données sont écrites dans les fichiers, il est éventuellement accessible à un principal non autorisé jusqu’à ce que d’autres données soient écrites sur cette zone spécifique du fichier de données. Même si le fichier de base de données est attaché à l’instance de SQL Server, le risque de divulgation de ces informations est limité par la liste de contrôle d’accès discrétionnaire (DACL, Discretionary Access Control List) du fichier. Cette liste DACL n’autorise l’accès au fichier qu’à l’administrateur local et au compte de service SQL Server. Cependant, quand le fichier est détaché, un utilisateur ou un service ne bénéficiant pas de l’autorisation SE\_MANAGE\_VOLUME_NAME peut y accéder. Cette situation se présente aussi quand la base de données est sauvegardée : si le fichier de sauvegarde n’est pas protégé par une liste DACL appropriée, le contenu supprimé peut devenir accessible à un utilisateur ou à un service non autorisé.

Une autre considération est que quand la taille est augmentée avec IFI, un administrateur SQL Server peut potentiellement accéder au contenu de la page brute et voir le contenu précédemment supprimé.

Si les fichiers de base de données sont hébergés sur un réseau de zone de stockage, il est également possible que le réseau de zone de stockage présente toujours les nouvelles pages préinitialisées. Or, laisser le système d’exploitation réinitialiser les pages peut représenter une charge supplémentaire non nécessaire.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-tempdb-databasedatabasestempdb-databasemd"></a>2. &nbsp; [Base de données tempdb](databases/tempdb-database.md)

*Mise à jour : 17-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_1) | [Suivant](#TitleNum_3))

<!-- Source markdown line 100.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 337555ea28f4c3fdd6b78f1bfb4d62607a6bf92d 3257c92d6e2a88968fc44e5f6262c02cd0624635  (PR=0  ,  Filename=tempdb-database.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=45e6082acc29ba306525e7c08d2c22cc2b86eec3) -->



 Pour obtenir une description de ces options de base de données, consultez [Options ALTER DATABASE SET (Transact-SQL)](databases/../../t-sql/statements/alter-database-transact-sql-set-options.md).

**Base de données tempdb dans SQL Database**


|SLO|Taille maximale du fichier de données tempdb (Mo)|Nombre de fichiers de données tempdb|Taille maximale des données tempdb (Mo)|
|---|---:|---:|---:|
|Simple|14,225| 1|14,225|
|S0|14,225| 1|14,225|
|S1|14,225| 1|14,225|
|S2|14,225|  1|14,225|
|S3|32,768| 1|32,768|
|S4|32,768|2|65,536|
|S6|32,768|3|98,304|
|S7|32,768|6|196,608|
|S9|32,768|12|393,216|
|S12|32,768|12|393,216|
|P1|32,768|12|393,216|
|P2|32,768|12|393,216|
|P4|32,768|12|393,216|
|P6|32,768|12|393,216|
|P11|32,768|12|393,216|
|P15|32,768|12|393,216|
|Pools élastiques Premium (toutes les configurations de DTU)|14,225|12|170,700|
|Pools élastiques Standard (toutes les configurations de DTU)|14,225|12|170,700|
|Pools élastiques De base (toutes les configurations de DTU)|14,225|12|170,700|
||||




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-json-data-in-sql-serverjsonjson-data-sql-servermd"></a>3. &nbsp; [Données JSON dans SQL Server](json/json-data-sql-server.md)

*Mise à jour : 01-02-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_2) | [Suivant](#TitleNum_4))

<!-- Source markdown line 233.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 62dd9c68d8cb72d6bf51b941a0731224514f0a7f 19e276637a463b412f2c29a84f9fb7d0b0f5fcc5  (PR=4783  ,  Filename=json-data-sql-server.md  ,  Dirpath=docs\relational-databases\json\  ,  MergeCommitSha40=73f18ae24a9a48234bf997ee9a2ef441bc4918b9) -->



-   [Load GeoJSON data into SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/) (Charger des données GeoJSON dans SQL Server 2016)

**Analyser des données JSON à l’aide de requêtes SQL**

Si vous devez filtrer ou agréger des données JSON pour générer des rapports, vous pouvez utiliser **OPENJSON** pour transformer les données JSON au format relationnel. Vous pouvez ensuite utiliser le langage et les fonctions intégrées Transact-SQL standard pour préparer les rapports.

```
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



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-lesson-1-connecting-to-the-database-enginelesson-1-connecting-to-the-database-enginemd"></a>4. &nbsp; [Leçon 1 : Connexion au moteur de base de données](lesson-1-connecting-to-the-database-engine.md)

*Mise à jour : 13-12-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_3) | [Suivant](#TitleNum_5))

<!-- Source markdown line 79.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3c070935895450fd2ea054e2be9e1c48f7dc2b6c 0c386e3d47fb7f8f1e63b9301f0cafec2bc88ab0  (PR=4282  ,  Filename=lesson-1-connecting-to-the-database-engine.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=6e016a4ffd28b09456008f40ff88aef3d911c7ba) -->



2.  Sélectionnez **Moteur de base de données**.

    ![object-explorer](../relational-databases/media/object-explorer.png)

3.  Dans la zone **Nom du serveur**, tapez le nom de l’instance du moteur de base de données. Pour l'instance par défaut de SQL Server, le nom du serveur est celui de l'ordinateur. Pour une instance nommée de SQL Server, le nom du serveur est *<nom_ordinateur>***\\***<nom_instance>,* par exemple **ACCTG_SRVR\SQLEXPRESS**. La capture d’écran suivante montre la connexion à l’instance par défaut (non nommée) de SQL Server sur un ordinateur nommé « PracticeComputer ». L’utilisateur connecté à Windows est Mary du domaine Contoso. Quand vous utilisez l’authentification Windows, vous ne pouvez pas modifier le nom d’utilisateur.

    ![connect-to-server](../relational-databases/media/connect-to-server.png)

4.  Cliquez sur **Se connecter**.

> [!NOTE]
> Ce didacticiel part du principe que vous ne connaissez pas SQL Server et que vous n’avez pas de problème de connexion particulier. Ainsi, il peut convenir au plus grand nombre et garde toute sa simplicité. Pour connaître les étapes de dépannage détaillées, consultez [Résoudre les problèmes de connexion au moteur de base de données SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

**<a name="additional"></a>Autorisation de connexions supplémentaires**

Maintenant que vous êtes connecté à SQL Server en tant qu’administrateur, l’une de vos premières tâches consiste à autoriser d’autres utilisateurs à se connecter. Pour cela, vous pouvez créer une connexion et l'autoriser à accéder à une base de données en tant qu'utilisateur. Les connexions peuvent désigner des connexions d’authentification Windows qui exploitent les informations d’identification Windows, ou bien des connexions d’authentification SQL Server qui stockent les données d’authentification dans SQL Server et qui n’ont aucun lien avec vos informations d’identification Windows. Utilisez l'authentification Windows chaque fois que cela est possible.



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-manage-the-size-of-the-transaction-log-filelogsmanage-the-size-of-the-transaction-log-filemd"></a>5. &nbsp; [Gérer la taille du fichier journal des transactions](logs/manage-the-size-of-the-transaction-log-file.md)

*Mise à jour : 17-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_4) | [Suivant](#TitleNum_6))

<!-- Source markdown line 105.  ms.author= "jhubbard".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5847b31cf8f6003a380f0c8aaa289efdc55be678 84e45320d81db218cde17fbf8b9668a9ac3805a7  (PR=0  ,  Filename=manage-the-size-of-the-transaction-log-file.md  ,  Dirpath=docs\relational-databases\logs\  ,  MergeCommitSha40=45e6082acc29ba306525e7c08d2c22cc2b86eec3) -->



-   Un incrément de croissance réduit peut générer un nombre excessif de petits [fichiers journaux virtuels](logs/../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) et réduire le niveau de performance. Pour déterminer la distribution optimale des fichiers journaux virtuels pour la taille actuelle du journal des transactions de toutes les bases de données dans une instance donnée, ainsi que les incréments de croissance pour atteindre la taille nécessaire, consultez ce [script](http://github.com/Microsoft/tigertoolbox/tree/master/Fixing-VLFs).

-   Un incrément de croissance élevé peut générer un nombre insuffisants de [fichiers journaux virtuels](logs/../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) volumineux et affecter également le niveau de performance. Pour déterminer la distribution optimale des fichiers journaux virtuels pour la taille actuelle du journal des transactions de toutes les bases de données dans une instance donnée, ainsi que les incréments de croissance pour atteindre la taille nécessaire, consultez ce [script](http://github.com/Microsoft/tigertoolbox/tree/master/Fixing-VLFs).

-   Même si la croissance automatique est activée, vous pouvez recevoir un message indiquant que le journal des transactions est complet, s’il ne peut pas croître suffisamment rapidement pour répondre aux besoins de votre requête. Pour plus d’informations sur le changement de l’incrément de croissance, consultez [Options de fichiers et de groupes de fichiers &#40;Transact-SQL&#41; ALTER DATABASE](logs/../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).

-   Avoir plusieurs fichiers journaux dans une base de données n’améliore pas du tout le niveau de performance, car les fichiers journaux de transactions n’utilisent pas le [remplissage proportionnel](logs/../../relational-databases/pages-and-extents-architecture-guide.md#ProportionalFill) comme les fichiers de données dans un même groupe de fichiers.

-   Les fichiers journaux peuvent être définis de manière à se réduire automatiquement. Toutefois, cette configuration étant **déconseillée**, la propriété de base de données **auto_shrink** est définie sur FALSE par défaut. Si **auto_shrink** est définie sur la valeur TRUE, la troncation automatique réduit la taille d’un fichier uniquement quand plus de 25 pour cent de son espace est inutilisé.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-bcpbindnative-client-odbc-extensions-bulk-copy-functionsbcp-bindmd"></a>6. &nbsp; [bcp_bind](native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)

*Mise à jour : 30-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_5) | [Suivant](#TitleNum_7))

<!-- Source markdown line 127.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d50791cef948ce8b3066438e317ab4d34d535258 e6f70559e7237cfc86dfc5746d218c08bec52af6  (PR=4762  ,  Filename=bcp-bind.md  ,  Dirpath=docs\relational-databases\native-client-odbc-extensions-bulk-copy-functions\  ,  MergeCommitSha40=60006e90d03fdb75b282bbc0dad3d40571bacacc) -->



 Le tableau suivant répertorie les types de données énumérées valides et les types de données ODBC C correspondants.

|eDataType|Type C|
|-----------------------|------------|
|SQLTEXT|char *|
|SQLNTEXT|wchar_t *|
|SQLCHARACTER|char *|
|SQLBIGCHAR|char *|
|SQLVARCHAR|char *|
|SQLBIGVARCHAR|char *|
|SQLNCHAR|wchar_t *|
|SQLNVARCHAR|wchar_t *|
|SQLBINARY|unsigned char *|
|SQLBIGBINARY|unsigned char *|
|SQLVARBINARY|unsigned char *|
|SQLBIGVARBINARY|unsigned char *|
|SQLBIT|char|
|SQLBITN|char|
|SQLINT1|char|
|SQLINT2|short int|
|SQLINT4|INT|
|SQLINT8|_int64|
|SQLINTN|*cbIndicator*<br /> 1: SQLINT1<br /> 2: SQLINT2<br /> 4: SQLINT4<br /> 8: SQLINT8|
|SQLFLT4|FLOAT|
|SQLFLT8|FLOAT|
|SQLFLTN|*cbIndicator*<br /> 4: SQLFLT4<br /> 8: SQLFLT8|
|SQLDECIMALN|SQL_NUMERIC_STRUCT|
|SQLNUMERICN|SQL_NUMERIC_STRUCT|
|SQLMONEY|DBMONEY|
|SQLMONEY4|DBMONEY4|
|SQLMONEYN|*cbIndicator*<br /> 4: SQLMONEY4<br /> 8: SQLMONEY|
|SQLTIMEN|SQL_SS_TIME2_STRUCT|
|SQLDATEN|SQL_DATE_STRUCT|
|SQLDATETIM4|DBDATETIM4|
|SQLDATETIME|DBDATETIME|
|SQLDATETIMN|*cbIndicator*<br /> 4: SQLDATETIM4<br /> 8: SQLDATETIME|
|SQLDATETIME2N|SQL_TIMESTAMP_STRUCT|
|SQLDATETIMEOFFSETN|SQL_SS_TIMESTAMPOFFSET_STRUCT|
|SQLIMAGE|unsigned char *|
|SQLUDT|unsigned char *|
|SQLUNIQUEID|SQLGUID|
|SQLVARIANT|*Tout type de données sauf :*<br />-   text<br />-   ntext<br />-   image<br />-   varchar(max)<br />-   varbinary(max)<br />-   nvarchar(max)<br />-   xml<br />-   timestamp|
|SQLXML|*Types de données C pris en charge :*<br />-   char*<br />-   wchar_t *<br />-   unsigned char *|



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-sql-server-index-design-guidesql-server-index-design-guidemd"></a>7. &nbsp; [Guide de conception d’index SQL Server](sql-server-index-design-guide.md)

*Mise à jour : 02-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_6) | [Suivant](#TitleNum_8))

<!-- Source markdown line 700.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bd09c9e66cd3cf5f3ebebe7ffa6e937978353169 8e5cbbf0063971676a8bafefba75aa5c7c28be61  (PR=0  ,  Filename=sql-server-index-design-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=74daee358fef75a25d75c69d971d08536c5bd2be) -->



À compter de SQL Server 2016, vous pouvez créer un **index columnstore non-cluster pouvant être mis à jour sur une table rowstore**. L’index columnstore stocke une copie des données, afin que vous n’ayez pas besoin de stockage supplémentaire. Toutefois, les données de l’index columnstore sont compressées à une taille plus petite que ce que nécessite la table rowstore.  Ce faisant, vous pouvez exécuter l’analytique sur l’index columnstore et les transactions sur l’index rowstore en même temps. La banque des colonnes (columnstore) est mise à jour lors de la modification des données de la table rowstore. Les deux index utilisent donc les mêmes données.

À compter de SQL Server 2016, vous pouvez avoir **un ou plusieurs index rowstore non-cluster sur un index columnstore**. Ce faisant, vous pouvez effectuer des recherches de tables efficaces sur le columnstore sous-jacent. D’autres options sont également disponibles. Par exemple, vous pouvez appliquer une contrainte de clé primaire à l’aide d’une contrainte UNIQUE sur la table rowstore. Dans la mesure où une valeur non unique ne peut pas être insérée dans la table rowstore, SQL Server ne peut pas insérer la valeur dans le columnstore.

**Considérations relatives aux performances**


-   La définition d’index columnstore non cluster prend en charge l’utilisation d’une condition filtrée. Pour minimiser l’impact sur les performances de l’ajout d’un index columnstore sur une table OLTP, utilisez une condition filtrée pour créer un index columnstore non cluster uniquement sur les données brutes de votre charge de travail opérationnelle.

-   Une table en mémoire peut avoir un index columnstore. Vous pouvez le créer lors de la création de la table ou l’ajouter ultérieurement avec [ALTER TABLE &#40;Transact-SQL&#41;](../t-sql/statements/alter-table-transact-sql.md). Avant SQL Server 2016, seule une table sur disque pouvait avoir un index columnstore.

Pour plus d’informations, consultez [Index columnstore - Performances des requêtes](../relational-databases/indexes/columnstore-indexes-query-performance.md).

**Conseils pour la conception**


-   Une table rowstore peut avoir un index columnstore non cluster actualisable. Avant SQL Server 2014, les index columnstore non-cluster étaient en lecture seule.



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-spexecuteexternalscript-transact-sqlsystem-stored-proceduressp-execute-external-script-transact-sqlmd"></a>8. &nbsp; [sp_execute_external_script (Transact-SQL)](system-stored-procedures/sp-execute-external-script-transact-sql.md)

*Mise à jour : 23-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_7) | [Suivant](#TitleNum_9))

<!-- Source markdown line 207.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0ee4d591ae9d9a5c015eec98aad9ccbb86268761 ac9b439c23ffae5fcc77639de6ff955763cf5844  (PR=4696  ,  Filename=sp-execute-external-script-transact-sql.md  ,  Dirpath=docs\relational-databases\system-stored-procedures\  ,  MergeCommitSha40=d7dcbcebbf416298f838a39dd5de6a46ca9f77aa) -->



Pour générer un modèle semblable à l’aide de Python, vous devez remplacer l’identificateur de langage `@language=N'R'` par `@language = N'Python'` et apporter les modifications nécessaires à l’argument `@script`. Autrement, tous les paramètres fonctionnent de la même manière que pour R.

**C. Créer un modèle Python et générer des scores à partir de ce modèle**


Cet exemple illustre l’utilisation de sp\_execute\_external\_script pour générer des scores sur un modèle Python simple.

```
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

**Input query to generate the customer data**

DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders`

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

**Get data from input query**

customer_data = my_input_data

**Define the model**

n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Les en-têtes de colonne utilisés dans le code Python ne sont pas sortis dans SQL Server. Par conséquent, vous devez utiliser l’instruction WITH RESULTS pour spécifier les noms de colonnes et les types de données que SQL doit utiliser.

Pour calculer les scores, vous pouvez également utiliser la fonction [PREDICT](system-stored-procedures/../../t-sql/queries/predict-transact-sql.md) native, qui est généralement plus rapide car elle évite d’appeler le runtime Python ou R.




&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-create-primary-keystablescreate-primary-keysmd"></a>9. &nbsp; [Créer des clés primaires](tables/create-primary-keys.md)

*Mise à jour : 18-01-2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_8))

<!-- Source markdown line 102.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d18b485f314cc005d624cab8a51650d3b8f55f89 9bd2e9453206e8940d30b0a01c43f9d8e1aed606  (PR=4652  ,  Filename=create-primary-keys.md  ,  Dirpath=docs\relational-databases\tables\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



**Pour créer une clé primaire avec un index non-cluster dans une nouvelle table**


1.  Dans l’**Explorateur d’objets**, connectez-vous à une instance du moteur de base de données.

2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.

3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L’exemple crée une table, puis définit une clé primaire sur la colonne `CustomerID` et un index cluster sur `TransactionID`.

```
    USE AdventureWorks2012;
    GO
    CREATE TABLE Production.TransactionHistoryArchive1
    (
       CustomerID uniqueidentifier DEFAULT NEWSEQUENTIALID(),
       TransactionID int IDENTITY (1,1) NOT NULL,
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY NONCLUSTERED (uniqueidentifier)
    );
    GO

    -- Now add the clustered index
    CREATE CLUSTERED INDEX CIX_TransactionID ON Production.TransactionHistoryArchive1 (TransactionID);
    GO
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Articles similaires sur les articles nouveaux ou mis à jour

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Domaines *avec* des articles nouveaux ou mis à jour récemment


- [Nouveaux + Mis à jour (1 + 3) :&nbsp; **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **Système de la plateforme d’analyse pour SQL** (documentation)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (12 + 1) :**Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (6 + 2) :&nbsp; **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (15 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (2 + 9) :&nbsp; **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (1 + 0) :&nbsp; **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (1 + 1) :&nbsp; **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveaux + Mis à jour (1 + 1) :&nbsp; **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) :&nbsp; **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (1 + 2) :&nbsp; **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (0 + 2) :&nbsp; **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Domaines *sans* article nouveau ou mis à jour récemment


- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


