---
title: "Mise à jour des statistiques (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE STATISTICS
- UPDATE_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- updating statistics
- query optimization statistics [SQL Server], updating
- UPDATE STATISTICS statement
- statistical information [SQL Server], updating
ms.assetid: 919158f2-38d0-4f68-82ab-e1633bd0d308
caps.latest.revision: 74
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5a1b053ddc09876717f0fbf34b2d7c294988162f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="update-statistics-transact-sql"></a>UPDATE STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Met à jour les statistiques d'optimisation de requête d'une table ou d'une vue indexée. Par défaut, l’optimiseur de requête met à jour les statistiques selon les besoins pour améliorer le plan de requête ; Dans certains cas, vous pouvez améliorer les performances des requêtes à l’aide de UPDATE STATISTICS ou la procédure stockée [sp_updatestats](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md) pour mettre à jour des statistiques plus fréquemment que les mises à jour par défaut.  
  
 La mise à jour des statistiques est l'assurance que les requêtes sont compilées avec des statistiques à jour. Toutefois, la mise à jour des statistiques entraîne une recompilation des requêtes. À ce titre, il est déconseillé de mettre à jour les statistiques de façon trop régulière eu égard aux performances. Un compromis doit être trouvé entre le souhait d'améliorer les plans de requête et le temps nécessaire à la recompilation des requêtes. Ce compromis peut varier en fonction de votre application. UPDATE STATISTICS peut utiliser tempdb pour trier l’échantillon de lignes à des fins statistiques.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
UPDATE STATISTICS table_or_indexed_view_name   
    [   
        {   
            { index_or_statistics__name }  
          | ( { index_or_statistics_name } [ ,...n ] )   
                }  
    ]   
    [    WITH   
        [  
            FULLSCAN   
              [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
            | SAMPLE number { PERCENT | ROWS }   
              [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
            | RESAMPLE   
              [ ON PARTITIONS ( { <partition_number> | <range> } [, …n] ) ]  
            | <update_stats_stream_option> [ ,...n ]  
        ]   
        [ [ , ] [ ALL | COLUMNS | INDEX ]   
        [ [ , ] NORECOMPUTE ]   
        [ [ , ] INCREMENTAL = { ON | OFF } ]  
    ] ;  
  
<update_stats_stream_option> ::=  
    [ STATS_STREAM = stats_stream ]  
    [ ROWCOUNT = numeric_constant ]  
    [ PAGECOUNT = numeric_contant ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
UPDATE STATISTICS schema_name . ] table_name   
    [ ( { statistics_name | index_name } ) ]  
    [ WITH   
       {  
              FULLSCAN   
            | SAMPLE number PERCENT   
            | RESAMPLE   
        }  
    ]  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *table_or_indexed_view_name*  
 Est le nom de la table ou la vue indexée qui contient l’objet de statistiques.  
  
 *index_or_statistics_name*  
 Nom de l'index dont les statistiques doivent être mises à jour ou nom des statistiques à mettre à jour. Si *index_or_statistics_name* n’est pas spécifié, l’optimiseur de requête met à jour toutes les statistiques de la table ou vue indexée. Cela inclut les statistiques créées à l'aide de l'instruction CREATE STATISTICS, les statistiques de colonnes uniques créées lorsque AUTO_CREATE_STATISTICS a la valeur ON, ainsi que les statistiques créées pour les index.  
  
 Pour plus d’informations sur AUTO_CREATE_STATISTICS, consultez [Options ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md). Pour afficher tous les index d’une table ou une vue, vous pouvez utiliser [sp_helpindex](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md).  
  
 FULLSCAN  
 Calcule les statistiques en analysant toutes les lignes dans la table ou vue indexée. FULLSCAN et SAMPLE 100 PERCENT ont les mêmes résultats. Cette option ne peut pas être utilisée avec l'option SAMPLE.  
  
 EXEMPLE *nombre* {% | LIGNES}  
 Spécifie le pourcentage ou nombre de lignes approximatif dans la table ou vue indexée à utiliser par l'optimiseur de requête lors de la mise à jour des statistiques. Pour PERCENT, *nombre* peut être comprise entre 0 et 100 et des lignes, *nombre* peut être comprise entre 0 et le nombre total de lignes. Le pourcentage ou nombre de lignes réel échantillonné par l'optimiseur de requête peut ne pas correspondre au pourcentage ou nombre spécifié. Par exemple, l'optimiseur de requête analyse toutes les lignes d'une page de données.  
  
 SAMPLE est utile pour les cas spéciaux dans lesquels le plan de requête, basé sur l'échantillonnage par défaut, n'est pas optimal. Dans la plupart des situations, il n'est pas nécessaire de spécifier SAMPLE car l'optimiseur de requête utilise l'échantillonnage et détermine la taille d'échantillon statistiquement significative par défaut, comme requis pour créer des plans de requête de haute qualité. 
 
En commençant par [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], l’échantillonnage des données pour générer des statistiques s’effectue en parallèle, lors de l’utilisation du niveau de compatibilité 130, pour améliorer les performances de la collection de statistiques. L’optimiseur de requête utilise des statistiques d’échantillon parallèle, chaque fois qu’une taille de la table dépasse un certain seuil. 
   
 SAMPLE ne peut pas être utilisé avec l'option FULLSCAN. Lorsque ni SAMPLE ni FULLSCAN n'est spécifié, l'optimiseur de requête utilise les données échantillonnées et calcule la taille d'échantillon par défaut.  
  
 Il est déconseillé de spécifier 0 PERCENT ou 0 ROWS. Lorsque 0 PERCENT ou ROWS est spécifié, l'objet de statistiques est mis à jour mais ne contient pas de données de statistiques.  
  
 Pour la plupart des charges de travail, une analyse complète n’est pas obligatoire, et l’échantillonnage par défaut est suffisante.  
Toutefois, certaines charges de travail qui sont sensibles aux différents des distributions de données peuvent nécessiter une taille d’échantillon augmenté, ou même une analyse complète.  
Pour plus d’informations, consultez la [blog CSS SQL escalade Services](http://blogs.msdn.com/b/psssql/archive/2010/07/09/sampling-can-produce-less-accurate-statistics-if-the-data-is-not-evenly-distributed.aspx).  
  
 RESAMPLE  
 Met à jour chaque statistique à l'aide de son taux d'échantillonnage le plus récent.  
  
 L'utilisation de RESAMPLE peut entraîner une analyse complète de la table. Par exemple, les statistiques relatives aux index utilisent une analyse de table complète pour leur taux d'échantillonnage. Si aucune option d'échantillonnage (SAMPLE, FULLSCAN, RESAMPLE) n'est spécifiée, l'optimiseur de requête échantillonne les données et calcule la taille d'échantillon par défaut.  

PERSIST_SAMPLE_PERCENT = {ON | {OFF}  
Lorsque **ON**, les statistiques conservera le pourcentage d’échantillonnage défini pour les mises à jour qui ne spécifient pas explicitement un pourcentage d’échantillonnage. Lorsque **OFF**, pourcentage d’échantillonnage des statistiques sera réinitialisée à échantillonnage par défaut dans les mises à jour qui ne spécifient pas explicitement un pourcentage d’échantillonnage. La valeur par défaut est **OFF**. 
 
 > [!NOTE]
 > Si l’option AUTO_UPDATE_STATISTICS est exécutée, il utilise le pourcentage d’échantillonnage persistante si elle est disponible, ou utiliser le pourcentage d’échantillonnage par défaut dans le cas contraire.
 > RÉÉCHANTILLONNER comportement n’est pas affecté par cette option.
 
 > [!TIP] 
 > [DBCC SHOW_STATISTICS](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md) et [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md) exposer la valeur de pourcentage exemple persistante pour la statistique sélectionnée.
 
 **S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4.  
 
 SUR les PARTITIONS ({ \<partition_number > | \<plage >} [,... n]) ] Force les statistiques de niveau feuille couvrant les partitions spécifiées dans la clause ON PARTITIONS être recalculé et ensuite fusionnés pour générer des statistiques globales. WITH RESAMPLE est nécessaire car les statistiques de partitions créées avec différents taux d'échantillonnage ne peuvent pas être fusionnées ensemble.  
  
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 ALL | COLUMNS | INDEX  
 Met à jour toutes les statistiques existantes, les statistiques créées sur une ou plusieurs colonnes, ou les statistiques créées pour les index. Si aucune option n'est spécifiée, l'instruction UPDATE STATISTICS met à jour toutes les statistiques de la table ou vue indexée.  
  
 NORECOMPUTE  
 Désactive l'option de mise à jour automatique des statistiques, AUTO_UPDATE_STATISTICS, pour les statistiques spécifiées. Si cette option est spécifiée, l'optimiseur de requête effectue cette mise à jour des statistiques et désactive les mises à jour ultérieures.  
  
 Pour réactiver le comportement de l’option AUTO_UPDATE_STATISTICS, réexécutez UPDATE STATISTICS sans l’option NORECOMPUTE ou exécutez **sp_autostats**.  
  
> [!WARNING]  
>  L'utilisation de cette option peut produire des plans de requête non optimaux. Nous recommandons d'utiliser cette option avec parcimonie et uniquement par un administrateur système qualifié.  
  
 Pour plus d’informations sur l’option AUTO_UPDATE_STATISTICS, consultez [Options ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 INCREMENTAL = { ON | OFF }  
 Lorsque **ON**, les statistiques sont recréées conformément aux statistiques de partition. Lorsque **OFF**, l’arborescence des statistiques est supprimée et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recalcule les statistiques. La valeur par défaut est **OFF**.  
  
 Si les statistiques par partition ne sont pas prises en charge, une erreur est générée. Les statistiques incrémentielles ne sont pas prises en charge pour les types de statistiques suivants :  
  
-   statistiques créées avec des index qui ne sont pas alignés sur les partitions avec la table de base ;  
  
-   statistiques créées sur les bases de données secondaires lisibles Always On ;  
  
-   statistiques créées sur les bases de données en lecture seule ;  
  
-   statistiques créées sur les index filtrés ;  
  
-   statistiques créées sur les vues ;  
  
-   statistiques créées sur les tables internes ;  
  
-   Statistiques créées avec les index spatiaux ou les index XML.  
  
**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 \<update_stats_stream_option >[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="remarks"></a>Notes  
  
## <a name="when-to-use-update-statistics"></a>Quand utiliser UPDATE STATISTICS  
 Pour plus d’informations sur l’utilisation des statistiques de mise à jour, consultez [statistiques](../../relational-databases/statistics/statistics.md).  
  
## <a name="updating-all-statistics-with-spupdatestats"></a>Mise à jour de toutes les statistiques avec sp_updatestats  
 Pour plus d’informations sur la mise à jour des statistiques pour toutes les tables définies par l’utilisateur et les tables internes de la base de données, consultez la procédure stockée [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md). Par exemple, la commande suivante appelle sp_updatestats pour mettre à jour toutes les statistiques de la base de données.  
  
```t-sql  
EXEC sp_updatestats;  
```  
  
## <a name="determining-the-last-statistics-update"></a>Détermination de la dernière mise à jour des statistiques  
 Pour déterminer la date de la dernière mise à jour des statistiques, utilisez la fonction [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md) .  
  
## <a name="pdw--sql-data-warehouse"></a>PDW / de l’entrepôt de données SQL  
 La syntaxe suivante n’est pas pris en charge par PDW / de l’entrepôt de données SQL  
  
```t-sql  
update statistics t1 (a,b);   
```  
  
```t-sql  
update statistics t1 (a) with sample 10 rows;  
```  
  
```t-sql  
update statistics t1 (a) with NORECOMPUTE;  
```  
  
```t-sql  
update statistics t1 (a) with INCREMENTAL=ON;  
```  
  
```t-sql  
update statistics t1 (a) with stats_stream = 0x01;  
```  
  
## <a name="permissions"></a>Permissions  
 Nécessite une autorisation ALTER sur la table ou la vue.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-update-all-statistics-on-a-table"></a>A. Mettre à jour toutes les statistiques d'une table  
 L’exemple suivant met à jour les statistiques pour tous les index sur les `SalesOrderDetail` table.  
  
```t-sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Sales.SalesOrderDetail;  
GO  
```  
  
### <a name="b-update-the-statistics-for-an-index"></a>B. Mettre à jour les statistiques d'un index  
 L'exemple suivant illustre la mise à jour des statistiques pour l'index `AK_SalesOrderDetail_rowguid` de la table `SalesOrderDetail`.  
  
```t-sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;  
GO  
```  
  
### <a name="c-update-statistics-by-using-50-percent-sampling"></a>C. Mettre à jour des statistiques avec un échantillonnage de 50 pour cent  
 L'exemple suivant crée, puis met à jour les statistiques des colonnes `Name` et `ProductNumber` de la table `Product`.  
  
```t-sql  
USE AdventureWorks2012;  
GO  
CREATE STATISTICS Products  
    ON Production.Product ([Name], ProductNumber)  
    WITH SAMPLE 50 PERCENT  
-- Time passes. The UPDATE STATISTICS statement is then executed.  
UPDATE STATISTICS Production.Product(Products)   
    WITH SAMPLE 50 PERCENT;  
```  
  
### <a name="d-update-statistics-by-using-fullscan-and-norecompute"></a>D. Mettre à jour des statistiques avec FULLSCAN et NORECOMPUTE  
 L'exemple suivant met à jour les statistiques de `Products` dans la table `Product`, force l'analyse complète de toutes les lignes de la table `Product` et désactive la mise à jour automatique des statistiques pour les statistiques de `Products`.  
  
```t-sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Production.Product(Products)  
    WITH FULLSCAN, NORECOMPUTE;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-update-statistics-on-a-table"></a>E. Mettre à jour les statistiques d’une table  
 L’exemple suivant met à jour la `CustomerStats1` des statistiques sur les `Customer` table.  
  
```t-sql  
UPDATE STATISTICS Customer ( CustomerStats1 );  
```  
  
### <a name="f-update-statistics-by-using-a-full-scan"></a>F. Mettre à jour des statistiques à l’aide d’une analyse complète  
 L’exemple suivant met à jour la `CustomerStats1` des statistiques, en fonction de l’analyse de toutes les lignes dans la `Customer` table.  
  
```t-sql  
UPDATE STATISTICS Customer (CustomerStats1) WITH FULLSCAN;  
```  
  
### <a name="g-update-all-statistics-on-a-table"></a>G. Mettre à jour toutes les statistiques d'une table  
 L’exemple suivant met à jour toutes les statistiques sur les `Customer` table.  
  
```t-sql  
UPDATE STATISTICS Customer;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Statistiques](../../relational-databases/statistics/statistics.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)   
 [STATS_DATE &#40; Transact-SQL &#41;](../../t-sql/functions/stats-date-transact-sql.md)  
 [Sys.dm_db_stats_properties &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)
  
  




