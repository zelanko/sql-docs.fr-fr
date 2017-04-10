---
title: "Index de hachage pour les tables m&#233;moire optimis&#233;es | Microsoft Docs"
ms.custom: 
  - "MSDN content"
  - "MSDN - SQL DB"
ms.date: "08/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-database"
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e922cc3a-3d6e-453b-8d32-f4b176e98488
caps.latest.revision: 7
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 7
---
# Index de hachage pour les tables m&#233;moire optimis&#233;es
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
Cet article décrit le type *hash* d’index qui est disponible pour une table mémoire optimisée. L’article :  
  
- fournit de courts exemples de code pour illustrer la syntaxe Transact-SQL ;  
- décrit les aspects fondamentaux des index de hachage ;  
- Décrit [comment estimer un nombre de compartiments approprié](#configuring_bucket_count) ;  
- explique comment concevoir et gérer vos index de hachage ;  
  
  
#### Condition préalable  
  
Des informations de contexte importantes pour comprendre cet article sont disponibles dans l’article :  
  
- [Index pour les tables optimisées en mémoire](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)  
  
  
  
## A. Syntaxe des index optimisés en mémoire  
  
  
### A.1 Exemple de code pour la syntaxe  
  
Cette sous-section contient un bloc de code Transact-SQL qui illustre les syntaxes disponibles pour créer un index de hachage sur une table mémoire optimisée :  
  
- L’exemple montre que l’index de hachage est déclaré à l’intérieur de l’instruction CREATE TABLE.  
  - Vous pouvez déclarer à la place l’index de hachage dans une instruction [ALTER TABLE...ADD INDEX](#h3-b2-declaration-limitations) distincte.  
  
  
  
    DROP TABLE IF EXISTS SupportEventHash;  
    go  
      
    CREATE TABLE SupportIncidentRating_Hash  
    (  
      SupportIncidentRatingId   int      not null   identity(1,1)  
        PRIMARY KEY NONCLUSTERED,  
      
      RatingLevel          int           not null,  
      
      SupportEngineerName  nvarchar(16)  not null,  
      Description          nvarchar(64)      null,  
      
      INDEX ix_hash_SupportEngineerName  
        HASH (SupportEngineerName) WITH (BUCKET_COUNT = 100000)  
    )  
      WITH (  
        MEMORY_OPTIMIZED = ON,  
        DURABILITY = SCHEMA_ONLY);  
    go  
  

Pour déterminer le droit `BUCKET_COUNT` pour vos données, consultez la page [Configuration du nombre de compartiments d’index de hachage](#configuring_bucket_count). 
  
## B. Index de hachage  
  
  
### B.1 Principes de base concernant les performances  
  
Les performances d’un index de hachage sont :  
  
- excellentes quand la clause WHERE spécifie une valeur *exacte* pour chaque colonne de la clé d’index de hachage ;  
- médiocres quand la clause WHERE recherche une *plage* de valeurs dans la clé d’index ;  
- médiocres quand la clause WHERE spécifie une valeur donnée pour la première colonne d’une clé d’index de hachage de deux colonnes, mais ne spécifie pas de valeur pour la *deuxième* colonne de la clé.  
  
  
<a name="h3-b2-declaration-limitations"></a>  
  
### B.2 Limitations de déclaration  
  
Un index de hachage peut exister uniquement sur une table optimisée en mémoire. Il ne peut pas exister sur une table sur disque.  
  
Un index de hachage peut être déclaré comme :  
  
- UNIQUE ou prendre par défaut la valeur Nonunique ;  
- NONCLUSTERED, qui est la valeur par défaut.   
  
  
Voici un exemple de la syntaxe de création d’un index de hachage en dehors de l’instruction CREATE TABLE :  
  
  
    ALTER TABLE MyTable_memop  
      ADD INDEX ix_hash_Column2 UNIQUE  
        HASH (Column2) WITH (BUCKET_COUNT = 64);  
  
  
  
### B.3 Compartiments et fonction de hachage  
  
Un index de hachage ancre ses valeurs de clés dans ce que nous appelons un tableau de *compartiments* :  
  
- Chaque compartiment comprend 8 octets, qui sont utilisés pour stocker l’adresse mémoire d’une liste de liens d’entrées d’index.  
- Chaque entrée correspond à une valeur pour une clé d’index, plus l’adresse de la ligne associée dans la table mémoire optimisée sous-jacente.  
  - Chaque entrée pointe vers l’entrée suivante dans une liste de liens d’entrées, toutes chaînées au compartiment actuel.  
  
  
L’algorithme de hachage tente de propager toutes les valeurs de clés uniques ou distinctes uniformément entre les compartiments, mais une régularité totale est un idéal inatteignable. Toutes les instances d’une valeur de clé donnée sont chaînées au même compartiment. Ce compartiment peut également mélanger toutes les instances d’une valeur de clé différente.  
  
- Ce mélange est appelé une *collision de hachage*. Les collisions sont courantes, mais pas souhaitables.  
- Un objectif réaliste est que 30 % des compartiments contiennent deux valeurs de clés différentes.  
  
  
Vous déclarez le nombre de compartiments qu’un index de hachage doit comprendre.  
  
- Plus le rapport entre les compartiments et les lignes de table ou les valeurs distinctes est faible, plus la liste moyenne de liens de compartiments sera longue.  
- Les listes de liens courtes sont plus rapides que les listes de liens longues.  
  
  
SQL Server possède une fonction de hachage qu’il utilise pour tous les index de hachage :  
  
- La fonction de hachage est déterministe : avec la même valeur de clé d’entrée, elle génère systématiquement le même emplacement de compartiment.  
- Avec des appels répétés, les sorties de la fonction de hachage ont tendance à former une distribution de Poisson ou de courbe en cloche, et non une distribution plate linéaire.  
  
  
L’interaction entre l’index de hachage et les compartiments est résumée dans l’image ci-dessous.  
  
  
![hekaton_tables_23d](../../relational-databases/in-memory-oltp/media/hekaton-tables-23d.png "Index keys, input into hash function, output is address of a hash bucket, which points to head of chain.")  
  
  
  
### B.4 Versions de lignes et garbage collection  
  
  
Dans une table mémoire optimisée, quand une ligne est affectée par une instruction SQL UPDATE, la table crée une version mise à jour de la ligne. Lors de la transaction de mise à jour, d’autres sessions peuvent être en mesure de lire l’ancienne version de la ligne et d’éviter ainsi le ralentissement des performances associé à un verrou de ligne.  
  
L’index de hachage peut également avoir différentes versions de ses entrées pour prendre en charge la mise à jour.  
  
Par la suite, quand les anciennes versions ne sont plus nécessaires, un thread garbage collection (GC) traverse les compartiments et leurs listes de liens pour nettoyer les anciennes entrées. Le thread GC fonctionne mieux si les longueurs de chaîne des listes de liens sont courtes.   
  
<a name="configuring_bucket_count"></a>
  
## C. Configuration du nombre de compartiments d’index de hachage  
  
Le nombre de compartiments d’index de hachage est spécifié au moment de la création de l’index et peut être modifié à l’aide de la syntaxe ALTER TABLE...ALTER INDEX REBUILD.  
  
Dans la plupart des cas, le nombre de compartiments doit être compris entre 1 et 2 fois le nombre de valeurs distinctes dans la clé d’index.   
Vous ne pouvez pas toujours prédire le nombre exact de valeurs qu'une clé d'index donnée peut avoir ou aura. Les performances sont en général encore bonnes si la valeur **BUCKET_COUNT** est inférieure ou égale à 10 fois le nombre réel de valeurs de clés et il est généralement préférable de surestimer que de sous-estimer.  
  
Un trop *petit* nombre de compartiments présente les inconvénients suivants :  
  
- Davantage de collisions de hachage de valeurs de clés distinctes.  
  - Chaque valeur distincte est forcée de partager le même compartiment avec une autre valeur distincte.  
  - La longueur de chaîne moyenne par compartiment augmente.  
  - Plus la chaîne de compartiment est longue, plus les recherches d’égalité sont lentes dans l’index.  
  
Un trop *grand* nombre de compartiments présente les inconvénients suivants :  
  
- Un nombre de compartiments trop élevé peut entraîner plus de compartiments vides.  
  - Des compartiments vides affectent les performances des analyses d’index complètes. Si celles-ci sont effectuées régulièrement, envisagez de choisir un nombre de compartiments proche du nombre de valeurs de clés distinctes.  
  - Des compartiments vides utilisent de la mémoire, même si chaque compartiment utilise seulement 8 octets.  
    
  
> [AZURE.NOTE] L’ajout de nouveaux compartiments ne fait rien pour réduire le chaînage groupé des entrées qui partagent une valeur en double. Le taux de duplication de valeurs est utilisé pour déterminer si un hachage constitue le type d’index approprié, et non pour calculer le nombre de compartiments.  
  
  
  
### C.1 Nombres pratiques  
  
Même si la valeur **BUCKET_COUNT** se situe modérément en dessous ou au-dessus de la plage par défaut, les performances de l’index de hachage sont susceptibles d’être tolérables ou acceptables. Aucune situation de crise n’est générée.  
  
Affectez à l’index de hachage une valeur **BUCKET_COUNT** à peu près égale au nombre de lignes que vous pensez que votre table optimisée en mémoire finira par atteindre.  
  
Supposons que votre table en développement comprend 2 000 000 de lignes, mais vous prévoyez que cette quantité sera multipliée par 10 pour atteindre 20 000 000 de lignes. Démarrez avec un nombre de compartiments qui représente 10 fois le nombre de lignes dans la table. Vous avez ainsi la place pour une quantité accrue de lignes.  
  
- Dans l’idéal, vous augmentez le nombre de compartiments quand la quantité de lignes atteint le nombre de compartiments initial.  
- Même si la quantité de lignes atteint un nombre 5 fois plus élevé que le nombre de compartiments, les performances restent satisfaisantes dans la plupart des cas.  
  
Supposons qu’un index de hachage possède 10 000 000 de valeurs de clés distinctes.  
  
- Un nombre de compartiments de 2 000 000 représente le seuil minimal que vous pouvez accepter. Le degré de détérioration des performances peut être tolérable.  
  
### C.2 Trop de valeurs en double dans l’index ?  
  
Si les valeurs indexées de hachage ont un taux élevé de doublons, les compartiments de hachage ont des chaînes plus longues.  
  
Supposons que vous utilisez la même table SupportEvent que pour le bloc de code de la syntaxe T-SQL plus haut. Le code T-SQL suivant montre comment vous pouvez rechercher et afficher le rapport entre *toutes* les valeurs et les valeurs *uniques* :  
  
        -- Calculate ratio of:  Rows / Unique_Values.  
    DECLARE @allValues float(8) = 0.0, @uniqueVals float(8) = 0.0;  
      
    SELECT @allValues = Count(*) FROM SupportEvent;  
      
    SELECT @uniqueVals = Count(*) FROM  
      (SELECT DISTINCT SupportEngineerName  
         FROM SupportEvent) as d;  
      
        -- If (All / Unique) >= 10.0, use a nonclustered index, not a hash.   
    SELECT Cast((@allValues / @uniqueVals) as float) as [All_divby_Unique];  
    go  
  
- Un résultat de rapport supérieur ou égal à 10,0 signifie qu’un hachage constitue un type d’index médiocre. Envisagez plutôt d’utiliser un index non-cluster.   
  
## D. Résolution de problèmes liés au nombre de compartiments d’index de hachage  
  
Cette section décrit comment résoudre les problèmes liés au nombre de compartiments pour votre index de hachage.  
  
### D.1 Analyser les statistiques relatives aux chaînes et compartiments vides  
  
Vous pouvez analyser les statistiques de l’intégrité de vos index de hachage en exécutant l’instruction T-SQL SELECT suivante. L’instruction SELECT utilise la vue de gestion de données nommée **sys.dm_db_xtp_hash_index_stats**.  
  
  
```t-sql
  SELECT  
    QUOTENAME(SCHEMA_NAME(t.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(h.object_id)) as [table],   
    i.name                   as [index],   
    h.total_bucket_count,  
    h.empty_bucket_count,  
      
    FLOOR((  
      CAST(h.empty_bucket_count as float) /  
        h.total_bucket_count) * 100)  
                             as [empty_bucket_percent],  
    h.avg_chain_length,   
    h.max_chain_length  
  FROM  
         sys.dm_db_xtp_hash_index_stats  as h   
    JOIN sys.indexes                     as i  
            ON h.object_id = i.object_id  
           AND h.index_id  = i.index_id  
    JOIN sys.memory_optimized_tables_internal_attributes ia ON h.xtp_object_id=ia.xtp_object_id
    JOIN sys.tables t on h.object_id=t.object_id
  WHERE ia.type=1
  ORDER BY [table], [index];  
```
  
  
Comparez les résultats de l’instruction SELECT aux règles statistiques suivantes :  
  
- Compartiments vides :  
  - 33 % est une valeur cible correcte, mais un pourcentage plus important (même 90 %) est généralement accepté.  
  - Quand le nombre de compartiments est égal au nombre de valeurs de clés distinctes, environ 33 % des compartiments sont vides.  
  - Une valeur inférieure à 10 % est trop faible.  
- Chaînes dans les compartiments :  
  - Une longueur de chaîne moyenne de 1 est idéale en l’absence de valeurs de clé d’index en double. Les longueurs de chaîne jusqu’à 10 sont généralement acceptables.  
  - Si la longueur de chaîne moyenne est supérieure à 10 et que le pourcentage de compartiments vides est supérieur à 10 %, les données comportent tant de doublons qu’il est possible qu’un index de hachage ne représente pas le type le plus approprié.  
  

  
### D.2 Démonstration de chaînes et de compartiments vides  
  
  
Le bloc de code T-SQL suivant vous permet de tester aisément un `SELECT * FROM sys.dm_db_xtp_hash_index_stats;`. Le bloc de code se termine en 1 minute. Voici les phases du bloc de code suivant :  
  
  
1. Crée une table optimisée en mémoire avec quelques index de hachage.  
2. Remplit la table avec des milliers de lignes.  
    a. Un opérateur modulo est utilisé pour configurer le taux de valeurs en double dans la colonne StatusCode.  
    b. La boucle INSERT ajoute 262 144 lignes en une minute environ.  
3. PRINT imprime un message vous demandant d’exécuter l’instruction SELECT précédente à partir de **sys.dm_db_xtp_hash_index_stats**.  
  
  
```t-sql
    DROP TABLE IF EXISTS SalesOrder_Mem;  
    go  
      
      
    CREATE TABLE SalesOrder_Mem  
    (  
      SalesOrderId   uniqueidentifier  NOT NULL  DEFAULT newid(),  
      OrderSequence  int               NOT NULL,  
      OrderDate      datetime2(3)      NOT NULL,  
      StatusCode     tinyint           NOT NULL,  
      
      PRIMARY KEY NONCLUSTERED  
          HASH (SalesOrderId)  WITH (BUCKET_COUNT = 262144),  
      
      INDEX ix_OrderSequence  
          HASH (OrderSequence) WITH (BUCKET_COUNT = 20000),  
      
      INDEX ix_StatusCode  
          HASH (StatusCode)    WITH (BUCKET_COUNT = 8),  
      
      INDEX ix_OrderDate       NONCLUSTERED (OrderDate DESC)  
    )  
      WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
    go  
      
        --------------------  
      
    SET NoCount ON;  
      
      -- Same as PK bucket_count.  68 seconds to complete.  
    DECLARE @i int = 262144;  
      
    BEGIN TRANSACTION;  
      
    WHILE @i > 0  
    Begin  
      
      INSERT SalesOrder_Mem  
          (OrderSequence, OrderDate, StatusCode)  
        Values  
          (@i, GetUtcDate(), @i % 8);  -- Modulo technique.  
      
      SET @i -= 1;  
    End  
    COMMIT TRANSACTION;  
      
    PRINT 'Next, you should query:  sys.dm_db_xtp_hash_index_stats .';  
    go  
```  
  
  
La boucle INSERT précédente effectue les opérations suivantes :  
  
- Elle insère des valeurs uniques pour l’index de clé primaire et pour ix_OrderSequence.  
- Elle insère deux cent mille lignes qui représentent uniquement 8 valeurs distinctes pour StatusCode. Par conséquent, le taux de duplication de valeurs est élevé dans l’index ix_StatusCode.  
  
Pour obtenir des informations de dépannage quand le nombre de compartiments n’est pas optimal, examinez la sortie suivante de l’instruction SELECT dans **sys.dm_db_xtp_hash_index_stats**. Pour ces résultats, nous avons ajouté `WHERE Object_Name(h.object_id) = 'SalesOrder_Mem'` à l’instruction SELECT copiée à partir de la section D.1.  
  
  
  
Nos résultats SELECT sont affichés après le code, artificiellement divisés en deux tables de résultats plus étroites pour un meilleur affichage.  
  
- Voici les résultats pour le *nombre de compartiments*.  
  
  
| IndexName | total_bucket_count | empty_bucket_count | EmptyBucketPercent |  
| :-------- | -----------------: | -----------------: | -----------------: |  
| ix_OrderSequence | 32768 | 13 | 0 |  
| ix_StatusCode | 8 | 4 | 50 |  
| PK_SalesOrd_B14003... | 262144 | 96525 | 36 |  
  
  
- Ensuite, voici les résultats pour la *longueur de chaîne*.  
  
  
| IndexName | avg_chain_length | max_chain_length |  
| :-------- | ---------------: | ---------------: |  
| ix_OrderSequence | 8 | 26 |  
| ix_StatusCode | 65536 | 65536 |  
| PK_SalesOrd_B14003... | 1 | 8 |  
  
  
  
  
Interprétons les tables de résultats précédentes pour les trois index de hachage :  
  
*ix_StatusCode :*  
  
- 50 % des compartiments sont vides, ce qui est correct.  
- Cependant, la longueur de chaîne moyenne est très élevée (65536).  
  - Cela indique un taux élevé de valeurs en double.  
  - Par conséquent, l’utilisation d’un index de hachage n’est pas appropriée dans ce cas. Il convient d'utiliser un index non cluster.  
  
*ix_OrderSequence :*  
  
- 0 % des compartiments sont vides, ce qui est trop faible.  
- La longueur de chaîne moyenne est égale à 8, même si toutes les valeurs de cet index sont uniques.  
  - Par conséquent, le nombre de compartiments doit être augmenté pour ramener la longueur de chaîne moyenne plus près de 2 ou 3.  
- Étant donné que la clé d’index a 262 144 valeurs uniques, le nombre de compartiments doit être supérieur ou égal à 262 144.  
  - Si une croissance future est attendue, le nombre de compartiments doit être supérieur.  
  
*Index de clé primaire (PK_SalesOrd_...) :*  
  
- 36 % des compartiments sont vides, ce qui est correct.  
- La longueur de chaîne moyenne est égale à 1, ce qui est également correct. Aucun changement n’est nécessaire.  
  
  
### D.3 Équilibre du compromis  
  
Les charges de travail OLTP se concentrent sur des lignes individuelles. Les analyses de tables complètes ne sont généralement pas un problème critique pour les performances pour les charges de travail OLTP. Par conséquent, un compromis doit être trouvé entre les éléments suivants :  
  
- la quantité d’utilisation de la mémoire par rapport aux  
- performances des tests d’égalité et des opérations d’insertion.  
  
  
*Si l’utilisation de la mémoire représente le principal critère :*  
  
- Choisissez un nombre de compartiments proche du nombre d’enregistrements de clés d’index.  
- Le nombre de compartiments ne doit pas être considérablement inférieur au nombre de valeurs de clés d'index, car cela affecte la plupart des opérations DML tout comme le temps de récupération de la base de données après le redémarrage du serveur.  
  
  
*Si les performances des tests d’égalité représentent le principal critère :*  
  
- Un nombre plus élevé de compartiments, égal à 2 ou 3 fois le nombre de valeurs d’index uniques, semble approprié. Un nombre plus élevé signifie :  
  - des récupérations plus rapides lors de la recherche d’une valeur spécifique ;  
  - une utilisation accrue de la mémoire ;  
  - une augmentation du temps requis pour une analyse complète de l’index de hachage.  
  
  
  
  
## E. Avantages des index de hachage  
  
  
Un index de hachage est préférable à un index non cluster dans les cas suivants :  
  
- Les requêtes testent la colonne indexée à l’aide d’une clause WHERE avec une égalité, comme dans le code suivant :  
  
  
  
    SELECT col9 FROM TableZ  
        WHERE Z_Id = 2174;  
  
  
  
### E.1 Clés d’index de hachage à plusieurs colonnes  
  
  
Votre index à deux colonnes peut être un index non-cluster ou un index de hachage. Supposons que les colonnes d’index sont col1 et col2. D’après l’instruction SQL SELECT suivante, seul l’index non-cluster peut être utile à l’optimiseur de requête :  
  
  
    SELECT col1, col3  
        FROM MyTable_memop  
        WHERE col1 = 'dn';  
  
  
L’index de hachage a besoin de la clause WHERE pour spécifier un test d’égalité pour chacune des colonnes dans sa clé. Sinon, l’index de hachage n’est pas utile à l’optimiseur.  
  
Aucun type d’index n’est utile si la clause WHERE spécifie uniquement la deuxième colonne de la clé d’index.  
  
  
  
\<!--   
Hash_Indexes_for_Memory-Optimized_Tables.md , which is....  
CAPS guid: {e922cc3a-3d6e-453b-8d32-f4b176e98488}  
CAPS guid of parent is: {eecc5821-152b-4ed5-888f-7c0e6beffed9}  
  
  
  
  
| IndexName | total_bucket_count | empty_bucket_count | EmptyBucketPercent | avg_chain_length | max_chain_length |  
| :-------- | -----------------: | -----------------: | -----------------: | ---------------: | ---------------: |  
| ix_OrderSequence | 32768 | 13 | 0 | 8 | 26 |  
| ix_StatusCode | 8 | 4 | 50 | 65536 | 65536 |  
| PK_SalesOrd_B14003E308C1A23C | 262144 | 96525 | 36 | 1 | 8 |  
  
  
  
  
GeneMi  ,  2016-05-05  Thursday  15:01pm  
-->  
  
  
  
