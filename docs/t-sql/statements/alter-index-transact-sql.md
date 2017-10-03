---
title: ALTER INDEX (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER INDEX
- ALTER_INDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- indexes [SQL Server], reorganizing
- ALTER INDEX statement
- indexes [SQL Server], disabling
- online index operations
- index reorganization [SQL Server]
- ALLOW_ROW_LOCKS option
- ALL keyword
- reorganizing indexes
- constraints [SQL Server], indexes
- row locks [SQL Server]
- index rebuilding [SQL Server]
- rebuilding indexes
- locking [SQL Server], indexes
- partitioned indexes [SQL Server], rebuilding
- defragmenting indexes
- disabling indexes
- XML indexes [SQL Server], modifying
- index modifications [SQL Server]
- indexes [SQL Server], modifying
- index options [SQL Server]
- modifying indexes
- index disabling [SQL Server]
- MAXDOP index option, ALTER INDEX statement
- spatial indexes [SQL Server], modifying
- indexes [SQL Server], options
- ALLOW_PAGE_LOCKS option
- page locks [SQL Server]
ms.assetid: b796c829-ef3a-405c-a784-48286d4fb2b9
caps.latest.revision: 222
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: f61b6469e40ba303cbff14db9bde15161b225ca7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="alter-index-transact-sql"></a>ALTER INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Modifie une table ou un index de vue (relationnel ou XML) en désactivant, en reconstruisant ou en réorganisant l'index d'une part, ou en définissant les options portant sur l'index d'autre part.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and SQL Database
  
ALTER INDEX { index_name | ALL } ON <object>  
{  
      REBUILD {  
            [ PARTITION = ALL ] [ WITH ( <rebuild_index_option> [ ,...n ] ) ]   
          | [ PARTITION = partition_number [ WITH ( <single_partition_rebuild_index_option> ) [ ,...n ] ]  
      }  
    | DISABLE  
    | REORGANIZE  [ PARTITION = partition_number ] [ WITH ( <reorganize_option>  ) ]  
    | SET ( <set_index_option> [ ,...n ] )   
    | RESUME [WITH (<resumable_index_options>,[…n])]
    | PAUSE
    | ABORT
}  
[ ; ]  
  
<object> ::=   
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_or_view_name  
}  
  
<rebuild_index_option > ::=  
{  
      PAD_INDEX = { ON | OFF }  
    | FILLFACTOR = fillfactor   
    | SORT_IN_TEMPDB = { ON | OFF }  
    | IGNORE_DUP_KEY = { ON | OFF }  
    | STATISTICS_NORECOMPUTE = { ON | OFF }  
    | STATISTICS_INCREMENTAL = { ON | OFF }  
    | ONLINE = {   
          ON [ ( <low_priority_lock_wait> ) ]   
        | OFF } 
    | RESUMABLE = { ON | OFF } 
    | MAX_DURATION = <time> [MINUTES}     
    | ALLOW_ROW_LOCKS = { ON | OFF }  
    | ALLOW_PAGE_LOCKS = { ON | OFF }  
    | MAXDOP = max_degree_of_parallelism  
    | COMPRESSION_DELAY = {0 | delay [Minutes]}  
    | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }   
        [ ON PARTITIONS ( {<partition_number> [ TO <partition_number>] } [ , ...n ] ) ]  
}  
  
<single_partition_rebuild_index_option> ::=  
{  
      SORT_IN_TEMPDB = { ON | OFF }  
    | MAXDOP = max_degree_of_parallelism  
    | RESUMABLE = { ON | OFF } 
    | MAX_DURATION = <time> [MINUTES}     
    | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE} }  
    | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<reorganize_option>::=  
{  
       LOB_COMPACTION = { ON | OFF }  
    |  COMPRESS_ALL_ROW_GROUPS =  { ON | OFF}  
}  
  
<set_index_option>::=  
{  
      ALLOW_ROW_LOCKS = { ON | OFF }  
    | ALLOW_PAGE_LOCKS = { ON | OFF }  
    | IGNORE_DUP_KEY = { ON | OFF }  
    | STATISTICS_NORECOMPUTE = { ON | OFF }  
    | COMPRESSION_DELAY= {0 | delay [Minutes]}  
}  

<resumable_index_option> ::=
 { 
    MAXDOP = max_degree_of_parallelism
    | MAX_DURATION =<time> [MINUTES]
    | <low_priority_lock_wait>  
 }
 
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ] ,   
                          ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )  
}  

```  
  
```  
-- Syntax for SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER INDEX { index_name | ALL }  
    ON   [ schema_name. ] table_name  
{  
      REBUILD {  
            [ PARTITION = ALL [ WITH ( <rebuild_index_option> ) ] ] 
          | [ PARTITION = partition_number [ WITH ( <single_partition_rebuild_index_option> )] ] 
      }  
    | DISABLE  
    | REORGANIZE [ PARTITION = partition_number ]  
}  
[;]  

<rebuild_index_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }
        [ ON PARTITIONS ( {<partition_number> [ TO <partition_number>] } [ , ...n ] ) ]   
}

<single_partition_rebuild_index_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
}  
  
```    
## <a name="arguments"></a>Arguments  
 *index_name*  
 Nom de l'index. Les noms d'index doivent être uniques dans une table ou une vue, mais ne doivent pas être nécessairement uniques dans une base de données. Les noms d’index doivent respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md).  
  
 ALL  
 Indique tous les index associés à une table ou à une vue indépendamment du type d'index. L'ajout de l'option ALL provoque un échec de l'instruction si des index se trouvent dans un groupe de fichiers hors connexion ou en lecture seule ou si l'opération spécifiée n'est pas autorisée sur certains types d'index. Le tableau suivant répertorie les types d'opérations ainsi que les types d'index non autorisés.  
  
|À l’aide du mot clé ALL avec cette opération|Entraîne un échec si la table possède des|  
|----------------------------------------|----------------------------------------|  
|REBUILD WITH ONLINE = ON|Index XML<br /><br /> Index spatial<br /><br /> Index ColumnStore : **s’applique à :** SQL Server (à partir de SQL Server 2012) et la base de données SQL Azure.|  
|REBUILD PARTITION = *partition_number*|Index non partitionné, index XML, index spatial ou index désactivé|  
|REORGANIZE|Index pour lesquels ALLOW_PAGE_LOCKS a la valeur OFF|  
|RÉORGANISER une PARTITION = *partition_number*|Index non partitionné, index XML, index spatial ou index désactivé|  
|IGNORE_DUP_KEY = ON|Index XML<br /><br /> Index spatial<br /><br /> Index ColumnStore : **s’applique à :** SQL Server (à partir de SQL Server 2012) et la base de données SQL Azure.|  
|ONLINE = ON|Index XML<br /><br /> Index spatial<br /><br /> Index ColumnStore : **s’applique à :** SQL Server (à partir de SQL Server 2012) et la base de données SQL Azure.|
| PEUT ÊTRE REPRIS = ON  | Non pris en charge avec les index peut être repris **tous les** (mot clé). <br /><br /> **S’applique à**: à partir de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique) |   
  
> [!WARNING]
>  Pour plus d’informations sur les opérations d’index qui peuvent être effectuées en ligne, consultez [instructions pour les opérations d’Index en ligne](../../relational-databases/indexes/guidelines-for-online-index-operations.md).

 Si ALL est spécifié avec PARTITION = *partition_number*, tous les index doivent être alignées. Ceci revient à les partitionner d'après des fonctions de partition équivalentes. À l’aide de ALL avec PARTITION entraîne toutes les partitions d’index avec le même *partition_number* à reconstruire ou réorganiser. Pour plus d'informations sur les index partitionnés, consultez [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
 *database_name*  
 Nom de la base de données.  
  
 *schema_name*  
 Nom du schéma auquel la table ou la vue appartient.  
  
 *nom_table_ou_vue*  
 Nom de la table ou de la vue associée à l'index. Pour afficher un rapport des index sur un objet, utilisez le [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vue de catalogue.  
  
 Base de données SQL prend en charge le nom_base_de_données de format de nom en trois parties. [nom_schéma] .nom_table_ou_vue lorsque nom_bd est la base de données actuelle ou nom_bd est tempdb et nom_table_ou_vue commence par #.  
  
 RECONSTRUIRE [WITH **(**\<rebuild_index_option > [ **,**... *n*]**)** ]  
 Index à reconstruire d'après les mêmes colonnes, le même type d'index, le même attribut assurant son unicité ainsi que le même ordre de tri. Cette clause équivaut à [DBCC DBREINDEX](../../t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md). REBUILD permet de réactiver un index désactivé. La reconstruction portant sur un index cluster n'entraîne pas celle des index non cluster associés, à moins que le mot clé ALL ne soit spécifié. Si les options d’index ne sont pas spécifiées, l’index existant option des valeurs stockées dans [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) sont appliquées. Des options d’index dont la valeur n’est pas stockée dans **sys.indexes**, la valeur par défaut indiquée dans la définition de l’argument de l’option s’applique.  
  
 Si l'option ALL est indiquée et que la table sous-jacente correspond à un segment de mémoire, l'opération de reconstruction n'a alors aucun effet sur la table. Tous les index non cluster associés à la table sont donc reconstruits.  
  
 L'opération de reconstruction peut être consignée dans un journal au minimum si le mode de récupération de base de données est défini sur Utilisant les journaux de transactions ou sur Simple.  
  
> [!NOTE]
>  Si vous reconstruisez un index XML primaire, la table utilisateur sous-jacente devient indisponible pour toute la durée de l'opération d'index.  
  
**S’applique à**: SQL Server (à partir de SQL Server 2012) et la base de données SQL Azure.
  
 Pour les index columnstore, l’opération de reconstruction :  
  
1.  N’utilise pas l’ordre de tri.  
  
2.  Acquiert un verrou exclusif sur la table ou la partition lorsque la reconstruction se produit.  Les données sont hors connexion et indisponibles pendant la reconstruction, même si vous utilisez NOLOCK, RCSI ou SI.  
  
3.  Recompresse toutes les données dans le columnstore. Il existe deux copies de l'index columnstore pendant la reconstruction. Lorsque la reconstruction est terminée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprime l'index columnstore d'origine.  
  
 Pour plus d’informations sur la reconstruction d’index columnstore, consultez [défragmentation des index Columnstore -](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
PARTITION  

**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.  
  
 Indique que seule une partition d'un index doit être reconstruite ou réorganisée. PARTITION ne peut pas être spécifiée si *index_name* n’est pas un index partitionné.  
  
 PARTITION = ALL reconstruit toutes les partitions.  
  
> [!WARNING]
>  La création et la reconstruction des index non alignés sur une table contenant plus de 1 000 partitions sont possibles, mais ne sont pas prises en charge. Ces opérations peuvent entraîner une dégradation des performances ou une consommation de mémoire excessive. Nous vous recommandons d'utiliser uniquement des index alignés lorsque le nombre de partitions est supérieur à 1000.  
  
 *partition_number*  
   
**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.
  
 Numéro de partition d'un index partitionné à reconstruire ou à réorganiser. *partition_number* est une expression constante qui permettre référencer des variables. Cela inclut les fonctions ou variables de types définies par l'utilisateur et les fonctions définies par l'utilisateur, mais exclut l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. *partition_number* doit exister ou l’instruction échoue.  
  
 AVEC **(**\<single_partition_rebuild_index_option >**)**  
   
**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.  
  
 Option SORT_IN_TEMPDB, MAXDOP et DATA_COMPRESSION sont les options qui peuvent être spécifiées quand vous régénérez une seule partition (PARTITION =  *n* ). Les index XML ne peuvent pas être indiqués dans une opération de reconstruction d'une seule partition.  
  
 DISABLE  
 Marque l'index comme désactivé et non disponible pour être utilisé par le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Tout index peut être désactivé. La définition d'un index désactivé est conservé dans le catalogue système sans y inclure de données sous-jacentes. Désactiver un index cluster permet d'éviter l'accès aux données de la table sous-jacente par les utilisateurs. Pour activer un index, utilisez ALTER INDEX REBUILD ou CREATE INDEX WITH DROP_EXISTING. Pour plus d’informations, consultez [désactiver des index et contraintes](../../relational-databases/indexes/disable-indexes-and-constraints.md) et [Enable Indexes and Constraints](../../relational-databases/indexes/enable-indexes-and-constraints.md).  
  
 RÉORGANISER un index rowstore  
 Pour les index rowstore, RÉORGANISER spécifie pour réorganiser le niveau feuille d’index.  L’opération de réorganisation est la suivante :  
  
-   Toujours effectuées en ligne. En d'autres termes, les verrous de tables bloquants à long terme ne sont pas conservés, ce qui permet aux requêtes et aux mises à jour de la table sous-jacente de se poursuivre pendant la transaction ALTER INDEX REORGANIZE.  
  
-   Pas autorisé pour un index désactivé  
  
-   Pas autorisé lorsque ALLOW_PAGE_LOCKS est définie sur OFF  
  
-   Pas restauré lorsqu’elle est exécutée dans une transaction et la transaction est restaurée.  
  
RÉORGANISER AVEC **(** LOB_COMPACTION = { **ON** | {OFF} **)**  
 S’applique aux index rowstore.  
  
LOB_COMPACTION = ON  
  
-   Spécifie pour compresser toutes les pages qui contiennent des données de ces types de données LOB (large object) : image, text, ntext, varchar (max), nvarchar (max), varbinary (max) et xml. Compactage de ces données peut réduire la taille des données sur le disque.  
  
-   Pour un index cluster, il compacte toutes les colonnes LOB qui sont contenus dans la table.  
  
-   Pour un index non ordonné en clusters, il compacte toutes les colonnes LOB qui sont des colonnes non-clés (incluses) dans l’index.  
  
-   RÉORGANISER tout effectue LOB_COMPACTION sur tous les index. Pour chaque index, il compacte toutes les colonnes LOB dans l’index cluster, table sous-jacente ou des colonnes incluses dans un index non cluster.  
  
LOB_COMPACTION = DÉSACTIVÉ  
  
-   Les pages contenant des données d'objet volumineux ne sont pas compactées.  
  
-   La valeur OFF n'a aucun effet sur un segment de mémoire.  
  
RÉORGANISEZ un index columnstore  
RÉORGANISATION est effectuée en ligne.  
  
Pour les index columnstore, RÉORGANISER compresse chaque rowgroup delta fermé dans le columnstore en tant qu’un rowgroup compressé.  
  
-   REORGANIZE n’est pas nécessaire pour déplacer les rowgroups delta fermés dans des rowgroups compressés. Le processus de déplacement de tuple (TM) en arrière-plan se réveille régulièrement pour compresser les rowgroups delta fermés. Nous vous recommandons d’utiliser REORGANIZE lorsque le moteur de tuple est en retard. REORGANIZE permet de compresser rowgroups plus efficacement.  
  
-   Pour compresser tous les rowgroups ouvert et fermé, consultez l’option REORGANIZE avec (COMPRESS_ALL_ROW_GROUPS) dans cette section.  
  
Pour les index columnstore dans SQL Server (à partir de 2016) et de la base de données SQL, REORGANIZE effectue des optimisations suivantes de défragmentation supplémentaires en ligne :  
  
-   Supprime physiquement les lignes d’un groupe de lignes lorsqu’au moins 10 % des lignes ont été logiquement supprimées. Les octets supprimés sont récupérés sur le support physique. Par exemple, si un groupe de lignes compressé de 1 million de lignes a 100 Ko les lignes supprimées, SQL Server supprime les lignes supprimées et recompresser le rowgroup avec 900 lignes k. Elle enregistre sur le stockage en supprimant les lignes supprimées.  
  
-   Associe un ou plusieurs groupes de lignes compressés pour augmenter les lignes par rowgroup jusqu'à la limite maximale de 1,024,576 lignes. Par exemple, si vous importez en bloc 5 lots de 102 400 lignes, vous obtiendrez des rowgroups compressés 5. Si vous exécutez REORGANIZE, ces rowgroups sera sont fusionnés dans un rowgroup compressé 1 de taille 512 000 lignes. Cela suppose que ne existait aucun dictionnaire de limitations de taille ou de la mémoire.  
  
-   Pour les rowgroups dans laquelle au moins 10 % des lignes ont été logiquement supprimé, SQL Server va tenter d’associer ce groupe de lignes avec un ou plusieurs groupes de lignes.    Par exemple, 1 de rowgroup est compressé avec 500 000 lignes et 21 de rowgroup est compressé avec la valeur maximale de 1 048 576 lignes.  Rowgroup 21 a 60 % des lignes supprimées qui laisse 409,830 lignes. SQL Server favorise la combinaison de ces deux groupes de lignes pour compresser un nouveau rowgroup qui a des 909,830 lignes.  
  
RÉORGANISER AVEC (COMPRESS_ALL_ROW_GROUPS = {ON | **OFF** })  
 Dans SQL Server (à partir de 2016) et la base de données SQL, le COMPRESS_ALL_ROW_GROUPS offre un moyen pour les rowgroups delta ouvert ou fermé dans le columnstore. Avec cette option, il n’est pas nécessaire de reconstruire l’index pour vider les rowgroups delta.  Ceci, combiné avec les autres supprimer et fusion défragmentation fonctionnalités fait il n’est plus nécessaire de reconstruire l’index dans la plupart des situations.    
-   ON force tous les rowgroups dans le columnstore, quelle que soit la taille et l’état (fermées ou ouvertes).  
  
-   DÉSACTIVER force tous les rowgroups fermés dans le columnstore.  
  
Définissez **(** \<set_index option > [ **,**... *n*] **)**  
 Indique des options d'index sans pour autant reconstruire ou réorganiser l'index. SET ne peut pas être spécifié pour un index désactivé.  
  
PAD_INDEX = { ON | OFF }  
   
**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.  
  
 Spécifie le remplissage de l'index. La valeur par défaut est OFF.  
  
 ON  
 Le pourcentage d'espace libre indiqué par FILLFACTOR est appliqué aux pages de niveau intermédiaire de l'index. Si FILLFACTOR n’est pas spécifié en même temps PAD_INDEX est définie sur ON, valeur stockée dans du facteur de remplissage [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) est utilisé.  
  
 DÉSACTIVER ou *fillfactor* n’est pas spécifié  
 Les pages de niveau intermédiaire sont remplies jusqu'à la presque totalité de la capacité. Cela laisse suffisamment d'espace libre pour au moins une ligne de la taille maximale que l'index peut occuper, d'après un ensemble de clés sur les pages intermédiaires.  
  
 Pour plus d’informations, consultez [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
FILLFACTOR = *facteur de remplissage*  
 
 **S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.
  
 Spécifie un pourcentage indiquant le taux de remplissage appliqué par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] au niveau feuille de chaque page d'index lors de la création ou de la modification de l'index. *facteur de remplissage* doit être un entier compris entre 1 et 100. La valeur par défaut est 0. Les taux de remplissage 0 et 100 sont identiques en tous points.  
  
 Un paramètre FILLFACTOR explicite ne s'applique que lors de la première création ou reconstruction de l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne conserve pas dynamiquement dans les pages le pourcentage d'espace libre défini. Pour plus d’informations, consultez [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
 Pour afficher le paramètre du facteur de remplissage, utilisez **sys.indexes**.  
  
> [!IMPORTANT]
>  La création ou la modification d'un index cluster avec une valeur de FILLFACTOR affecte la quantité de l'espace de stockage occupé par les données, car le [!INCLUDE[ssDE](../../includes/ssde-md.md)] redistribue les données lorsqu'il crée l'index en question.  
  
 SORT_IN_TEMPDB = {ON | **OFF** }  
 

**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.  
  
 Spécifie s’il faut stocker les résultats de tri dans **tempdb**. La valeur par défaut est OFF.  
  
 ON  
 Les résultats de tri intermédiaires qui sont utilisés pour créer l’index sont stockés dans **tempdb**. Si **tempdb** est un ensemble de disques que la base de données utilisateur, cela peut réduire le temps nécessaire pour créer un index. Toutefois, une plus grande quantité d'espace disque est alors utilisée lors de la création de l'index.  
  
 OFF  
 Les résultats de tri intermédiaires sont stockés dans la même base de données que l'index.  
  
 Si une opération de tri n'est pas requise ou si le tri peut s'effectuer en mémoire, l'option SORT_IN_TEMPDB est ignorée.  
  
 Pour plus d’informations, consultez [Option SORT_IN_TEMPDB pour les index](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md).  
  
 IGNORE_DUP_KEY  **=**  {ON | {OFF}  
 Spécifie la réponse d'erreur lorsqu'une opération d'insertion essaie d'insérer des valeurs de clés en double dans un index unique. L'option IGNORE_DUP_KEY s'applique uniquement aux opérations d'insertion après la création ou la régénération de l'index. La valeur par défaut est OFF.  
  
 ON  
 Un message d'avertissement s'affichera lorsque des valeurs de clé en double sont insérées dans un index unique. Seules les lignes qui violent la contrainte d'unicité échouent.  
  
 OFF  
 Un message d'erreur s'affichera lorsque des valeurs de clé en double sont insérées dans un index unique. L'intégralité de l'opération INSERT sera restaurée.  
  
 IGNORE_DUP_KEY ne peut pas être activée pour les index créés sur une vue, les index non uniques, les index XML, les index spatiaux et les index filtrés.  
  
 Pour afficher IGNORE_DUP_KEY, utilisez [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Dans la syntaxe de compatibilité descendante, WITH IGNORE_DUP_KEY est équivalent à WITH IGNORE_DUP_KEY = ON.  
  
 STATISTICS_NORECOMPUTE  **=**  {ON | {OFF}  
 Spécifie si les statistiques de distribution sont recalculées. La valeur par défaut est OFF.  
  
 ON  
 Les statistiques obsolètes ne sont pas recalculées automatiquement.  
  
 OFF  
 La mise à jour automatique des statistiques est activée.  
  
 Pour restaurer la mise à jour automatique des statistiques, affectez la valeur OFF à STATISTICS_NORECOMPUTE ou exécutez UPDATE STATISTICS sans la clause NORECOMPUTE.  
  
> [!IMPORTANT]
>  Si vous désactivez le recalcul automatique des statistiques de distribution, il se peut que cela empêche l'optimiseur de requête de choisir les plans d'exécution optimaux pour les requêtes impliquant la table.  
  
 STATISTICS_INCREMENTAL = {ON | **OFF** }  
 Lorsque **ON**, les statistiques sont créées par partition. Lorsque **OFF**, l’arborescence des statistiques est supprimée et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recalcule les statistiques. La valeur par défaut est **OFF**.  
  
 Si les statistiques par partition ne sont pas prises en charge, l'option est ignorée et un avertissement est généré. Les statistiques incrémentielles ne sont pas prises en charge pour les types de statistiques suivants :  
  
-   statistiques créées avec des index qui ne sont pas alignés sur les partitions avec la table de base ;  
  
-   statistiques créées sur les bases de données secondaires lisibles Always On ;  
  
-   statistiques créées sur les bases de données en lecture seule ;  
  
-   statistiques créées sur les index filtrés ;  
  
-   statistiques créées sur les vues ;  
  
-   statistiques créées sur les tables internes ;  
  
-   Statistiques créées avec les index spatiaux ou les index XML.  
  
 
**S’applique à**: SQL Server (à partir de SQL Server 2014) et la base de données SQL Azure.  
  
 En ligne  **=**  {ON | **OFF** } \<s’appliqu’à rebuild_index_option >  
 Indique si les tables sous-jacentes et les index associés sont disponibles pour les requêtes et la modification de données pendant l'opération d'index. La valeur par défaut est OFF.  
  
 Pour un index XML ou un index spatial, seul ONLINE = OFF est pris en charge et si ONLINE a la valeur ON, une erreur est générée.  
  
> [!NOTE]
>  Les opérations d’index en ligne ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ON  
 Les verrous de table à long terme ne sont pas maintenus pendant la durée de l'opération d'index. Lors de la principale phase de l'indexation, seul le verrou de partage intentionnel (IS, Intent Share) est maintenu sur la table source. Cela permet aux requêtes ou aux mises à jour effectuées dans la table et les index sous-jacents de continuer. Au début de l'opération, un verrou partagé (S, Shared) est très brièvement maintenu sur l'objet source. À la fin de l'opération, un verrou partagé (S) est très brièvement maintenu sur la source si un index non cluster est en cours de création ou bien un verrou SCH-M (Modification du schéma) est acquis lorsqu'un index cluster est créé ou supprimé en ligne ou lorsqu'un index cluster ou non cluster est en cours de reconstruction. ONLINE ne peut pas prendre la valeur ON si un index est en cours de création sur une table locale temporaire.  
  
 OFF  
 Des verrous de table sont appliqués pendant l'opération d'indexation. Une opération d'index hors connexion qui crée, reconstruit ou supprime un index cluster, spatial ou XML, ou qui reconstruit ou supprime un index non cluster, acquiert un verrou Sch-M (Modification du schéma) sur la table. Cela empêche tous les utilisateurs d'accéder à la table sous-jacente pendant la durée de l'opération. Une opération d'indexation hors ligne qui crée un index non cluster acquiert un verrou partagé (S, Shared) sur la table. Cela empêche la mise à jour de la table sous-jacente, mais autorise les opérations de lecture, telles que des instructions SELECT.  
  
 Pour plus d’informations, consultez [Online Index opérations fonctionnement](../../relational-databases/indexes/how-online-index-operations-work.md).  
  
 Les index, notamment les index portant sur des tables temporaires globales, ne peuvent pas être reconstruits en ligne, à l'exception des index suivants :  
  
-   Index XML  
  
-   index portant sur des tables temporaires locales ;  
  
-   sous-ensemble d'un index partitionné (un index partitionné entier peut être reconstruit en ligne).  

-  Base de données SQL antérieures à V12 et SQL Server antérieures à SQL Server 2012, ne permettent pas la `ONLINE` est définie sur la construction d’index en cluster ou de reconstruire les opérations lors de la table de base contient **varchar (max)** ou **varbinary (max)** colonnes.

PEUT ÊTRE REPRIS  **=**  {ON | **OFF**}

**S’applique à**: à partir de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique)  

 Spécifie si une opération d’index en ligne est peut être reprise.

 SUR l’Index de l’opération est peut être reprise.

 DÉSACTIVER l’Index de l’opération n’est pas pouvant être reprise.

MAX_DURATION  **=**  *temps* [**MINUTES**] utilisé avec **reprise = ON** (nécessite **ONLINE = ON**).
 
**S’applique à**: à partir de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique)  

Indique le temps (valeur entière spécifiée en minutes) qu’une reprise en ligne opération d’index est exécutée avant en pause. 

ALLOW_ROW_LOCKS  **=**  { **ON** | {OFF}  
 
**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.  
  
 Indique si les verrous de ligne sont autorisés ou non. La valeur par défaut est ON.  
  
 ON  
 Les verrous de ligne sont autorisés lors de l'accès à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] détermine le moment où les verrous de ligne sont utilisés.  
  
 OFF  
 Les verrous de ligne ne sont pas utilisés.  
  
ALLOW_PAGE_LOCKS  **=**  { **ON** | {OFF}  
  
**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.
  
 Indique si les verrous de page sont autorisés. La valeur par défaut est ON.  
  
 ON  
 Les verrous de page sont autorisés lors de l'accès à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] détermine le moment où les verrous de page sont utilisés.  
  
 OFF  
 Les verrous de page ne sont pas utilisés.  
  
> [!NOTE]
>  Un index ne peut pas être réorganisé lorsque ALLOW_PAGE_LOCKS est désactivé (OFF).  
  
 MAXDOP  **=**  max_degree_of_parallelism  
 
**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.  
  
 Remplace le **degré maximal de parallélisme** option de configuration pour la durée de l’opération d’index. Pour plus d’informations, consultez [Configurer l’option de configuration du serveur max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). Utilisez MAXDOP pour limiter le nombre de processeurs utilisés dans une exécution de plan parallèle. Le nombre maximal de processeurs est égal à 64.  
  
> [!IMPORTANT]
>  Bien que l'option MAXDOP soit prise en charge syntaxiquement pour tous les index XML, pour un index spatial ou un XML primaire, ALTER INDEX utilise actuellement seulement un processeur unique.  
  
 *max_degree_of_parallelism* peut être :  
  
 1  
 Supprime la création de plans parallèles.  
  
 \>1  
 Limite au nombre spécifié le nombre maximal de processeurs utilisés dans le traitement en parallèle des index.  
  
 0 (valeur par défaut)  
 Utilise le nombre réel de processeurs ou un nombre de processeurs inférieur en fonction de la charge de travail actuelle du système.  
  
 Pour plus d’informations, consultez [Configurer des opérations d’index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]
>  Opérations d’index parallèles ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 COMPRESSION_DELAY  **=**  { **0** |*durée [Minutes]* }  
 Cette fonctionnalité est disponible à partir de SQL Server 2016  
  
 Pour une table basée sur disque, délai Spécifie le nombre minimal de minutes pendant lesquelles qu'un rowgroup delta à l’état CLOSED doit rester dans le rowgroup delta avant que SQL Server peut compresser dans le rowgroup compressé. Étant donné que les tables sur disque ne suivre insérer et mettre à jour heures sur des lignes individuelles, SQL Server s’applique le délai d’attente pour les groupes de lignes delta à l’état CLOSED.  
La valeur par défaut est 0 minute.  
  
 La valeur par défaut est 0 minute.  
  
 Pour obtenir des recommandations sur l’utilisation de COMPRESSION_DELAY, voir les index Columnstore pour les Analytique opérationnelle en temps réel.  
  
 DATA_COMPRESSION  
 Spécifie l'option de compression de données pour l'index, le numéro de partition ou la plage de partitions spécifiés. Les options disponibles sont les suivantes :  
  
 Aucune  
 L'index ou les partitions spécifiées ne sont pas compressés. Ne s'applique pas aux index columnstore.  
  
 ROW  
 L'index ou les partitions spécifiées sont compressés au moyen de la compression de ligne. Ne s'applique pas aux index columnstore.  
  
 PAGE  
 L'index ou les partitions spécifiées sont compressés au moyen de la compression de page. Ne s'applique pas aux index columnstore.  
  
 COLUMNSTORE  
   
**S’applique à**: SQL Server (à partir de SQL Server 2014) et la base de données SQL Azure.
  
 S'applique uniquement aux index columnstore, y compris aux index columnstore non cluster et cluster. COLUMNSTORE spécifie qu'il faut décompresser l'index ou les partitions spécifiées compressés à l'aide de l'option COLUMNSTORE_ARCHIVE. Lorsque les données sont restaurées, elles continuent à être compressées à l'aide de la compression columnstore utilisée pour tous les index columnstore.  
  
 COLUMNSTORE_ARCHIVE  
  
**S’applique à**: SQL Server (à partir de SQL Server 2014) et la base de données SQL Azure.
  
 S'applique uniquement aux index columnstore, y compris aux index columnstore non cluster et cluster. COLUMNSTORE_ARCHIVE compressera davantage la partition spécifiée en une plus petite taille. Peut être utilisé pour l'archivage, ou d'autres situations qui nécessitent moins de stockage et supportent plus de temps pour le stockage et la récupération.  
  
 Pour plus d’informations sur la compression, consultez [la Compression des données](../../relational-databases/data-compression/data-compression.md).  
  
 SUR les PARTITIONS **(** { \<partition_number_expression > | \<plage >} [**,**... n] **)**  
    
**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure. 
  
 Spécifie les partitions auxquelles le paramètre DATA_COMPRESSION s'applique. Si l'index n'est pas partitionné, l'argument ON PARTITIONS générera une erreur. Si la clause ON PARTITIONS n'est pas fournie, l'option DATA_COMPRESSION s'applique à toutes les partitions d'un index partitionné.  
  
 \<partition_number_expression > peut être spécifié comme suit :  
  
-   Spécifiez le numéro d'une partition, par exemple : ON PARTITIONS (2).  
  
-   Spécifiez des numéros de partition pour plusieurs partitions individuelles séparées par des virgules, par exemple : ON PARTITIONS (1, 5).  
  
-   Spécifiez à la fois des plages et des partitions individuelles : ON PARTITIONS (2, 4, 6 TO 8).  
  
 \<plage > peut être spécifié en tant que numéros de partitions séparés par le mot TO, par exemple : ON PARTITIONS (6 TO 8).  
  
 Pour définir des types différents de compression de données pour des partitions différentes, spécifiez plusieurs fois l'option DATA_COMPRESSION, par exemple :  
  
```tsql  
REBUILD WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
);  
```  
  
 En ligne  **=**  {ON | **OFF** } \<s’appliqu’à single_partition_rebuild_index_option >  
 Spécifie si un index ou une partition d’index d’une table sous-jacente peut être reconstruite en ligne ou hors connexion. Si **reconstruire** est effectuée en ligne (**ON**) les données de cette table seront disponibles pour la modification de requêtes et des données pendant l’opération d’index.  La valeur par défaut est **OFF**.  
  
 ON  
 Les verrous de table à long terme ne sont pas maintenus pendant la durée de l'opération d'index. Lors de la principale phase de l'indexation, seul le verrou de partage intentionnel (IS, Intent Share) est maintenu sur la table source. Un verrou S sur la table est requis au début de la reconstruction d’index et un verrou Sch-M sur la table à la fin de la reconstruction d’index en ligne. Bien que les deux verrous soient des verrous de métadonnées courtes, le verrou Sch-M doit notamment attendre que toutes les transactions bloquantes soient terminées. Pendant le temps d'attente, le verrou Sch-M bloque toutes les autres transactions qui attendent derrière ce verrou en cas d'accès à la même table.  
  
> [!NOTE]
>  Reconstruction d’index en ligne peut définir le *low_priority_lock_wait* options décrites plus loin dans cette section.  
  
 OFF  
 Des verrous de table sont appliqués pendant l'opération d'indexation. Cela empêche tous les utilisateurs d'accéder à la table sous-jacente pendant la durée de l'opération.  
  
 WAIT_AT_LOW_PRIORITY utilisé avec **ONLINE = ON** uniquement.  
 
**S’applique à**: SQL Server (à partir de SQL Server 2014) et la base de données SQL Azure.
  
 Une reconstruction d'index en ligne doit attendre les opérations de blocage sur cette table. **WAIT_AT_LOW_PRIORITY** indique que l’opération de reconstruction d’index en ligne attend les verrouillages de faible priorité, laissant les autres opérations se poursuivre pendant l’opération de création d’index en ligne est en attente. L’omission de la **attente basse** option est équivalente à `WAIT_AT_LOW_PRIORITY (MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`. Pour plus d’informations, consultez [WAIT_AT_LOW_PRIORITY](alter-index-transact-sql.md). 
  
 MAX_DURATION = *temps* [**MINUTES**]  
  
**S’applique à**: SQL Server (à partir de SQL Server 2014) et la base de données SQL Azure.
  
 Temps d'attente (valeur entière spécifiée en minutes) pendant lequel les verrous de reconstruction d'index en ligne devront attendre avec une faible priorité lors de l'exécution de la commande DDL. Si l’opération est bloquée pendant la **MAX_DURATION** de temps, un de la **ABORT_AFTER_WAIT** actions seront exécutées. **MAX_DURATION** heure est toujours en minutes et le mot **MINUTES** peut être omis.  
 
 ABORT_AFTER_WAIT = [**NONE** | **SELF** | **DES BLOCAGES** }]  
   
**S’applique à**: SQL Server (à partir de SQL Server 2014) et la base de données SQL Azure.
  
 Aucune  
 Continuez à attendre le verrou avec la priorité normale.  
  
 SELF  
 Quittez l'opération DDL de reconstruction de l'index en ligne actuellement exécutée sans effectuer aucune action.  
  
 BLOCKERS  
 Annulez toutes les transactions utilisateur qui bloquent l'opération DDL de reconstruction de l'index en ligne afin que l'opération puisse continuer. Le **des blocages** option requiert la connexion ait **ALTER ANY CONNECTION** autorisation.  
 
 RESUME 
 
**S’applique à**: à partir de SQL Server 2017 est (fonctionnalité est en version préliminaire publique)

Reprendre une opération d’index est en pause manuellement ou en raison d’une défaillance.

MAX_DURATION est utilisé avec **reprise = ON**

 
**S’applique à**: à partir de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique)

L’heure (valeur entière spécifiée en minutes) de l’opération d’index en ligne peut être repris est exécutée après la reprise. Une fois que le délai expire, l’opération de reprise est suspendue si elle est en cours d’exécution.

WAIT_AT_LOW_PRIORITY utilisé avec **reprise = ON** et **ONLINE = ON**.  
  
**S’applique à**: à partir de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique)
  
 La reprise d’une reconstruction d’index en ligne après qu’une pause se trouve en attente pour les opérations de blocage sur cette table. **WAIT_AT_LOW_PRIORITY** indique que l’opération de reconstruction d’index en ligne attend les verrouillages de faible priorité, laissant les autres opérations se poursuivre pendant l’opération de création d’index en ligne est en attente. L’omission de la **attente basse** option est équivalente à `WAIT_AT_LOW_PRIORITY (MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`. Pour plus d’informations, consultez [WAIT_AT_LOW_PRIORITY](alter-index-transact-sql.md). 


PAUSE
 
**S’applique à**: à partir de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique)
  
Interrompre une opération de reconstruction d’index en ligne peut être repris.

ABANDON

**S’applique à**: à partir de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique)   

Abandonner une opération d’index en cours d’exécution ou en pause qui a été déclarée comme pouvant être reprise. Vous devez exécuter explicitement une **abandonner** opération de reconstruction de commande pour mettre fin à un index peut être repris. Échec ou la suspension d’une opération d’index peut être repris n’arrête pas son exécution ; au lieu de cela, elle laisse l’opération dans un état de pause indéterminée.
  
## <a name="remarks"></a>Notes  
 ALTER INDEX ne peut pas être utilisé pour recréer la partition d'un index ou le déplacer vers un autre groupe de fichiers. Cette instruction ne peut pas être utilisée pour modifier la définition de l'index, comme l'ajout ou la suppression de colonnes ou la modification de l'ordre des colonnes. Exécutez CREATE INDEX avec la clause DROP_EXISTING afin de procéder aux opérations suivantes.  
  
 Si une option n'est pas spécifiée de façon explicite, le paramètre actuel s'applique. Par exemple, si un paramètre FILLFACTOR n'est pas indiqué dans la clause REBUILD, la valeur de facteur de remplissage stockée dans le catalogue système est utilisée lors du processus de reconstruction. Pour afficher les paramètres de l’index en cours, utilisez [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
> [!NOTE]
>  Les valeurs pour les options ONLINE, MAXDOP et SORT_IN_TEMPDB ne sont pas stockées dans le catalogue système. À moins qu'elle ne soit précisée dans l'instruction d'index, la valeur par défaut de l'option est alors utilisée.
  
 Sur des ordinateurs multiprocesseurs, comme c'est aussi le cas pour d'autres requêtes, ALTER INDEX REBUILD utilise automatiquement plus de processeurs pour pouvoir procéder aux opérations d'analyse et de tri associées à la modification de l'index. Lorsque vous exécutez ALTER INDEX REORGANIZE, avec ou sans LOB_COMPACTION, la **degré maximal de parallélisme** valeur indique une opération mono-thread. Pour plus d’informations, consultez [Configurer des opérations d’index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
 Un index ne peut pas être réorganisé ou reconstruit si le groupe de fichiers dans lequel il se trouve est hors connexion ou en lecture seule. Si le mot clé ALL est spécifié et que des index se trouvent dans un groupe de fichiers hors connexion ou en lecture seule, l'instruction échoue.  
  
## <a name="rebuilding-indexes"></a>Reconstruction des index  
 La reconstruction d'un index entraîne sa suppression puis sa recréation. Ceci permet d'éviter toute fragmentation, de libérer de l'espace disque en compactant les pages d'après le paramètre du facteur de remplissage spécifié ou déjà existant et en retriant les lignes de l'index en pages contiguës. Quand ALL est précisé, tous les index sur la table sont supprimés puis reconstruits en une seule transaction. Il n'est pas nécessaire de supprimer les contraintes FOREIGN KEY au préalable. Lorsque de la reconstruction d'index contenant au moins 128 étendues, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] diffère les désallocations de pages ainsi que les verrous qui y sont associés jusqu'à ce que la transaction soit validée.  
  
 Bien souvent, la reconstruction ou la réorganisation de petits index ne réduit pas la fragmentation. Les pages de petits index sont parfois stockées sur des extensions mixtes. Les extensions mixtes sont partagées par huit objets maximum ; par conséquent, la fragmentation dans un petit index peut ne pas être réduite après sa réorganisation ou sa reconstruction.  
  
 À partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], les statistiques ne sont pas créées en analysant toutes les lignes de la table quand un index partitionné est créé ou reconstruit. Au lieu de cela, l'optimiseur de requête utilise l'algorithme d'échantillonnage par défaut pour générer des statistiques. Pour obtenir des statistiques sur les index partitionnés en analysant toutes les lignes de la table, utilisez CREATE STATISTICS ou UPDATE STATISTICS avec la clause FULLSCAN.  
  
 Dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous aviez parfois la possibilité de reconstruire un index non cluster afin de corriger les incohérences dues à des défaillances matérielles. Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures, vous pouvez toujours réparer de telles incohérences entre l'index et l'index cluster en reconstruisant un index non cluster hors connexion. Toutefois, vous ne pouvez pas réparer les incohérences d'un index non cluster en reconstruisant l'index en ligne. En effet, le mécanisme de reconstruction en ligne utilise l'index non cluster existant comme base pour la reconstruction et propage de ce fait l'incohérence. La reconstruction de l'index hors connexion peut parfois imposer une analyse de l'index cluster (ou segment de mémoire) et éliminer ainsi l'incohérence. Afin de garantir une reconstruction à partir de l'index cluster, supprimez et recréez l'index non cluster. Comme pour les versions précédentes, nous vous recommandons d'éliminer les incohérences en restaurant les données concernées à partir d'une sauvegarde. Toutefois, il est possible que vous puissiez réparer les incohérences d'un index en reconstruisant l'index non cluster hors connexion. Pour plus d’informations, consultez [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).  
  
 Pour reconstruire un index cluster columnstore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1.  Acquiert un verrou exclusif sur la table ou la partition lorsque la reconstruction se produit. Les données sont hors connexion et indisponibles pendant la reconstruction.  
  
2.  Défragmente le columnstore en supprimant physiquement les lignes qui ont été logiquement supprimées de la table ; les octets supprimés sont récupérés sur le support physique.  
  
3.  Lit toutes les données de l'index columnstore d'origine, y compris le deltastore. Associe les données dans de nouveaux rowgroups, et compresse les rowgroups dans le columnstore.  
  
4.  Nécessite de l'espace sur le support physiques pour stocker deux copies de l'index columnstore pendant que la reconstruction est en cours. Lorsque la reconstruction est terminée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprime l'index columnstore cluster d'origine.  
  
## <a name="reorganizing-indexes"></a>Réorganisation d'index  
 La réorganisation d'un index utilise des ressources système minimes. En effet, elle défragmente le niveau feuille des index cluster et non cluster sur les tables et les vues en retriant les pages de niveau feuille de façon physique afin de resuivre l'ordre logique, c'est-à-dire de gauche à droite, des nœuds. Cette opération compacte également les pages d'index. Le compactage s'appuie sur la valeur du facteur de remplissage existante. Pour afficher le paramètre du facteur de remplissage, utilisez [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Si ALL est précisé, les index relationnels, aussi bien cluster que non cluster, et les index XML sur la table sont réorganisés. Des restrictions s'appliquent néanmoins si vous utilisez l'option ALL ; consultez sa définition dans la section Arguments.  
  
 Pour plus d’informations, consultez [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
## <a name="disabling-indexes"></a>Désactivation d'index  
 Désactiver un index permet d'éviter l'accès à l'index, et dans le cas d'index cluster, aux données de la table sous-jacente par les utilisateurs. La définition de l'index est conservée dans le catalogue système. Désactiver un index, qu'il soit non cluster ou cluster, sur une vue supprime physiquement les données de l'index. Désactiver un index cluster permet d'éviter l'accès aux données mais celles-ci ne sont plus mises à jour dans l'arborescence binaire (appelé également arbre B) jusqu'à ce que l'index soit supprimé ou reconstruit. Pour afficher l’état d’un index activé ou désactivé, interrogez la **is_disabled** colonne dans la **sys.indexes** vue de catalogue.  
  
 Si une table est dans une publication de réplication transactionnelle, vous ne pouvez pas désactiver les index qui sont associés à des colonnes clés primaire. Ces index sont requis par la réplication. Pour désactiver un index, vous devez d'abord supprimer la table de la réplication. Pour plus d’informations, consultez [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
 Pour activer l'index, utilisez l'instruction ALTER INDEX REBUILD ou CREATE INDEX WITH DROP_EXISTING. La reconstruction d'un index cluster désactivé ne peut être effectuée si l'option ONLINE est activée (ON). Pour plus d’informations, consultez [Désactiver les index et contraintes](../../relational-databases/indexes/disable-indexes-and-constraints.md).  
  
## <a name="setting-options"></a>Configuration des options  
 Vous pouvez définir les options ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, IGNORE_DUP_KEY et STATISTICS_NORECOMPUTE pour un index précis sans pour autant avoir à le reconstruire ou le réorganiser. Les valeurs modifiées sont immédiatement appliquées à l'index. Pour afficher ces paramètres, utilisez **sys.indexes**. Pour plus d’informations, consultez [Définir les options d’index](../../relational-databases/indexes/set-index-options.md).  
  
### <a name="row-and-page-locks-options"></a>Options de verrous de ligne et de page  
 Si ALLOW_ROW_LOCKS = ON et ALLOW_PAGE_LOCK = ON, les verrous de ligne, de page et de table sont autorisés lorsque vous accédez à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] choisit le verrou approprié et peut promouvoir un verrou de ligne ou de page en verrou de table.  
  
 Si ALLOW_ROW_LOCKS = OFF et ALLOW_PAGE_LOCK = OFF, seul un verrou au niveau des tables est autorisé si vous accédez à l'index.  
  
 Si ALL est indiqué lors de la définition des options de verrouillage de ligne ou de page, les paramètres s'appliquent à tous les index. Si la table sous-jacente correspond à un segment de mémoire, les paramètres s'appliquent des façons suivantes :  
  
|||  
|-|-|  
|ALLOW_ROW_LOCKS = ON ou OFF|S'applique au segment de mémoire et à tout index non cluster qui lui est associé.|  
|ALLOW_PAGE_LOCKS = ON|S'applique au segment de mémoire et à tout index non cluster qui lui est associé.|  
|ALLOW_PAGE_LOCKS = OFF|Verrou entier pour les index non cluster. En d'autres termes, tous les verrous de page ne sont pas autorisés sur les index non cluster. En ce qui concerne le segment de mémoire, seul les verrous partagé (P), de mise à jour (M) et exclusifs (E) ne sont pas autorisés. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut toujours acquérir un verrou de page intentionnel (IS, IU ou IX) à des fins internes.|  
  
## <a name="online-index-operations"></a>Opérations d'index en ligne  
 Si vous reconstruisez un index et que l'option ONLINE est activée (ON), les objets, les tables et les index associés sous-jacents sont disponibles pour permettre les requêtes et la modification de données. Vous pouvez également reconstruire en ligne une partie d'un index résidant sur une partition unique. Les verrous de tables exclusifs ne sont maintenus que pour une durée courte lors du processus de modification.  
  
 La réorganisation d'un index s'effectue toujours en ligne. Elle ne conserve pas les verrous à long terme et ne bloque pas ainsi les requêtes ou les mises à jour en cours d'exécution.  
  
 Vous pouvez lancer des opérations d'index en ligne simultanées sur une même table ou partition de table, mais uniquement dans les cas suivants :  
  
-   Création de plusieurs index non cluster.  
  
-   réorganisation de différents index sur une même table ;  
  
-   réorganisation de différents index lors de la reconstruction d'index ne se chevauchant pas et portant sur une même table.  
  
 Toutes les autres opérations en ligne sur les index exécutées en même temps échouent. Par exemple, vous ne pouvez pas reconstruire de façon concurrente plusieurs index portant sur une même table ou créer d'index lors de la reconstruction d'un index existant portant sur la même table.  

### <a name="resumable-index-operations"></a>Opérations d’index pouvant être reprises

**S’applique à**: à partir de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique)

RECONSTRUCTION d’INDEX en ligne est spécifié comme pouvant être repris à l’aide de la reprise = option. 
-  L’option de reprise n’est pas conservée dans les métadonnées pour un index donné et s’applique uniquement à la durée d’une instruction DDL en cours. Par conséquent, la reprise = ON clause doit être spécifiée explicitement pour activer la fonction.

-  Notez les deux options MAX_DURATION. L’une est liée à low_priority_lock_wait et l’autre est liée à la reprise = option.
   -  Option MAX_DURATION est pris en charge pour la reprise = option ou **low_priority_lock_wait** option de l’argument. 
   MAX_DURATION pour l’option peut être reprise Spécifie l’intervalle de temps pour un index en cours de reconstruction. Une fois cette durée est utilisée, la reconstruction d’index est mise en pause ou il termine son exécution. Utilisateur décide quand une reconstruction d’un index en pause peut être reprise. Le **temps** en minutes pour MAX_DURATION doit être supérieure à 0 minute et inférieur ou égale une semaine (7 x 24 x 60 = 10080 minutes). Ayant une longue pause pour une opération d’index peut avoir un impact sur les performances DML sur une table spécifique, ainsi que la capacité du disque de base de données puisque les deux index d’origine et celui qui vient d’être créé d’espace disque et doivent être mis à jour au cours des opérations DML. Si l’option MAX_DURATION est omise, l’opération d’index se poursuivra jusqu'à son achèvement, ou jusqu'à ce qu’une défaillance se produit. 
-   Le \<low_priority_lock_wait > argument option vous permet de décider comment l’opération d’index peut continuer lorsque bloquée sur le verrou SCH-M.
 
-  Ré-exécution de l’instruction ALTER INDEX REBUILD d’origine avec les mêmes paramètres reprend une opération de reconstruction d’index en pause. Vous pouvez également reprendre une opération de reconstruction d’index en pause en exécutant l’instruction ALTER INDEX reprendre la.
-  L’option SORT_IN_TEMPDB = ON option n’est pas prise en charge pour les index pouvant être reprise 
-  La commande DDL avec reprise = ON ne peut pas être exécutée à l’intérieur d’une transaction explicite (ne peut pas faire partie de begin tran... bloc de validation).
-  Uniquement les opérations d’index qui sont suspendues sont peut être reprises.
-   Lors de la reprise d’une opération d’index est en pause, vous pouvez modifier la valeur MAXDOP une nouvelle valeur.  Si MAXDOP n’est pas spécifiée lors de la reprise d’une opération d’index qui est suspendue, la dernière valeur MAXDOP est effectuée. Si l’option MAXDOP n’est pas du tout spécifiée pour l’opération de reconstruction d’index, la valeur par défaut est effectuée.
- Pour suspendre immédiatement l’opération d’index, vous pouvez arrêter la commande en cours (Ctrl-C), ou vous pouvez exécuter la commande ALTER INDEX mettre en PAUSE ou l’arrêt *session_id* commande. Une fois la commande est interrompue peut être repris à l’aide d’option de reprise.
-  La commande d’annulation met fin à la session qui a hébergé la reconstruction d’index d’origine et abandonne l’opération d’index  
-  Aucune des ressources supplémentaires ne sont requis pour la reconstruction de l’index peut être repris à l’exception de
   -    Espace supplémentaire requis pour conserver l’index en cours de génération, y compris le temps lorsque l’index est en pause
   -    Un état DDL empêche toute modification DDL
-  Le nettoyage des enregistrements fantômes s’exécuteront pendant la phase de pause des index, mais il sera suspendu au cours de l’index exécutées   
La fonctionnalité suivante est désactivée pour les opérations de reconstruction d’index pouvant être reprises
   -    Reconstruction d’un index désactivé n’est pas pris en charge avec reprise = ON
   -    Commande ALTER INDEX REBUILD ALL
   -    ALTER TABLE, à l’aide de la reconstruction d’index  
   -    Commande DDL avec « RESUMEABLE = ON » ne peut pas être exécutée à l’intérieur d’une transaction explicite (ne peut pas faire partie de begin tran... bloc de validation)
   -    Reconstruire un index qui a calculé ou une ou des colonnes TIMESTAMP en tant que colonnes clés.
-   En cas de la table de base contient des colonnes LOB peut être repris en cluster reconstruction d’index requiert un verrou Sch-M au début de cette opération
   -    L’option SORT_IN_TEMPDB = ON option n’est pas prise en charge pour les index pouvant être reprise 

> [!NOTE]
> La commande DDL s’exécute jusqu'à ce qu’il ait terminé, s’arrête ou échoue. Dans le cas où la commande s’arrête, une erreur s’affiche indiquant que l’opération a été suspendue et que la création d’index n’a pas terminé. Plus d’informations sur l’état actuel de l’index peut être obtenu à partir de [sys.index_resumable_operations](../../relational-databases/system-catalog-views/sys-index-resumable-operations.md). Comme avant en cas de défaillance une erreur s’affiche également. 

  
 Pour plus d'informations, consultez [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md).  
  
 ### <a name="waitatlowpriority-with-online-index-operations"></a>WAIT_AT_LOW_PRIORITY avec les opérations d’index en ligne  
  
 Pour exécuter l'instruction DDL pour une reconstruction d'index en ligne, toutes les transactions bloquantes actives qui s'exécutent sur une table particulière doivent être terminées. Lorsque la reconstruction d'index en ligne s'exécute, elle bloque toutes les nouvelles transactions qui sont prêtes à s'exécuter sur cette table. Bien que la durée du verrou pour la reconstruction de l'index en ligne soit très courte, le fait d'attendre que toutes les transactions ouvertes sur une table spécifique soient exécutées, et le fait de bloquer les nouvelles transactions qui doivent démarrer, peuvent avoir un impact important sur le débit et provoquer un ralentissement ou un délai d'attente des charges de travail, limitant considérablement l'accès à la table sous-jacente. Le **WAIT_AT_LOW_PRIORITY** option permet d’administrateur de gérer les verrous des verrous S et Sch-M requis pour les index en ligne régénère et leur permet de sélectionner l’un des 3 options. Dans tous les 3 cas, si, pendant le délai d’attente ( `(MAX_DURATION = n [minutes])` ), il n’existe aucune activité bloquante, la reconstruction d’index en ligne est exécutée immédiatement sans attendre, et l’instruction DDL est terminée.  
  
## <a name="spatial-index-restrictions"></a>Restrictions des index spatiaux  
 Lorsque vous reconstruisez un index spatial, la table utilisateur sous-jacente est indisponible pour toute la durée de l'opération d'index car l'index spatial détient un verrou de schéma.  
  
 La contrainte PRIMARY KEY dans la table utilisateur ne peut pas être modifiée alors qu'un index spatial est défini sur une colonne de cette table. Pour modifier la contrainte PRIMARY KEY, commencez par supprimer chaque index spatial de la table. Après avoir modifié la contrainte PRIMARY KEY, vous pouvez recréer chaque index spatial.  
  
 Dans une opération individuelle de reconstruction de partition, vous ne pouvez pas spécifier d'index spatial. Toutefois, vous pouvez spécifier des index spatiaux dans une reconstruction de partition complète.  
  
 Pour modifier des options spécifiques à un index spatial, telles que BOUNDING_BOX ou GRID, vous pouvez utiliser une instruction CREATE SPATIAL INDEX qui spécifie DROP_EXISTING = ON ou supprimer l'index spatial et en créer un nouveau. Pour obtenir un exemple, consultez [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-spatial-index-transact-sql.md).  
  
## <a name="data-compression"></a>Data Compression  
 Pour plus d’informations sur la compression de données, consultez [Compression des données](../../relational-databases/data-compression/data-compression.md).  
  
 Pour évaluer la façon dont la modification de la compression de PAGE et de ligne affectera une table, un index ou une partition, utilisez le [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) procédure stockée.  
  
 Les restrictions suivantes s'appliquent aux index partitionnés :  
  
-   Lorsque vous utilisez `ALTER INDEX ALL ...`, vous ne pouvez pas modifier le paramètre de compression d’une partition unique si la table possède des index non alignés.  
  
-   L’instruction ALTER INDEX \<index >... REBUILD PARTITION ... reconstruit la partition spécifiée de l'index.  
  
-   L’instruction ALTER INDEX \<index >... REBUILD WITH ... reconstruit toutes les partitions de l'index.  
  
## <a name="statistics"></a>Statistiques  
 Lorsque vous exécutez **ALTER INDEX ALL...** sur une table, les statistiques associées aux index sont mis à jour. Les statistiques automatiques ou manuelles créées sur la table (au lieu d'un index) ne sont pas mises à jour.  
  
## <a name="permissions"></a>Permissions  
 Pour pouvoir exécuter l'instruction ALTER INDEX, vous devez obligatoirement bénéficier au minimum d'autorisations nécessaires pour exécuter les instructions ALTER sur la table ou la vue.  
  
## <a name="version-notes"></a>Notes de version  
  
-   Base de données SQL n’utilise pas les options de groupe de fichiers et de filestream.  
  
-   Index ColumnStore ne sont pas disponibles avant SQL Server 2012. 

-  Opérations d’index peut être repris sont disponibles à compter de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique) |   
  
## <a name="basic-syntax-example"></a>Exemple de syntaxe de base :   
  
```tsql 
ALTER INDEX index1 ON table1 REBUILD;  
  
ALTER INDEX ALL ON table1 REBUILD;  
  
ALTER INDEX ALL ON dbo.table1 REBUILD;  
```

## <a name="examples-columnstore-indexes"></a>Exemples : Les index Columnstore  
 Les exemples suivants s’appliquent aux index columnstore.  
  
### <a name="a-reorganize-demo"></a>A. RÉORGANISER la démonstration  
 Cet exemple illustre l’utilisation de la commande ALTER INDEX REORGANIZE.  Il crée une table qui comporte plusieurs groupes de lignes et montre ensuite comment RÉORGANISER fusionne les rowgroups.  
  
```  
-- Create a database   
CREATE DATABASE [ columnstore ];  
GO  
  
-- Create a rowstore staging table  
CREATE TABLE [ staging ] (  
     AccountKey              int NOT NULL,  
     AccountDescription      nvarchar (50),  
     AccountType             nvarchar(50),  
     AccountCodeAlternateKey     int  
     )  
  
-- Insert 10 million rows into the staging table.   
DECLARE @loop int  
DECLARE @AccountDescription varchar(50)  
DECLARE @AccountKey int  
DECLARE @AccountType varchar(50)  
DECLARE @AccountCode int  
  
SELECT @loop = 0  
BEGIN TRAN  
    WHILE (@loop < 300000)   
      BEGIN  
        SELECT @AccountKey = CAST (RAND()*10000000 as int);  
        SELECT @AccountDescription = 'accountdesc ' + CONVERT(varchar(20), @AccountKey);  
        SELECT @AccountType = 'AccountType ' + CONVERT(varchar(20), @AccountKey);  
        SELECT @AccountCode =  CAST (RAND()*10000000 as int);  
  
        INSERT INTO  staging VALUES (@AccountKey, @AccountDescription, @AccountType, @AccountCode);  
  
        SELECT @loop = @loop + 1;  
    END  
COMMIT  
  
-- Create a table for the clustered columnstore index  
  
CREATE TABLE cci_target (  
     AccountKey              int NOT NULL,  
     AccountDescription      nvarchar (50),  
     AccountType             nvarchar(50),  
     AccountCodeAlternateKey int  
     )  
  
-- Convert the table to a clustered columnstore index named inxcci_cci_target;  
```tsql
CREATE CLUSTERED COLUMNSTORE INDEX idxcci_cci_target ON cci_target;  
```  
  
 Utilisez l’option TABLOCK pour insérer des lignes en parallèle. À compter de SQL Server 2016, l’opération INSERT INTO peut exécuter en parallèle lorsque TABLOCK est utilisée.  
  
```tsql  
INSERT INTO cci_target WITH (TABLOCK) 
SELECT TOP 300000 * FROM staging;  
```  
  
 Exécutez cette commande pour voir les rowgroups delta ouvert. Le nombre de rowgroups varie selon le degré de parallélisme.  
  
```tsql  
SELECT *   
FROM sys.dm_db_column_store_row_group_physical_stats   
WHERE object_id  = object_id('cci_target');  
```  
  
 Exécutez cette commande pour forcer tous les fermé et rowgroups ouverts dans le columnstore.  
  
```tsql  
ALTER INDEX idxcci_cci_target ON cci_target REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
```  
  
 Exécutez à nouveau cette commande, et vous verrez que les plus petits rowgroups sont fusionnées dans un rowgroup compressé.  
  
```tsql  
ALTER INDEX idxcci_cci_target ON cci_target REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
```  
  
### <a name="b-compress-closed-delta-rowgroups-into-the-columnstore"></a>B. Compresser les rowgroups delta fermés dans le columnstore  
 Cet exemple utilise la réorganisation option compresse chaque rowgroup delta fermé dans le columnstore en tant qu’un rowgroup compressé.   Cela n’est pas nécessaire, mais il est utile lorsque le moteur de tuple pas compresse les rowgroups fermés assez rapides.  
  
```tsql  
-- Uses AdventureWorksDW  
-- REORGANIZE all partitions  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE;  
  
-- REORGANIZE a specific partition  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE PARTITION = 0;  
```  
  
### <a name="c-compress-all-open-and-closed-delta-rowgroups-into-the-columnstore"></a>C. Compresser tous les rowgroups delta ouvert et fermé dans le columnstore  
 Ne s’applique pas à : SQL Server 2012 et 2014  
  
 À compter de SQL Server 2016, vous pouvez exécuter REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON) pour compresser chaque rowgroup delta ouvert et fermé dans le columnstore en tant qu’un rowgroup compressé.    Vide le deltastores il force toutes les lignes à compressées dans le columnstore. Cela est utile en particulier après l’exécution de nombreuses opérations d’insertion dans la mesure où ces opérations stockent les lignes dans un ou plusieurs deltastores.  
  
 REORGANIZE combine rowgroups pour remplir les rowgroups jusqu'à un nombre maximal de lignes \<= 1,024,576. Par conséquent, lorsque vous compressez tous les rowgroups ouvert et fermé vous ne retrouvez avec un grand nombre de rowgroups compressés qui contiennent uniquement quelques lignes. Vous souhaitez que les rowgroups à être aussi complète que possible réduire la taille compressée et améliorer les performances des requêtes.  
  
```tsql  
-- Uses AdventureWorksDW2016  
-- Move all OPEN and CLOSED delta rowgroups into the columnstore.  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
  
-- For a specific partition, move all OPEN AND CLOSED delta rowgroups into the columnstore  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE PARTITION = 0 WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
```  
  
### <a name="d-defragment-a-columnstore-index-online"></a>D. Défragmenter un index columnstore en ligne  
 Ne s’applique pas à : SQL Server 2012 et 2014.  
  
 À compter de SQL Server 2016, REORGANIZE compresse plus les rowgroups delta dans le columnstore. Il effectue également la défragmentation en ligne. Tout d’abord, il réduit la taille du columnstore en supprimant physiquement les lignes supprimées lorsqu’au moins 10 % des lignes dans un groupe de lignes ont été supprimés.  Ensuite, elle combine les rowgroups pour former le plus grands rowgroups ayant au maximum de 1,024,576 lignes par rowgroups.  Tous les rowgroups sont modifiés compressées nouveau.  
  
> [!NOTE]
>  À compter de SQL Server 2016, reconstruire un index columnstore n’est plus nécessaire dans la plupart des cas, car REORGANIZE supprime les lignes supprimées physiquement et fusionne les rowgroups. L’option COMPRESS_ALL_ROW_GROUPS force tous les rowgroups delta ouvert ou fermé dans le columnstore qui précédemment peut être effectué uniquement avec une régénération.   REORGANIZE est en ligne et se produit en arrière-plan, afin que les requêtes peuvent continuer, car l’opération a lieu.  
  
```tsql  
-- Uses AdventureWorks  
-- Defragment by physically removing rows that have been logically deleted from the table, and merging rowgroups.  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE;  
```  
  
### <a name="e-rebuild-a-clustered-columnstore-index-offline"></a>E. Reconstruire un index columnstore cluster en mode hors connexion  
 S’applique à : SQL Server 2012, SQL Server 2014  
  
 En commençant par SQL Server 2016 et en [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], nous recommandons d’utiliser l’instruction ALTER INDEX REORGANIZE au lieu de l’instruction ALTER INDEX REBUILD.  
  
> [!NOTE]
>  Dans SQL Server 2012 et 2014, REORGANIZE est uniquement utilisée pour compresser les rowgroups fermés dans le columnstore. La seule façon pour effectuer des opérations de défragmentation et pour tous les rowgroups delta dans le columnstore consiste à reconstruire l’index.  
  
 Cet exemple montre comment reconstruire un index cluster et forcer tous les rowgroups delta dans le columnstore. Cette première étape prépare une table FactInternetSales2 avec un index columnstore cluster et insère les quatre premières colonnes.  
  
```tsql  
-- Uses AdventureWorksDW  
  
CREATE TABLE dbo.FactInternetSales2 (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
  
CREATE CLUSTERED COLUMNSTORE INDEX cci_FactInternetSales2  
ON dbo.FactInternetSales2;  
  
INSERT INTO dbo.FactInternetSales2  
SELECT ProductKey, OrderDateKey, DueDateKey, ShipDateKey  
FROM dbo.FactInternetSales;  
  
SELECT * FROM sys.column_store_row_groups;  
```  
  
 Les résultats indiquent un rowgroup ouvert, ce qui signifie qu’est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attend plus de lignes à ajouter avant de fermer le rowgroup et déplace les données dans le columnstore. L’instruction suivante reconstruit l’index columnstore cluster, ce qui force toutes les lignes dans le columnstore.  
  
```tsql  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REBUILD;  
SELECT * FROM sys.column_store_row_groups;  
```  
  
 Le résultat de l'instruction SELECT indique que le rowgroup est COMPRESSED, ce qui signifie que les segments de colonne du rowgroup sont compressés et stockés dans l'index columnstore.  
  
### <a name="f-rebuild-a-partition-of-a-clustered-columnstore-index-offline"></a>F. Reconstruire une partition d’un index columnstore cluster en mode hors connexion  
 Utilisez cette option pour : SQL Server 2012, SQL Server 2014  
  
 Pour reconstruire une partition d’un index columnstore cluster volumineux, utilisez ALTER INDEX REBUILD avec l’option de partition. Cet exemple reconstruit la partition 12. À compter de SQL Server 2016, nous vous recommandons de remplacer la reconstruction avec REORGANIZE.  
  
```tsql  
ALTER INDEX cci_fact3   
ON fact3  
REBUILD PARTITION = 12;  
```  
  
### <a name="g-change-a-clustered-columstore-index-to-use-archival-compression"></a>G. Modifier un index cluster columstore pour utiliser la compression d’archivage  
 Ne s’applique pas à : SQL Server 2012  
  
 Vous pouvez choisir de réduire la taille d’un index cluster columnstore encore davantage à l’aide de l’option de compression de données COLUMNSTORE_ARCHIVE. Cela est pratique pour les données plus anciennes que vous souhaitez conserver sur un stockage plus économique. Nous vous recommandons uniquement à l’aide de cela sur les données qui ne sont pas accessible souvent depuis décompresser plus lente qu’avec la compression COLUMNSTORE normale.  
  
 L'exemple suivant reconstruit un index columnstore cluster pour utiliser la compression d'archivage, puis montre comment supprimer la compression d'archivage. Le résultat final utilise uniquement la compression columnstore.  
  
```tsql  
--Prepare the example by creating a table with a clustered columnstore index.  
CREATE TABLE SimpleTable (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL  
);  
  
CREATE CLUSTERED INDEX cci_SimpleTable ON SimpleTable (ProductKey);  
  
CREATE CLUSTERED COLUMNSTORE INDEX cci_SimpleTable  
ON SimpleTable  
WITH (DROP_EXISTING = ON);  
  
--Compress the table further by using archival compression.  
ALTER INDEX cci_SimpleTable ON SimpleTable  
REBUILD  
WITH (DATA_COMPRESSION = COLUMNSTORE_ARCHIVE);  
  
--Remove the archive compression and only use columnstore compression.  
ALTER INDEX cci_SimpleTable ON SimpleTable  
REBUILD  
WITH (DATA_COMPRESSION = COLUMNSTORE);  
GO  
```  
  
## <a name="examples-rowstore-indexes"></a>Exemples : Les index Rowstore  
  
### <a name="a-rebuilding-an-index"></a>A. Reconstruction d'un index  
 L'exemple suivant reconstruit un seul index portant sur la table `Employee` de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```tsql  
ALTER INDEX PK_Employee_EmployeeID ON HumanResources.Employee REBUILD;  
```  
  
### <a name="b-rebuilding-all-indexes-on-a-table-and-specifying-options"></a>B. Reconstruction de tous les index d'une table et indication des options  
 L'exemple suivant indique le mot clé `ALL`. Il reconstruit tous les index associés à la table Production.Product dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Trois options sont spécifiées.  
  
**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.  
  
```tsql  
ALTER INDEX ALL ON Production.Product  
REBUILD WITH (FILLFACTOR = 80, SORT_IN_TEMPDB = ON, STATISTICS_NORECOMPUTE = ON);  
```  
  
 L'exemple suivant ajoute l'option ONLINE incluant l'option de verrou de faible priorité, et ajoute l'option de compression de ligne.  
  
**S’applique à**: SQL Server (à partir de SQL Server 2014) et la base de données SQL Azure.  
  
```tsql  
ALTER INDEX ALL ON Production.Product  
REBUILD WITH   
(  
    FILLFACTOR = 80,   
    SORT_IN_TEMPDB = ON,  
    STATISTICS_NORECOMPUTE = ON,  
    ONLINE = ON ( WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 4 MINUTES, ABORT_AFTER_WAIT = BLOCKERS ) ),   
    DATA_COMPRESSION = ROW  
);  
```  
  
### <a name="c-reorganizing-an-index-with-lob-compaction"></a>C. Réorganisation d'un index avec compactage LOB  
 L'exemple suivant réorganise un seul index cluster dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. L'index contenant un type de données LOB au niveau de la feuille, l'instruction compacte par la même occasion toutes les pages contenant les données LOB. Notez que l'indication de l'option WITH (LOB_COMPACTION) n'est pas nécessaire car la valeur par défaut est ON.  
  
```tsql  
ALTER INDEX PK_ProductPhoto_ProductPhotoID ON Production.ProductPhoto REORGANIZE WITH (LOB_COMPACTION);  
```  
  
### <a name="d-setting-options-on-an-index"></a>D. Définition des options d'un index  
 L'exemple suivant définit plusieurs options sur l'index `AK_SalesOrderHeader_SalesOrderNumber` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
**S’applique à**: SQL Server (à partir de SQL Server 2008) et la base de données SQL Azure.  
  
```tsql  
ALTER INDEX AK_SalesOrderHeader_SalesOrderNumber ON  
    Sales.SalesOrderHeader  
SET (  
    STATISTICS_NORECOMPUTE = ON,  
    IGNORE_DUP_KEY = ON,  
    ALLOW_PAGE_LOCKS = ON  
    ) ;  
GO
```  
  
### <a name="e-disabling-an-index"></a>E. Désactivation d'un index  
 L'exemple suivant désactive un index non cluster sur la table `Employee` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```tsql  
ALTER INDEX IX_Employee_ManagerID ON HumanResources.Employee DISABLE;
```  
  
### <a name="f-disabling-constraints"></a>F. Désactivation des contraintes  
 L’exemple suivant désactive une contrainte PRIMARY KEY en désactivant l’index de clé primaire dans la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données. La contrainte FOREIGN KEY portant sur la table sous-jacente est automatiquement désactivée et un avertissement s'affiche.  
  
```tsql  
ALTER INDEX PK_Department_DepartmentID ON HumanResources.Department DISABLE;  
```  
  
 Le jeu de résultats retourne l'avertissement suivant.  
  
 ```tsql  
 Warning: Foreign key 'FK_EmployeeDepartmentHistory_Department_DepartmentID'  
 on table 'EmployeeDepartmentHistory' referencing table 'Department'  
 was disabled as a result of disabling the index 'PK_Department_DepartmentID'.
 ```  
  
### <a name="g-enabling-constraints"></a>G. Activation des contraintes  
 L'exemple suivant active les contraintes PRIMARY KEY et FOREIGN KEY désactivées dans l'exemple F.  
  
 La contrainte PRIMARY KEY est activée lors de la reconstruction de l'index PRIMARY KEY.  
  
```tsql  
ALTER INDEX PK_Department_DepartmentID ON HumanResources.Department REBUILD;  
```  
  
 La contrainte FOREIGN KEY est ensuite activée.  
  
```tsql  
ALTER TABLE HumanResources.EmployeeDepartmentHistory  
CHECK CONSTRAINT FK_EmployeeDepartmentHistory_Department_DepartmentID;  
GO  
```  
  
### <a name="h-rebuilding-a-partitioned-index"></a>H. Reconstruction d'un index partitionné  
 L'exemple suivant reconstruit une seule partition, celle portant le numéro de partition `5`, de l'index partitionné `IX_TransactionHistory_TransactionDate` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. La partition 5 est reconstruite en ligne et le délai d'attente de 10 minutes pour le verrou de priorité basse s'applique séparément à chaque verrou acquis par l'opération de reconstruction d'index. Si pendant ce temps, le verrou ne peut pas être obtenu pour terminer la reconstruction de l'index complet, l'instruction de l'opération de reconstruction est interrompue.  
  
**S’applique à**: SQL Server (à partir de SQL Server 2014) et la base de données SQL Azure.  
  
```tsql  
-- Verify the partitioned indexes.  
SELECT *  
FROM sys.dm_db_index_physical_stats (DB_ID(),OBJECT_ID(N'Production.TransactionHistory'), NULL , NULL, NULL);  
GO  
--Rebuild only partition 5.  
ALTER INDEX IX_TransactionHistory_TransactionDate  
ON Production.TransactionHistory  
REBUILD Partition = 5   
   WITH (ONLINE = ON (WAIT_AT_LOW_PRIORITY (MAX_DURATION = 10 minutes, ABORT_AFTER_WAIT = SELF)));  
GO  
```  
  
### <a name="i-changing-the-compression-setting-of-an-index"></a>I. Modification du paramètre de compression d'un index  
 L'exemple suivant reconstruit un index sur une table rowstore non partitionnée.  
  
```tsql
ALTER INDEX IX_INDEX1   
ON T1  
REBUILD   
WITH (DATA_COMPRESSION = PAGE);  
GO  
```  
  
 Pour des exemples de la compression des données supplémentaires, consultez [la Compression des données](../../relational-databases/data-compression/data-compression.md).  
 
### <a name="j-online-resumable-index-rebuild"></a>J. Reconstruction d’index peut être repris en ligne

**S’applique à**: à partir de SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique)    

 Les exemples suivants montrent comment utiliser la reconstruction d’index peut être repris en ligne. 

1. Exécuter une reconstruction d’index en ligne en tant qu’opération pouvant être reprise avec MAXDOP = 1.

   ```tsql
   ALTER INDEX test_idx on test_table REBUILD WITH (ONLINE=ON, MAXDOP=1, RESUMABLE=ON) ;
   ```

2. L’exécution de la même commande Nouveau (voir ci-dessus) après qu’une opération d’index a été suspendue, reprend automatiquement l’opération de reconstruction d’index.

3. Exécutez une reconstruction d’index en ligne en tant qu’opération de reprise avec la valeur MAX_DURATION 240 minutes.

   ```tsql
   ALTER INDEX test_idx on test_table REBUILD WITH (ONLINE=ON, RESUMABLE=ON, MAX_DURATION=240) ; 
   ```
4. Suspendre une reconstruction d’index en ligne en cours d’exécution peut être repris.

   ```tsql
   ALTER INDEX test_idx on test_table PAUSE ;
   ```   
5. Reprendre une reconstruction d’index en ligne pour une reconstruction d’index qui a été exécutée, car l’opération peut être reprise en spécifiant une nouvelle valeur à MAXDOP a la valeur 4.

   ```tsql
   ALTER INDEX test_idx on test_table RESUME WITH (MAXDOP=4) ;
   ```
6. Reprendre une opération de reconstruction d’index en ligne pour une reconstruction d’index en ligne qui a été exécutée comme pouvant être repris. Définir MAXDOP à 2, la durée d’exécution de l’index en cours d’exécution en tant que resmumable et 240 minutes et en cas d’un index qui est bloqué dans l’attente de verrou 10 minutes et après que kill tous les bloqueurs. 

   ```tsql
      ALTER INDEX test_idx on test_table  
         RESUME WITH (MAXDOP=2, MAX_DURATION= 240 MINUTES, 
         WAIT_AT_LOW_PRIORITY (MAX_DURATION=10, ABORT_AFTER_WAIT=BLOCKERS)) ;
   ```      
7. Abandonner l’opération de reconstruction d’index peut être repris qui est en cours d’exécution ou suspendu.

   ```tsql
   ALTER INDEX test_idx on test_table ABORT ;
   ``` 
  
## <a name="see-also"></a>Voir aussi  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE SPATIAL INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/create-spatial-index-transact-sql.md)   
 [CRÉER un INDEX XML &#40; Transact-SQL &#41;](../../t-sql/statements/create-xml-index-transact-sql.md)   
 [DROP INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/drop-index-transact-sql.md)   
 [Désactiver les index et contraintes](../../relational-databases/indexes/disable-indexes-and-constraints.md)   
 [Index XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)   
 [Exécuter des opérations d’Index en ligne](../../relational-databases/indexes/perform-index-operations-online.md)   
 [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  



