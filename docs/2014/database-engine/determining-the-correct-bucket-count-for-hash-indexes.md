---
title: Déterminer le nombre de compartiments Correct pour les index de hachage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6d1ac280-87db-4bd8-ad43-54353647d8b5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56999c5e74648ecd36adea3ee941627c1e2e607b
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53377899"
---
# <a name="determining-the-correct-bucket-count-for-hash-indexes"></a>Déterminer le nombre de compartiments correct pour les index de hachage
  Vous devez spécifier une valeur pour le paramètre `BUCKET_COUNT` lorsque vous créez la table mémoire optimisée. Cette rubrique fournit des recommandations pour déterminer la valeur appropriée du paramètre `BUCKET_COUNT`. Si vous ne pouvez pas déterminer le nombre de compartiments correct, utilisez un index non cluster à la place.  Une valeur `BUCKET_COUNT` incorrecte, en particulier une valeur trop basse, peut avoir un impact important sur les performances de la charge de travail, ainsi que sur le temps de récupération de la base de données. Il vaut mieux surestimer le nombre de compartiments.  
  
 Les clés d'index dupliquées peuvent réduire les performances avec un index hach car elles sont hachées dans le même compartiment, ce qui entraîne l'augmentation de la chaîne du compartiment.  
  
 Pour plus d'informations sur les index de hachage non cluster, consultez [Hash Indexes](hash-indexes.md) et [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Une table de hachage est allouée pour chaque index de hachage sur une table mémoire optimisée. La taille de la table de hachage allouée pour un index est spécifié par le `BUCKET_COUNT` paramètre dans [CREATE TABLE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-table-transact-sql) ou [CREATE TYPE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-type-transact-sql). Le nombre de compartiment est arrondi en interne à la puissance de 2 suivante. Par exemple, la spécification d'un nombre de compartiments égal à 300 000 créera un nombre réel de compartiments égal à 524 288.  
  
 Pour accéder à un article et à une vidéo sur le nombre de compartiments, consultez [How to determine the right bucket count for hash indexes (In-Memory OLTP)](https://go.microsoft.com/fwlink/p/?LinkId=525853).  
  
## <a name="recommendations"></a>Recommandations  
 Dans la plupart des cas, le nombre de compartiments doit être compris entre 1 et 2 fois par le nombre estimé maximal de valeurs distinctes dans la clé d'index. Si la clé d'index contient de nombreuses valeurs dupliquées (en moyenne il y a plus de 10 lignes pour chaque valeur de clé d'index), utilisez un index non cluster à la place  
  
 Vous ne pouvez pas toujours prédire le nombre exact de valeurs qu'une clé d'index donnée peut avoir ou aura. Les performances doivent être acceptables si la valeur `BUCKET_COUNT` est inférieure ou égale à 5 fois le nombre réel de valeurs de clés.  
  
 Pour déterminer le nombre de clés d'index uniques dans les données existantes, utilisez des requêtes similaires aux exemples suivants :  
  
### <a name="primary-key-and-unique-indexes"></a>Clé primaire et index uniques  
 Étant donné que l'index de clé primaire est unique, le nombre de valeurs distinctes dans la clé correspond au nombre de lignes dans la table. Pour obtenir un exemple de clé primaire sur (SalesOrderID, SalesOrderDetailID) dans la table Sales.SalesOrderDetail dans la base de données AdventureWorks, exécutez la requête suivante pour calculer le nombre de valeurs de clé primaire distinctes, qui correspond au nombre de lignes dans la table :  
  
```tsql  
SELECT COUNT(*) AS [row count]   
FROM Sales.SalesOrderDetail  
```  
  
 Cette requête affiche un nombre de lignes égal à 121 317. Utilisez un nombre de compartiments de 240 000 si le nombre de lignes ne va pas changer de manière significative. Utilisez un nombre de compartiments de 480 000 si le nombre de commandes client dans la table va quadrupler.  
  
### <a name="non-unique-indexes"></a>Index non uniques  
 Pour les autres index, par exemple un index à plusieurs colonnes sur (SpecialOfferID, ProductID), exécutez la requête suivante pour déterminer le nombre de valeurs de clé d'index uniques :  
  
```tsql  
SELECT COUNT(*) AS [SpecialOfferID_ProductID index key count]  
FROM   
   (SELECT DISTINCT SpecialOfferID, ProductID   
    FROM Sales.SalesOrderDetail) t  
```  
  
 Cette requête retourne un nombre de clés d'index (pour SpecialOfferID, ProductID) de 484, indiquant qu'un index non cluster doit être utilisé à la place d'un index hach non cluster.  
  
### <a name="determining-the-number-of-duplicates"></a>Détermination du nombre de doublons  
 Pour déterminer le nombre moyen de valeurs dupliquées pour une valeur de clé d'index, divisez le nombre total de lignes par le nombre de clés d'index uniques.  
  
 Pour l'exemple d'index sur (SpecialOfferID, ProductID), cela aboutit à 121317 / 484 = 251. Cela signifie que les valeurs de clé d'index ont une moyenne de 251, par conséquent, ceci doit être un index non cluster.  
  
## <a name="troubleshooting-the-bucket-count"></a>Résolution des problèmes liés au nombre de compartiments  
 Pour résoudre les problèmes de nombre de compartiments dans les tables optimisées en mémoire, utilisez [sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql) pour obtenir les statistiques sur les compartiments vides et la longueur des chaînes de ligne. La requête suivante peut être utilisée pour obtenir les statistiques sur tous les index de hachage dans la base de données active. Son exécution peut prendre plusieurs minutes s'il existe de grandes tables dans la base de données.  
  
```tsql  
SELECT   
   object_name(hs.object_id) AS 'object name',   
   i.name as 'index name',   
   hs.total_bucket_count,  
   hs.empty_bucket_count,  
   floor((cast(empty_bucket_count as float)/total_bucket_count) * 100) AS 'empty_bucket_percent',  
   hs.avg_chain_length,   
   hs.max_chain_length  
FROM sys.dm_db_xtp_hash_index_stats AS hs   
   JOIN sys.indexes AS i   
   ON hs.object_id=i.object_id AND hs.index_id=i.index_id  
```  
  
 Les deux indicateurs clés d'intégrité d'index de hachage sont :  
  
 *empty_bucket_percent*  
 *empty_bucket_percent* indique le nombre de compartiments vides dans l'index de hachage.  
  
 Si *empty_bucket_percent* est inférieur à 10 pour cent, le nombre de compartiments est probablement trop bas. Idéalement, *empty_bucket_percent* devrait être de 33 pour cent ou plus. Si le nombre de compartiments correspond au nombre de valeurs de clés d'index, environ 1/3 des compartiments est vide, en raison de la distribution du hachage.  
  
 *avg_chain_length*  
 *avg_chain_length* indique la longueur maximale des chaînes de ligne dans les compartiments de hachage.  
  
 Si *avg_chain_length* est supérieur à 10 et *empty_bucket_percent* est supérieur à 10 pour cent, il existe probablement plusieurs valeurs de clé d'index dupliquées et un index non cluster serait plus approprié. Une longueur de chaîne moyenne de 1 est idéale.  
  
 Il y a deux facteurs qui ont un impact sur la longueur de chaîne :  
  
1.  Les doublons. Toutes les lignes en double font partie de la même chaîne dans l'index hach.  
  
2.  Plusieurs valeurs de clés mappent sur le même compartiment. Plus le nombre de compartiments est faible, plus il y aura de compartiments qui auront plusieurs valeurs mappées.  
  
 En guise d'exemple, examinez le tableau suivant et le script pour insérer des lignes d'exemple dans la table :  
  
```tsql  
CREATE TABLE [Sales].[SalesOrderHeader_test]  
(  
   [SalesOrderID] [uniqueidentifier] NOT NULL DEFAULT (newid()),  
   [OrderSequence] int NOT NULL,  
   [OrderDate] [datetime2](7) NOT NULL,  
   [Status] [tinyint] NOT NULL,  
  
PRIMARY KEY NONCLUSTERED HASH ([SalesOrderID]) WITH ( BUCKET_COUNT = 262144 ),  
INDEX IX_OrderSequence HASH (OrderSequence) WITH ( BUCKET_COUNT = 20000),  
INDEX IX_Status HASH ([Status]) WITH ( BUCKET_COUNT = 8),  
INDEX IX_OrderDate NONCLUSTERED ([OrderDate] ASC),  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
DECLARE @i int = 0  
BEGIN TRAN  
WHILE @i < 262144  
BEGIN  
   INSERT Sales.SalesOrderHeader_test (OrderSequence, OrderDate, [Status]) VALUES (@i, sysdatetime(), @i % 8)  
   SET @i += 1  
END  
COMMIT  
GO  
```  
  
 Le script insère 262 144 lignes dans la table. Il insère des valeurs uniques dans l'index de clé primaire et dans IX_OrderSequence. Il insère plusieurs valeurs dupliquées dans l'index IX_Status : le script génère uniquement 8 valeurs distinctes.  
  
 La sortie de la requête de résolution des problèmes BUCKET_COUNT est la suivante :  
  
|nom de l'index|total_bucket_count|empty_bucket_count|empty_bucket_percent|avg_chain_length|max_chain_length|  
|----------------|--------------------------|--------------------------|----------------------------|------------------------|------------------------|  
|IX_Status|8|4|50|65536|65536|  
|IX_OrderSequence|32768|13|0|8|26|  
|PK_SalesOrd_B14003C3F8FB3364|262144|96319|36|1|8|  
  
 Considérez les trois index de hachage sur cette table :  
  
-   IX_Status : 50 pour cent des compartiments sont vides, ce qui est correct. Cependant, la longueur de chaîne moyenne est très élevée (65 536). Cela indique un grand nombre de valeurs dupliquées. Par conséquent, l'utilisation d'un index de hachage non cluster n'est pas appropriée dans ce cas. Il convient d'utiliser un index non cluster.  
  
-   IX_OrderSequence : 0 pour cent des compartiments sont vides, ce qui est trop faible. En outre, la longueur de chaîne moyenne est de 8. En tant donné que les valeurs dans cet index sont uniques, cela signifie que 8 valeurs en moyenne sont mappées à chaque compartiment. Le nombre de compartiments doit être augmenté. Étant donné que la clé d'index a 262 144 valeurs uniques, le nombre de compartiments doit être égal ou supérieur à 262 144. Si une croissance future est attendue, le nombre doit être supérieur.  
  
-   Index de clé primaire (PK__SalesOrder …) : 36 pour cent des compartiments sont vides, ce qui est correct. En outre, la longueur de chaîne moyenne est de 1, ce qui est également correct. Aucun changement n'est requis.  
  
 Pour plus d'informations sur le dépannage de vos index de hachage mémoire optimisés, consultez [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md).  
  
## <a name="detailed-considerations-for-further-optimization"></a>Observations détaillées pour une meilleure optimisation  
 Cette section décrit d'autres éléments à prendre en considération pour optimiser le nombre de compartiments.  
  
 Pour obtenir de meilleures performances pour les index de hachage, équilibrez la quantité de mémoire allouée à la table de hachage et le nombre de valeurs distinctes dans la clé d'index. Il existe également un équilibre entre les performances des recherches de points et les analyses de table :  
  
-   Plus la valeur du nombre de compartiments est élevée, plus les compartiments vides seront nombreux dans l'index. Cela a un impact sur l'utilisation de la mémoire (8 octets par compartiment) et les performances des analyses de table, car chaque compartiment est analysé dans le cadre d'une analyse de table.  
  
-   Plus le nombre de compartiments est faible, plus le nombre de valeurs affectées à un seul compartiment est grand. Cela réduit les performances des recherches et des insertions de points, car [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut potentiellement parcourir plusieurs valeurs dans un seul compartiment pour trouver la valeur spécifiée par le prédicat de recherche.  
  
 Si le nombre de compartiments est considérablement inférieur au nombre de clés d'index uniques, plusieurs valeurs mapperont à chaque compartiment. Cela dégrade les performances de la plupart des opérations DML, en particulier les recherches de points (recherches de clés d'index individuelles) et des opérations d'insertion. Par exemple, vous pouvez constater des performances médiocres des requêtes et SELECT et des opérations UPDATE et DELETE avec des prédicats d'égalité correspondant aux colonnes clés d'index dans la clause WHERE. Un nombre de compartiments faible affectera également le temps de récupération de la base de données, car les index sont recréés au démarrage de la base de données.  
  
### <a name="duplicate-index-key-values"></a>Valeurs de clé d'index dupliquées  
 Les valeurs dupliquées peuvent augmenter l'impact des collisions de hachage sur les performances. Cela n'est généralement pas un problème si chaque clé d'index a un nombre faible de doublons. Mais des problèmes peuvent surgir si l'écart entre le nombre de clés d'index uniques et le nombre de lignes de la table est très grand.  
  
 Toutes les lignes ayant la même clé d'index vont aller dans la même chaîne dupliquée. Si plusieurs clés d'index sont dans le même compartiment en raison d'une collision de hachage, les scanneurs d'index doivent toujours analyser la chaîne en double complète pour la première valeur avant de pouvoir localiser la première ligne correspondant à la deuxième valeur. Les clés dupliquées rendent plus difficile la localisation de la ligne par le garbage collection. Par exemple, s'il existe 1 000 doublons d'une clé et une des lignes est supprimée, le garbage collector doit analyser la chaîne de 1 000 doublons pour dissocier la ligne de l'index. Cela est vrai même si la requête qui a trouvé la suppression a utilisé un index plus efficace (un index de clé primaire) pour localiser la ligne, car le garbage collector doit dissocier de chaque index.  
  
 Pour les index de hachage, il existe deux façons de réduire le travail causé par les valeurs de clé d'index dupliquées :  
  
-   Utilisez plutôt un index non cluster. Vous pouvez diminuer les doublons en ajoutant des colonnes à la clé d'index sans modifier l'application.  
  
-   Définissez un nombre très élevé de compartiments pour l'index. Par exemple, 20 à 100 fois le nombre de clés d'index uniques. Cela va réduire les collisions de hachage.  
  
### <a name="small-tables"></a>Petites tables  
 Pour les tables plus petites, l'utilisation de la mémoire n'est généralement pas un souci, car la taille de l'index sera petite comparée à la taille générale de la base de données.  
  
 Vous devez maintenant faire un choix en fonction du type de performances que vous recherchez :  
  
-   Si les opérations critiques pour les performances sur l'index sont majoritairement des recherches de point et/ou des opérations d'insertion, un nombre plus élevé de compartiments peut contribuer à réduire la probabilité de collisions de hachage. Trois fois le nombre de lignes, ou plus, est la meilleure option.  
  
-   Si les analyses complètes d'index sont les principales opérations critiques pour les performances, utilisez un nombre de compartiments qui est proche du nombre réel de valeurs de clés d'index.  
  
### <a name="big-tables"></a>Grandes tables  
 Pour les grandes tables, l'utilisation de la mémoire peut devenir un problème. Par exemple, avec une table de 250 millions de lignes qui a 4 index de hachage, chacun avec un nombre de compartiments d’un milliard, la surcharge pour les tables de hachage est de 4 index * 1 milliard de compartiments \* 8 octets = 32 gigaoctets d’utilisation de la mémoire. Lorsque vous choisissez un nombre de compartiments de 250 millions pour chacun des index, la charge totale pour les tables de hachage est de 8 gigaoctets. Notez que cela s’ajoute aux 8 octets de l’utilisation de la mémoire chaque index ajoute à chaque ligne individuelle, ce qui est de 8 gigaoctets dans ce scénario (4 index \* 8 octets \* 250 millions de lignes).  
  
 Les analyses de table complètes ne sont généralement pas un problème critique pour les performances pour les charges de travail OLTP. Par conséquent, un choix doit être fait entre l'utilisation de la mémoire et les performances de la recherche de point et des opérations d'insertion :  
  
-   Si l'utilisation de la mémoire est un souci, choisissez un nombre de compartiments similaire au nombre de valeurs de clés d'index. Le nombre de compartiments ne doit pas être considérablement inférieur au nombre de valeurs de clés d'index, car cela affecte la plupart des opérations DML tout comme le temps de récupération de la base de données après le redémarrage du serveur.  
  
-   Pour optimiser les performances des recherches de point, un nombre plus élevé de compartiments, égal à 2 ou 3 fois le nombre de valeurs d'index uniques, semble approprié. Un nombre plus élevé de compartiments signifierait une utilisation accrue de mémoire et une augmentation du temps requis pour une analyse d'index complète.  
  
## <a name="see-also"></a>Voir aussi  
 [Index sur des tables optimisées en mémoire](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
