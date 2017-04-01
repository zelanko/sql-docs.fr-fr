---
title: "Cr&#233;er un instantan&#233; d&#39;une publication de fusion avec des filtres param&#233;tr&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "05/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtres paramétrés [réplication SQL Server], instantanés"
  - "instantanés [réplication SQL Server], filtres paramétrés et"
  - "filtres [réplication SQL Server], paramétrés"
ms.assetid: 00dfb229-f1de-4d33-90b0-d7c99ab52dcb
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Cr&#233;er un instantan&#233; d&#39;une publication de fusion avec des filtres param&#233;tr&#233;s
  Cette rubrique explique comment créer un instantané pour une publication de fusion avec des filtres paramétrables dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour créer un instantané d'une publication de fusion avec des filtres paramétrés à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Lors de la génération d'un instantané pour une publication de fusion à l'aide de filtres paramétrables, vous devez commencer par générer un instantané standard (schéma) qui contient l'ensemble des données publiées, ainsi que les métadonnées de l'Abonné pour l'abonnement. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md). Après avoir créé l'instantané de schéma, vous pouvez générer l'instantané qui contient la partition des données publiées spécifique à l'Abonné.  
  
-   Si le filtrage d'un ou plusieurs articles de la publication donne des partitions qui ne se chevauchent pas et sont uniques pour chaque abonnement, les métadonnées sont nettoyées à chaque exécution de l'Agent de fusion. Cela signifie que l'instantané partitionné expire plus rapidement. Lorsque vous optez pour cette méthode, envisagez d'autoriser les Abonnées à initialiser la génération et la remise d'instantané. Pour plus d’informations sur les options de filtrage, consultez la section « Définition des options de partition » de [instantanés pour les Publications de fusion avec des filtres paramétrés](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Générer des instantanés pour les partitions sur le **des Partitions de données** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Vous pouvez permettre à des Abonnés de lancer la génération et la livraison d'instantanés et/ou de générer des instantanés.  
  
 Pour générer des instantanés pour une ou plusieurs partitions, vous devez préalablement :  
  
1.  créer une publication de fusion à l'aide de l'Assistant Nouvelle publication et spécifier un ou plusieurs filtres de lignes paramétrables dans la page **Ajouter un filtre** de l'Assistant. Pour plus d'informations, voir [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
2.  Générez un instantané du schéma pour la publication. Par défaut, un instantané du schéma est généré lorsque vous terminez l'Assistant Nouvelle publication ; vous pouvez également générer un instantané du schéma à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Pour générer un instantané du schéma  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis le dossier **Publications** .  
  
3.  Avec le bouton droit de la publication pour laquelle vous souhaitez créer un instantané, puis cliquez sur **Afficher l’état de l’Agent capture instantanée**.  
  
4.  Dans la **Afficher l’état de l’Agent capture instantanée - \< Publication>** boîte de dialogue, cliquez sur **Démarrer**.  
  
     Lorsque l'Agent d'instantané termine la génération de l'instantané, un message comme celui-ci s'affiche : « [100 %] Un instantané de 17 article(s) a été généré ».  
  
#### Pour permettre aux Abonnés d'initier la génération et la remise d'instantanés  
  
1.  Sur le **des Partitions de données** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez **définir automatiquement une partition et générer une capture instantanée si nécessaire lorsqu’un nouvel abonné essaie de se synchroniser**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### Pour générer et actualiser des instantanés  
  
1.  Sur le **des Partitions de données** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **Ajouter**.  
  
2.  Entrez une valeur pour le **HOST_NAME()** et/ou **SUSER_SNAME()** valeur associée à la partition pour laquelle vous souhaitez créer un instantané.  
  
3.  En option, spécifiez une planification pour l'actualisation des instantanés :  
  
    1.  Sélectionnez **planification de l’Agent de capture instantanée pour cette partition pour s’exécuter à la fois suivante**  
  
    2.  Acceptez la planification par défaut pour l'actualisation des instantanés, ou cliquez sur **Modifier** pour spécifier une autre planification.  
  
4.  Cliquez sur **OK**, ce qui vous renvoie à le **Propriétés de la Publication - \< Publication>** boîte de dialogue.  
  
5.  Sélectionnez la partition dans la grille de propriétés, puis cliquez sur **Générer les instantanés sélectionnés maintenant**.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les procédures stockées et l'Agent d'instantané permettent d'effectuer les tâches suivantes :  
  
-   Vous pouvez autoriser les Abonnés à demander la génération et l'application d'un instantané lors de leur première synchronisation.  
  
-   Vous pouvez prégénérer des instantanés pour chaque partition.  
  
-   générer manuellement un instantané pour chaque Abonné.  
  
    > [!IMPORTANT]  
    >  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
#### Pour créer une publication qui permet aux Abonnés d'initialiser la génération et la remise d'instantanés  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Spécifiez les paramètres suivants :  
  
    -   Le nom de la publication pour **@publication**.  
  
    -   Valeur **true** pour **@allow_subscriber_initiated_snapshot**, ce qui permet aux abonnés d’initier le processus d’instantané.  
  
    -   (Facultatif) Le nombre de processus de capture instantanée dynamique pouvant s’exécuter simultanément pour **@max_concurrent_dynamic_snapshots**. Si le nombre maximal de processus en cours d'exécution est atteint et si un Abonné essaie de générer un instantané, le processus est placé en file d'attente. Par défaut, le nombre de processus simultanés est illimité.  
  
2.  Sur le serveur de publication, exécutez [sp_addpublication_snapshot & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Spécifiez le nom de publication utilisé à l’étape 1 pour **@publication** et [!INCLUDE[msCoName](../../includes/msconame-md.md)] les informations d’identification Windows sous lequel le [Agent de capture instantanée de réplication](../../relational-databases/replication/agents/replication-snapshot-agent.md) s’exécute pour **@job_login** et **@password**. Si l’agent utilisera [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informations de connexion pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication. Pour plus d'informations sur la génération d'un instantané initial et la définition d'une planification personnalisée pour l'Agent d'instantané, consultez [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Lorsque vous configurez un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Exécutez [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Pour ajouter des articles à la publication. Cette procédure stockée doit être exécutée une fois pour chaque article de la publication. Lorsque vous utilisez des filtres paramétrés, vous devez spécifier un filtre de lignes paramétrable pour un ou plusieurs articles à l’aide de la **@subset_filterclause** paramètre. Pour plus d'informations, consultez [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Si d’autres articles doivent être filtrés en fonction du filtre de lignes paramétrable, exécutez [sp_addmergefilter & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) Pour définir les relations d’enregistrements logiques entre des articles de jointure. Cette procédure stockée doit être exécutée une fois pour chaque relation en cours de définition. Pour plus d'informations, voir [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Lorsque l'Agent de fusion demande à l'instantané d'initialiser l'Abonné, l'instantané de la partition de l'abonnement demandeur est généré automatiquement.  
  
#### Pour créer une publication et prégénérer ou actualiser automatiquement des instantanés  
  
1.  Exécutez [sp_addmergepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) Pour créer la publication. Pour plus d'informations, voir [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Sur le serveur de publication, exécutez [sp_addpublication_snapshot & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Spécifiez le nom de publication utilisé à l’étape 1 pour **@publication** et les informations d’identification Windows sous lequel l’Agent de capture instantanée s’exécute pour **@job_login** et **@password**. Si l’agent utilisera [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les informations de connexion pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication. Pour plus d'informations sur la génération d'un instantané initial et la définition d'une planification personnalisée pour l'Agent d'instantané, consultez [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Lorsque vous configurez un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Exécutez [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Pour ajouter des articles à la publication. Cette procédure stockée doit être exécutée une fois pour chaque article de la publication. Lorsque vous utilisez des filtres paramétrés, vous devez spécifier un filtre de lignes paramétrable pour un article à l’aide du **@subset_filterclause** paramètre. Pour plus d'informations, consultez [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Si d’autres articles doivent être filtrés en fonction du filtre de lignes paramétrable, exécutez [sp_addmergefilter & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) Pour définir les relations d’enregistrements logiques entre des articles de jointure. Cette procédure stockée doit être exécutée une fois pour chaque relation en cours de définition. Pour plus d'informations, voir [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), en spécifiant la valeur de **@publication** à l’étape 1. Notez la valeur de la **snapshot_jobid** dans le résultat défini.  
  
6.  Convertir la valeur de la **snapshot_jobid** obtenu à l’étape 5 **uniqueidentifier**.  
  
7.  Sur le serveur de publication sur le **msdb** de base de données, exécutez [sp_start_job & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), en spécifiant la valeur convertie obtenue à l’étape 6 pour **@job_id**.  
  
8.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergepartition & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md). Spécifiez le nom de la publication à l’étape 1 pour **@publication** et la valeur utilisée pour définir la partition pour **@suser_sname** Si [SUSER_SNAME & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/suser-sname-transact-sql.md) est utilisé dans la clause de filtre ou de **@host_name** Si [HOST_NAME & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/host-name-transact-sql.md) est utilisé dans la clause de filtre.  
  
9. Sur le serveur de publication sur la base de données de publication, exécutez [sp_adddynamicsnapshot_job & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md). Spécifiez le nom de la publication à l’étape 1 pour **@publication**, la valeur de **@suser_sname** ou **@host_name** à l’étape 8 et la planification de la tâche. Le travail qui génère l'instantané paramétrable pour la partition spécifiée est ainsi créé. Pour plus d'informations, voir [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!NOTE]  
    >  Ce travail s'exécute à l'aide du même compte Windows que le travail d'instantané initial défini à l'étape 2. Pour supprimer le travail d’instantané paramétrable et sa partition de données associées, exécutez [sp_dropdynamicsnapshot_job & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql.md).  
  
10. Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergepartition & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md), en spécifiant la valeur de **@publication** à l’étape 1 et la valeur de **@suser_sname** ou **@host_name** à l’étape 8. Notez la valeur de la **dynamic_snapshot_jobid** dans le résultat défini.  
  
11. Sur le serveur de distribution le **msdb** de base de données, exécutez [sp_start_job & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), en spécifiant la valeur obtenue à l’étape 9 pour **@job_id**. Le travail d'instantané paramétrable de la partition est alors démarré.  
  
12. Répétez les étapes 8 à 11 pour générer un instantané partitionné pour chaque abonnement.  
  
#### Pour créer une publication et créer manuellement des instantanés pour chaque partition  
  
1.  Exécutez [sp_addmergepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) Pour créer la publication. Pour plus d'informations, voir [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Sur le serveur de publication, exécutez [sp_addpublication_snapshot & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Spécifiez le nom de publication utilisé à l’étape 1 pour **@publication** et les informations d’identification Windows sous lequel l’Agent de capture instantanée s’exécute pour **@job_login** et **@password**. Si l’agent utilisera [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les informations de connexion pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication. Pour plus d'informations sur la génération d'un instantané initial et la définition d'une planification personnalisée pour l'Agent d'instantané, consultez [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    > [!IMPORTANT]  
    >  Lorsque vous configurez un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Exécutez [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Pour ajouter des articles à la publication. Cette procédure stockée doit être exécutée une fois pour chaque article de la publication. Lorsque vous utilisez des filtres paramétrés, vous devez spécifier un filtre de lignes paramétrable au moins un article à l’aide du **@subset_filterclause** paramètre. Pour plus d'informations, consultez [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
4.  Si d’autres articles doivent être filtrés en fonction du filtre de lignes paramétrable, exécutez [sp_addmergefilter & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) Pour définir les relations d’enregistrements logiques entre des articles de jointure. Cette procédure stockée doit être exécutée une fois pour chaque relation en cours de définition. Pour plus d'informations, voir [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
5.  Démarrez le travail d'instantané ou exécutez l'Agent d'instantané des réplications à partir de l'invite de commandes pour générer le schéma d'instantané standard et d'autres fichiers. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
6.  Réexécutez l’Agent de capture instantanée de réplication à partir de l’invite de commandes pour générer en bloc (.bcp) des fichiers, en spécifiant l’emplacement de la capture instantanée pour **- DynamicSnapshotLocation** et un ou deux des propriétés qui définit la partition suivantes :  
  
    -   **-DynamicFilterHostName** -la valeur si [HOST_NAME & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/host-name-transact-sql.md) est utilisé.  
  
    -   **-DynamicFilterLogin** -la valeur si [SUSER_SNAME & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/suser-sname-transact-sql.md) est utilisé.  
  
7.  Répétez l'étape 6 pour générer un instantané partitionné pour chaque abonnement.  
  
8.  Exécutez l'Agent de fusion pour chaque abonnement afin d'appliquer l'instantané partitionné initial aux Abonnés, en spécifiant les propriétés suivantes :  
  
    -   **-Hostname** -la valeur utilisée pour définir la partition si la valeur réelle de HOST_NAME est remplacée.  
  
    -   **-DynamicSnapshotLocation** -l’emplacement de la capture instantanée dynamique pour cette partition.  
  
> [!NOTE]  
>  Pour plus d’informations sur la programmation des agents de réplication, consultez [Concepts des exécutables de l’Agent réplication](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple crée une publication de fusion avec des filtres paramétrables dans laquelle les Abonnés initialisent le processus de génération d'instantané. Les valeurs pour **@job_login** et **@job_password** sont passés à l’aide de variables de script.  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_1.sql)]  
  
 Cet exemple crée une publication à l’aide d’un filtre paramétré où chaque abonné possède sa partition définie par l’exécution de [sp_addmergepartition](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md) et le travail d’instantané filtré créé par l’exécution de [sp_adddynamicsnapshot_job](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md) en transmettant les informations de partitionnement. Les valeurs pour **@job_login** et **@job_password** sont passés à l’aide de variables de script.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_2.sql)]  
  
 Cet exemple crée une publication à l'aide d'un filtre paramétrable dans laquelle la partition de données et le travail d'instantané filtré de chaque Abonné doivent être créés en fournissant les informations de partitionnement. Un Abonné fournit des informations de partitionnement à l'aide de paramètres de ligne de commande lors de l'exécution manuelle des agents de réplication. Cet exemple suppose qu'un abonnement à la publication a également été créé.  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPartitionManual](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_3.sql)]  
  
```  
  
REM Line breaks are added to improve readability.   
REM In a batch file, commands must be made in a single line.  
REM Run the Snapshot agent from the command line to generate the standard snapshot   
REM schema and other files.   
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub% -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  
  
PAUSE  
  
```  
  
```  
  
REM Run the Snapshot agent from the command line, this time to generate   
REM the bulk copy (.bcp) data for each Subscriber partition.    
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
MD %SnapshotDir%  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub%  -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  -DynamicFilterHostName "adventure-works\Fernando"    
-DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
```  
  
REM Run the Merge Agent for each subscription to apply the partitioned   
REM snapshot for each Subscriber.    
SET Publisher = %computername%  
SET Subscriber = %computername%  
SET PubDB = AdventureWorks2012   
SET SubDB = AdventureWorks2012Replica   
SET PubName = AdvWorksSalesPersonMerge   
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publisher  %Publisher%    
-Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB %PubDB%    
-SubscriberDB %SubDB% -Publication %PubName%  -PublisherSecurityMode 1  -OutputVerboseLevel 3    
-Output -SubscriberSecurityMode 1  -SubscriptionType 3 -DistributorSecurityMode 1    
-Hostname "adventure-works\Fernando"  -DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez utiliser les Replication Management Objects pour générer par programme des instantanés partitionnés des manières suivantes :  
  
-   Vous pouvez autoriser les Abonnés à demander la génération et l'application d'un instantané lors de leur première synchronisation.  
  
-   Vous pouvez prégénérer des instantanés pour chaque partition.  
  
-   Vous pouvez générer manuellement un instantané pour chaque Abonné en exécutant l'Agent d'instantané.  
  
> [!NOTE]  
>  Lors du filtrage pour un article génère des partitions sans chevauchement qui sont uniques pour chaque abonnement (en spécifiant une valeur de F:Microsoft.SqlServer.Replication.PartitionOptions.NonOverlappingSingleSubscription pour P:Microsoft.SqlServer.Replication.MergeArticle.PartitionOption lors de la création d’un article de fusion), les métadonnées sont nettoyées à chaque exécution de l’Agent de fusion. Cela signifie que l'instantané partitionné expire plus rapidement. Lorsque vous optez pour cette méthode, envisagez d'autoriser les Abonnées à demander la génération d'instantanés. Pour plus d'informations, consultez la section Utilisation des options de filtrage appropriées, dans la rubrique [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez stocker des informations d'identification, utilisez les [Services de chiffrement](http://go.microsoft.com/fwlink/?LinkId=34733) fournis par [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Pour créer une publication qui permet aux Abonnés d'initialiser la génération et la remise d'instantanés  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créer une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> classe pour la base de données de publication, définissez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à l’instance de <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à partir de l’étape 1, puis appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> (méthode). Si <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> retourne **false**, confirmez l’existence de la base de données.  
  
3.  Si <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> propriété **false**, affectez-lui la valeur **true** et appelez <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>.  
  
4.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> puis définissez les propriétés suivantes pour cet objet :  
  
    -   Le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Le nom de la base de données publiée pour <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>.  
  
    -   Un nom de la publication de <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>.  
  
    -   Le nombre maximal de travaux de capture instantanée dynamique à exécuter pour <xref:Microsoft.SqlServer.Replication.MergePublication.MaxConcurrentDynamicSnapshots%2A>. Comme des demandes d'instantané initialisées par l'Abonné peuvent se produire à tout moment, cette propriété limite le nombre des travaux de l'Agent d'instantané qui peuvent s'exécuter simultanément lorsque plusieurs Abonnés demandent leur instantané partitionné au même moment. Lorsque le nombre maximal de travaux s'exécute, des demandes d'instantanés partitionnés supplémentaires sont mises en file d'attente jusqu'à ce que l'un des travaux en cours d'exécution se termine.  
  
    -   Utilisez le OR logique (**|** en Visual c# et **ou** en Visual Basic) pour ajouter la valeur <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowSubscriberInitiatedSnapshot> à <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>.  
  
    -   Le <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> et <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> champs de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> pour fournir les informations d’identification pour la [!INCLUDE[msCoName](../../includes/msconame-md.md)] du compte Windows sous lequel s’exécute le travail de l’Agent de capture instantanée.  
  
        > [!NOTE]  
        >  Paramètre <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> est recommandée lors de la publication est créée par un membre de la **sysadmin** rôle serveur fixe. Pour plus d'informations, voir [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> méthode pour créer la publication.  
  
    > [!IMPORTANT]  
    >  Lorsque vous configurez un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour toutes les propriétés, y compris <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et serveur de distribution distant avant d’appeler le <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> méthode. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
6.  Utilisez le <xref:Microsoft.SqlServer.Replication.MergeArticle> propriété pour ajouter des articles à la publication. Spécifiez le <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> propriété au moins un article qui définit le filtre paramétré. (Facultatif) Créer <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> les objets qui définissent les filtres de jointure entre les articles. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
7.  Si la valeur de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> est **false**, appelez <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> pour créer le travail d’Agent de capture instantanée initial pour cette publication.  
  
8.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> Procédé de la <xref:Microsoft.SqlServer.Replication.MergePublication> objet créé à l’étape 4. Cela démarre le travail de l'agent qui génère l'instantané initial. Pour plus d'informations sur la génération d'un instantané initial et la définition d'une planification personnalisée pour l'Agent d'instantané, consultez [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
9. (Facultatif) Recherchez une valeur de **true** pour la <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> propriété pour déterminer quand l’instantané initial est prêt à être utilisé.  
  
10. Lorsque l'Agent de fusion pour un Abonné se connecte pour la première fois, un instantané partitionné est généré automatiquement.  
  
#### Pour créer une publication et prégénérer ou actualiser automatiquement des instantanés  
  
1.  Utilisez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe pour définir une publication de fusion. Pour plus d'informations, voir [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Utilisez le <xref:Microsoft.SqlServer.Replication.MergeArticle> propriété pour ajouter des articles à la publication. Spécifiez le <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> propriété pour au moins un article qui définit le filtre paramétrable et créez tous les <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> les objets qui définissent les filtres de jointure entre les articles. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Si la valeur de <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> est **false**, appelez <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> pour créer le travail de l’agent de capture instantanée pour cette publication.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> Procédé de la <xref:Microsoft.SqlServer.Replication.MergePublication> objet créé à l’étape 1. Cette méthode démarre le travail de l'agent qui génère l'instantané initial. Pour plus d'informations sur la génération d'un instantané initial et la définition d'une planification personnalisée pour l'Agent d'instantané, consultez [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
5.  Recherchez une valeur de **true** pour la <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> propriété pour déterminer quand l’instantané initial est prêt à être utilisé.  
  
6.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePartition> puis définissez les critères de filtrage paramétrés pour l’abonné à l’aide d’une ou les deux propriétés suivantes :  
  
    -   Si la partition de l’abonné est définie par le résultat de [SUSER_SNAME & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/suser-sname-transact-sql.md), utilisez <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A>.  
  
    -   Si la partition de l’abonné est définie par le résultat de [HOST_NAME & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/host-name-transact-sql.md) ou une surcharge de cette fonction, utilisez <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A>.  
  
7.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> puis définissez la propriété de même qu’à l’étape 6.  
  
8.  Utilisez le <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> classe pour définir une planification pour la génération de l’instantané filtré pour la partition d’abonné.  
  
9. À l’aide de l’instance de <xref:Microsoft.SqlServer.Replication.MergePublication> à l’étape 1, appelez <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergePartition%2A>. Passez le <xref:Microsoft.SqlServer.Replication.MergePartition> objet à l’étape 6.  
  
10. À l’aide de l’instance de <xref:Microsoft.SqlServer.Replication.MergePublication> à l’étape 1, appelez le <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergeDynamicSnapshotJob%2A> (méthode). Passez le <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> objet de l’étape 7 et <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> objet à l’étape 8.  
  
11. Appelez <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergeDynamicSnapshotJobs%2A>, puis recherchez le <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> objet pour le travail de capture instantanée partitionnée nouvellement ajouté dans le tableau retourné.  
  
12. Obtenir le <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob.Name%2A> propriété pour la tâche.  
  
13. Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
14. Créez une instance de serveur de gestion objets SMO (SQL) <xref:Microsoft.SqlServer.Management.Smo.Server> classe, en passant le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet à l’étape 13.  
  
15. Créez une instance de la <xref:Microsoft.SqlServer.Management.Smo.Agent.Job> classe, en passant le <xref:Microsoft.SqlServer.Management.Smo.Server.JobServer%2A> propriété de la <xref:Microsoft.SqlServer.Management.Smo.Server> objet à l’étape 14 et le nom du travail à l’étape 12.  
  
16. Appelez le <xref:Microsoft.SqlServer.Management.Smo.Agent.Job.Start%2A> méthode pour démarrer le travail de capture instantanée.  
  
17. Répétez les étapes 6 à 16 pour chaque Abonné.  
  
#### Pour créer une publication et créer manuellement des instantanés pour chaque partition  
  
1.  Utilisez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe pour définir une publication de fusion. Pour plus d'informations, voir [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Utilisez le <xref:Microsoft.SqlServer.Replication.MergeArticle> propriété pour ajouter des articles à la publication, spécifiez la <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> propriété pour au moins un article qui définit le filtre paramétrable et créez tous les <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> les objets qui définissent les filtres de jointure entre les articles. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Générez l'instantané initial. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
4.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> et définissez les propriétés requises suivantes :  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - nom du serveur de publication  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - nom de la base de données de publication  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - nom de la publication  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - nom du serveur de distribution  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -valeur <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> utilisé l’authentification intégrée de Windows ou une valeur de <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> à utiliser l’authentification SQL Server.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -valeur <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> utilisé l’authentification intégrée de Windows ou une valeur de <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> à utiliser l’authentification SQL Server.  
  
5.  Définir une valeur de <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> pour <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
6.  Définissez une ou plusieurs des propriétés suivantes pour définir les paramètres de partitionnement :  
  
    -   Si la partition de l’abonné est définie par le résultat de [SUSER_SNAME & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/suser-sname-transact-sql.md), utilisez <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterLogin%2A>.  
  
    -   Si la partition de l’abonné est définie par le résultat de [HOST_NAME & #40 ; Transact-SQL & #41 ;](../../t-sql/functions/host-name-transact-sql.md) ou une surcharge de cette fonction, utilisez <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterHostName%2A>.  
  
7.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> .  
  
8.  Répétez les étapes 4 à 7 pour chaque Abonné.  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple crée une publication de fusion qui permet aux Abonnés de demander la génération d'instantanés.  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
 Cet exemple crée manuellement la partition de l'Abonné et l'instantané filtré pour une publication de fusion avec des filtres de lignes paramétrables.  
  
 [!code-csharp[HowTo#rmo_CreateMergePartition](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepartition)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePartition](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepartition)]  
  
 Cet exemple lance manuellement l'Agent d'instantané pour qu'il génère l'instantané des données filtrées pour un Abonné à une publication de fusion avec des filtres de lignes paramétrables.  
  
 [!code-csharp[HowTo#rmo_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatefilteredsnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatefilteredsnapshot)]  
  
## Voir aussi  
 [Filtres de lignes paramétrés](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Concepts liés aux procédures stockées système de réplication](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Instantanés des publications de fusion avec des filtres paramétrés](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  