---
title: "G&#233;rer les partitions d&#39;une publication de fusion avec des filtres param&#233;trables | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "partitions [réplication SQL Server]"
  - "partitions de réplication de fusion [réplication SQL Server], SQL Server Management Studio"
  - "filtres paramétrés [réplication SQL Server], gestion de partitions"
ms.assetid: fb5566fe-58c5-48f7-8464-814ea78e6221
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# G&#233;rer les partitions d&#39;une publication de fusion avec des filtres param&#233;trables
  Cette rubrique explique comment gérer des partitions pour une publication de fusion avec des filtres paramétrables dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects). Les filtres de lignes paramétrables peuvent être utilisés pour générer des partitions qui ne se chevauchent pas. Ces partitions peuvent être restreintes afin qu'un seul abonnement puisse recevoir une partition donnée. Dans ces cas, un grand nombre d'abonnés se traduit par un nombre élevé de partitions, ce qui requiert ensuite un nombre égal d'instantanés partitionnés. Pour plus d'informations, voir [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour gérer les partitions d'une publication de fusion avec les filtres paramétrables à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Si vous créez un script de la topologie de réplication (ce qui est recommandé), les scripts de publication contiennent les appels de procédures stockées pour créer des partitions de données. Le script fournit une référence pour les partitions créées et un moyen permettant de recréer si nécessaire une ou plusieurs partitions. Pour plus d'informations, voir [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
-   Lorsqu'une publication a paramétré des filtres qui génèrent des abonnements avec des partitions ne se chevauchant pas, et si un abonnement particulier est perdu et doit être recréé, vous devez effectuer les opérations suivantes : supprimez la partition à laquelle s'abonner, recréez l'abonnement, puis recréez la partition. Pour plus d'informations, voir [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md). La réplication génère des scripts de création pour les partitions d'Abonné existantes lors de la génération d'un script de création de publication. Pour plus d'informations, voir [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Gérer des partitions sur le **des Partitions de données** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Sur cette page, vous pouvez : créer et supprimer des partitions, autoriser des Abonnés à initier la génération et la remise d'instantanés, générer des instantanés pour une ou plusieurs partitions et nettoyer des instantanés.  
  
#### Pour créer une partition  
  
1.  Sur le **des Partitions de données** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **Ajouter**.  
  
2.  Dans le **Ajouter une Partition de données** boîte de dialogue, entrez une valeur pour le **HOST_NAME()** et/ou **SUSER_SNAME()** valeur associée à la partition que vous souhaitez créer.  
  
3.  En option, spécifiez une planification pour l'actualisation des instantanés :  
  
    1.  Sélectionnez **planification de l’Agent de capture instantanée pour cette partition pour s’exécuter à la fois suivante**  
  
    2.  Acceptez la planification par défaut pour l'actualisation des instantanés, ou cliquez sur **Modifier** pour spécifier une autre planification.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Pour supprimer une partition  
  
1.  Sur la page **Partitions de données** , sélectionnez une partition dans la grille.  
  
2.  Cliquez sur **Supprimer**.  
  
#### Pour permettre aux Abonnés d'initier la génération et la remise d'instantanés  
  
1.  Sur la page **Partitions de données** , sélectionnez **Définir automatiquement une partition et générer un instantané si nécessaire lorsqu'un nouvel abonné essaie de se synchroniser**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Pour générer un instantané pour une partition  
  
1.  Sur la page **Partitions de données** , sélectionnez une partition dans la grille.  
  
2.  Cliquez sur **Générer les instantanés sélectionnés maintenant**.  
  
#### Pour nettoyer un instantané pour une partition  
  
1.  Sur la page **Partitions de données** , sélectionnez une partition dans la grille.  
  
2.  Cliquez sur **Nettoyer les instantanés existants**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Pour mieux gérer une publication avec des filtres paramétrables, vous pouvez énumérer par programmation les partitions existantes à l'aide de procédures stockées de réplication. Vous pouvez également créer et supprimer des partitions existantes. Vous pouvez obtenir les informations suivantes sur les partitions existantes :  
  
-   Comment une partition est filtrée (à l’aide de [SUSER_SNAME & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/suser-sname-transact-sql.md) ou [HOST_NAME & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/host-name-transact-sql.md)).  
  
-   Le nom du travail qui génère un instantané partitionné.  
  
-   La dernière fois qu'un travail d'instantané partitionné a été exécuté.  
  
 Tandis que la deuxième partie de l'instantané bipartite peut être généré à la demande lors de l'initialisation d'un nouvel abonnement, les procédures suivantes permettent de contrôler comment cet instantané est généré et de le prégénérer dans les cas les plus pratiques. Pour plus d'informations, voir [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
#### Pour consulter les informations sur les partitions existantes  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergepartition & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md). Spécifiez le nom de la publication pour **@ publication**. (Facultatif) Spécifiez **@suser_sname** ou **@host_name** pour renvoyer uniquement les informations basées sur un seul critère de filtrage.  
  
#### Pour définir une nouvelle partition et générer un nouvel instantané partitionné  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergepartition & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md). Spécifiez le nom de la publication pour **@publication**et la valeur paramétrable qui définit la partition pour l'un des éléments suivants :  
  
    -   **@suser_sname** - lorsque le filtre paramétrable est défini par la valeur retournée par [SUSER_SNAME & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/suser-sname-transact-sql.md).  
  
    -   **@host_name** - lorsque le filtre paramétrable est défini par la valeur retournée par [HOST_NAME & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/host-name-transact-sql.md).  
  
2.  Créez et initialisez l'instantané paramétrable de cette nouvelle partition. Pour plus d'informations, voir [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
#### Pour supprimer une partition  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_dropmergepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md). Spécifiez le nom de la publication pour **@publication** et la valeur paramétrable qui définit la partition pour l'un des éléments suivants :  
  
    -   **@suser_sname** - lorsque le filtre paramétrable est défini par la valeur retournée par [SUSER_SNAME & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/suser-sname-transact-sql.md).  
  
    -   **@host_name** - lorsque le filtre paramétrable est défini par la valeur retournée par [HOST_NAME & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/host-name-transact-sql.md).  
  
     Le travail d'instantané et les fichiers d'instantané de la partition sont également supprimés.  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Pour mieux gérer une publication avec les filtres paramétrables, vous pouvez par programmation créer, énumérer ou supprimer les partitions d'Abonné, en utilisant les objets RMO (Replication Management Objects). Pour plus d'informations sur la création de partitions d'Abonné, consultez [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). Vous pouvez obtenir les informations suivantes sur les partitions existantes :  
  
-   la valeur et la fonction de filtrage sur lesquelles la partition est basée ;  
  
-   le nom du travail qui génère un instantané paramétrable pour l'Abonné ;  
  
-   la dernière fois qu'un travail d'instantané paramétrable a été exécuté ;  
  
#### Pour consulter les informations sur les partitions existantes  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe. Définir le <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication et définissez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété du <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> (méthode) et transmettez le résultat dans un tableau de <xref:Microsoft.SqlServer.Replication.MergePartition> objets.  
  
5.  Pour chaque <xref:Microsoft.SqlServer.Replication.MergePartition> de l’objet dans le tableau, récupérez les propriétés d’intérêt.  
  
#### Pour supprimer les partitions existantes  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe. Définir le <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication et définissez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété du <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> (méthode) et transmettez le résultat dans un tableau de <xref:Microsoft.SqlServer.Replication.MergePartition> objets.  
  
5.  Pour chaque <xref:Microsoft.SqlServer.Replication.MergePartition> de l’objet dans le tableau, déterminez si la partition doit être supprimée. Cette décision est généralement basée sur la valeur de la <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> propriété ou <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> propriété.  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> méthode sur le <xref:Microsoft.SqlServer.Replication.MergePublication> objet de l’étape 2. Passez le <xref:Microsoft.SqlServer.Replication.MergePartition> objet de l’étape 5.  
  
7.  Répétez l'étape 6 pour chaque partition supprimée.  
  
## Voir aussi  
 [Filtres de lignes paramétrés](../../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Instantanés des publications de fusion avec des filtres paramétrés](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  