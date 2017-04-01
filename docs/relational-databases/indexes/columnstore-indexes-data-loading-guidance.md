---
title: "Chargement de donn&#233;es d’index columnstore | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b29850b5-5530-498d-8298-c4d4a741cdaf
caps.latest.revision: 31
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 28
---
# Chargement de donn&#233;es d’index columnstore
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Chargez des données dans un index columnstore en utilisant le chargement en masse SQL standard et des méthodes d’insertion segmentée. Ces méthodes incluent le programme de copie en bloc (BCP), Integration Services et les instructions MERGE ou INSERT de Transact-SQL.  
  
 Vous ne connaissez pas les index columnstore ? Prenez connaissance des termes et concepts examinés dans le [Guide des index Columnstore](../Topic/Columnstore%20Indexes%20Guide.md).  
  
 Vous avez besoin d’une présentation approfondie ? Consultez ce [billet de blog](http://blogs.msdn.com/b/sqlcat/archive/2015/03/11/data-loading-performance-considerations-on-tables-with-clustered-columnstore-index.aspx).  
  
##  <a name="dataload_cci"></a> Chargement en masse dans un index columnstore cluster  
 Pour charger des lignes en masse dans un index columnstore cluster, vous pouvez vous servir de l’outil en ligne de commande BCP ou d’Integration Services, ou encore sélectionner des lignes dans une table de mise en lots.  
  
 ![Chargement dans un index columnstore en cluster](../../relational-databases/indexes/media/sql-server-pdw-columnstore-loadprocess.gif "Chargement dans un index columnstore en cluster")  
  
 Comme l’indique le diagramme :  
  
1.  Un chargement en masse ne trie pas les données. Les données sont insérées dans des groupes de lignes (rowgroup), dans l’ordre de leur réception.  
  
2.  Si la taille du lot est supérieure ou égale à 102 400, les lignes sont directement insérées dans des rowgroup compressés. Pour une importation en bloc efficace, il est recommandé de choisir une taille de lot supérieure ou égale à 102 400 lignes, car cela permet d’éviter de déplacer les lignes de données vers des rowgroup delta avant leur déplacement final vers des rowgroup compressés par un thread d’arrière-plan, le moteur de tuple.  
  
3.  Si la taille du lot est inférieure à 102 400 lignes, ou si les lignes restantes sont en nombre inférieur à 102 400, celles-ci sont chargées dans des rowgroup delta.  
  
 Les optimisations disponibles pour le chargement en masse dans un index columnstore cluster sont les suivantes :  
  
-   Charge parallèle : vous pouvez effectuer plusieurs importations en bloc simultanées (BCP ou insertion en bloc) chargeant chacune un fichier de données distinct. Contrairement à l’utilisation d’une table rowstore, vous n’avez pas besoin de spécifier l’option d'insertion en bloc TABLOCK, car chaque thread d’importation en bloc charge des données exclusivement dans un rowgroup distinct (compressé ou delta) avec un verrou exclusif appliqué à celui-ci.   L’utilisation de option d'insertion en bloc TABLOCK applique un verrou exclusif à la table, qui empêche d’importer des données en parallèle.  
  
-   Optimisation du journal : le chargement en masse fait l’objet d’une journalisation minimale lors du chargement de données dans le rowgroup compressé. En revanche, aucune journalisation minimale n’est effectuée quand des données sont chargées dans un rowgroup delta sont la taille de lot est inférieure à 102 400.  
  
-   Optimisation du verrouillage : lors du chargement dans rowgroup compressé, le verrou X sur le rowgroup est acquis. Toutefois, lors d’un chargement en bloc dans un rowgroup delta, un verrou X est acquis au niveau du rowgroup, mais SQL Server continue de verrouiller les verrous PAGE/EXTENT, car le verrou X du rowgroup ne fait pas partie de la hiérarchie de verrouillage.  
  
 Si vous disposez d’un ou plusieurs index non cluster, aucune optimisation du verrouillage ou du journal n’est effectuée pour l’index proprement dit, mais les optimisations de l’index columnstore cluster décrites ci-dessus ont toujours lieu.  
  
## Fonctionnement du deltastore  
 Les index columnstore cluster collectent jusqu’à 1 048 576 lignes dans un deltastore avant de les compresser dans le rowgroup compressé. Cela améliore la compression de l’index columnstore. Quand un rowgroup deltastore contient 1 048 576 lignes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] marque le rowgroup comme étant fermé. Un processus en arrière-plan, appelé *moteur de tuple*, recherche chaque rowgroup fermé et le compresse dans le columnstore.  
  
 Pour chaque index columnstore cluster il peut y avoir plusieurs deltastores.  
  
-   Si un deltastore est verrouillé, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] essaie d'obtenir un verrou sur un autre deltastore. Si aucun deltastore n'est disponible, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée un nouveau deltastore.  
  
-   Une table partitionnée peut comprendre un ou plusieurs deltastores pour chaque partition.  
  
 Les scénarios suivants décrivent à quel moment les lignes chargées sont directement insérées dans le columnstore ou quand elles sont placées dans le deltastore.  
  
 Dans l'exemple, chaque rowgroup peut avoir 102 400-1 048 576 lignes par rowgroup. Dans la pratique, la taille maximale d’un rowgroup peut être inférieure à 1 048 576 lignes si la mémoire est très sollicitée.  
  
|Lignes à charger en masse|Lignes ajoutées au rowgroup compressé|Lignes ajoutées au rowgroup delta|  
|-----------------------|-------------------------------------------|--------------------------------------|  
|102 000|0|102 000|  
|145 000|145 000<br /><br /> Taille de rowgroup : 145 000|0|  
|1 048 577|1,048,576<br /><br /> Taille de rowgroup : 1 048 576|1|  
|2 252 152|2 252 152<br /><br /> Tailles de rowgroup : 1 048 576, 1 048 576, 155 000.|0|  
  
 L’exemple suivant montre les résultats du chargement de 1 048 577 lignes dans une table. Les résultats indiquent un rowgroup COMPRESSÉ dans le columnstore (comme segments de colonne compressés), et 1 ligne dans le deltastore.  
  
```  
SELECT object_id, index_id, partition_number, row_group_id, delta_store_hobt_id, state state_desc, total_rows, deleted_rows, size_in_bytes   
FROM sys.dm_db_column_store_row_group_physical_stats  
```  
  
 ![Rowgroup and deltastore for a batch load](../../relational-databases/indexes/media/sql-server-pdw-columnstore-batchload.gif "Rowgroup and deltastore for a batch load")  
  
## Charger à partir d’une table de mise en lots  
 Un modèle commun pour le chargement de données consiste à charger celles-ci dans une table de mise en lots, à effectuer une transformation, puis à charger celle-ci dans la table cible à l’aide de la commande suivante :  
  
```  
INSERT INTO <columnstore index>  SELECT <list of columns> FROM <Staging Table>  
  
```  
  
 Cette commande charge les données dans l’index columnstore de manière similaire à BCP ou à une insertion en bloc, mais dans un lot unique. Si le nombre de lignes de la table de mise en lots est inférieur à 102 400, les lignes sont chargées dans un rowgroup delta. Dans le cas contraire, elles sont chargées directement dans un rowgroup compressé.  Une limitation clé était que cette opération d’insertion était monothread. Pour charger des données en parallèle, vous pouviez créer plusieurs tables de mise en lots ou émettre des instructions INSERT/SELECT sans chevauchement des plages de lignes de la table de mise en lots.  Cette limitation disparaît avec SQL Server 2016. La commande suivante charge les données de la table de mise en lots en parallèle, mais vous devez spécifier l’option d'insertion en bloc TABLOCK.  
  
```  
INSERT INTO <columnstore index>  WITH (TABLOCK)  SELECT <list of columns> FROM <Staging Table>  
```  
  
 Les optimisations disponibles lors du chargement dans un index columnstore cluster à partir d’une table de mise en lots sont les suivantes :  
  
-   Optimisation du journal : journalisation minimale lors du chargement de données dans le rowgroup compressé. Aucune journalisation minimale lorsque des données sont chargées dans le rowgroup delta.  
  
-   Optimisation du verrouillage : lors du chargement dans rowgroup compressé, le verrou X sur le rowgroup est acquis. Toutefois, avec un rowgroup delta, un verrou X est acquis au niveau du rowgroup, mais SQL Server continue de verrouiller les verrous PAGE/EXTENT, car le verrou X du rowgroup ne fait pas partie de la hiérarchie de verrouillage.  
  
 Si vous disposez d’un ou plusieurs index non cluster, aucune optimisation du verrouillage ou du journal n’est effectuée pour l’index proprement dit, mais les optimisations de l’index columnstore cluster décrites ci-dessus ont toujours lieu.  
  
## Charger avec une insertion segmentée  
 L’*insertion segmentée* fait référence à la façon dont les lignes sont chargés dans le columnstore à l’aide de la commande INSERT INTO. Chaque ligne est ajoutée à un rowgroup delta. Les lignes entrantes sont directement placées dans un rowgroup deltastore, où elles s’accumulent jusqu’à ce que le rowgroup soit fermé après avoir atteint la limite de 1 048 576 lignes, ou jusqu’à la régénération de l’index columnstore.  
  
```  
INSERT INTO <table-name> VALUES (<set of values>)  
```  
  
 Notez que des threads simultanés utilisant la commande INSERT INTO pour insérer des valeurs dans un index columnstore cluster peuvent insérer des lignes dans le même rowgroup deltastore.  
  
 Lorsque le rowgroup contient 1 048 576 lignes, le rowgroup delta est marqué comme fermé, tout en restant disponible pour les requêtes et les opérations de mise à jour/suppression. En revanche, les lignes récemment insérées passent dans un rowgroup deltastore existant ou nouvellement créé. Un thread d’arrière-plan, *moteur de tuple*, compresse les rowgroups delta fermés environ toutes les 5 minutes. Pour compresser le rowgroup delta fermé, vous pouvez appeler explicitement la commande suivante :  
  
```  
ALTER INDEX <index-name> on <table-name> REORGANIZE  
```  
  
 Si vous souhaitez forcer un rowgroup delta fermé et compressé, vous pouvez exécuter la commande suivante. Vous pouvez exécuter cette commande si vous avez fini de charger les lignes et n’en attendez pas de nouvelles. En fermant et compressant explicitement le rowgroup delta, vous pouvez augmenter la capacité de stockage et améliorer les performances de requête d’analyse. Il est recommandé d’appeler cette commande si vous ne prévoyez pas l’insertion de nouvelles lignes.  
  
```  
ALTER INDEX <index-name> on <table-name> REORGANIZE with (COMPRESS_ALL_ROW_GROUPS = ON)  
```  
  
## Charger dans une table partitionnée  
 Pour les données partitionnées, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affecte d'abord chaque ligne à une partition, puis effectue les opérations de columnstore sur les données dans la partition. Chaque partition a ses propres rowgroups et au moins un deltastore.  
  
## Charger dans une index columnstore non cluster  
 Pour une table rowstore comportant des données d’index columnstore non cluster, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] insère toujours les données dans la table de base. Les données ne sont jamais insérées directement dans l’index columnstore.  
  
## Voir aussi  
 [Guide des index columnstore](../Topic/Columnstore%20Indexes%20Guide.md)   
 [Synthèse des fonctionnalités des index columnstore en fonction des versions](../Topic/Columnstore%20Indexes%20Versioned%20Feature%20Summary.md)   
 [Performances des requêtes d’index columnstore](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [Prise en main de columnstore pour l’analytique opérationnelle en temps réel](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [Index columnstore pour l’entreposage des données](../Topic/Columnstore%20Indexes%20for%20Data%20Warehousing.md)   
 [Défragmentation des index columnstore](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
  