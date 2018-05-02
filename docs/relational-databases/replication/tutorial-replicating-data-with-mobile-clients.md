---
title: 'Tutoriel : Configurer la réplication entre un serveur et des clients mobiles (réplication de fusion) | Microsoft Docs'
ms.custom: ''
ms.date: 04/03/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d9751b7adc3d2cd4169bcd6b3a174de720c05eb9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-configure-replication-between-a-server-and-mobile-clients-merge"></a>Tutoriel : Configurer la réplication entre un serveur et des clients mobiles (réplication de fusion)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
La réplication de fusion constitue une bonne solution au problème de transfert des données entre un serveur central et des clients mobiles qui ne sont connectés que de façon occasionnelle. À l’aide des Assistants de réplication, vous pouvez aisément configurer et administrer une topologie de réplication de fusion. Ce didacticiel vous explique comment configurer une topologie de réplication pour des clients mobiles.  Pour plus d’informations sur la réplication de fusion, consultez [Présentation de la réplication de fusion](https://docs.microsoft.com/en-us/sql/relational-databases/replication/merge/merge-replication)
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
Dans ce tutoriel, vous allez apprendre à utiliser la réplication de fusion pour publier des données issues d’une base de données centrale dans un ou plusieurs comptes d’utilisateurs mobiles, afin que chaque utilisateur obtienne le sous-ensemble de données filtré dont il a besoin. 

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> * Configurer un serveur de publication pour la réplication de fusion
> * Ajouter un abonné mobile à la publication de fusion
> * Synchroniser l’abonnement avec la publication de fusion
  
## <a name="prerequisites"></a>Prerequisites  
Ce tutoriel est destiné aux utilisateurs qui sont familiers des opérations essentielles de base de données, mais pas de la réplication. Avant de commencer ce tutoriel, vous devez effectuer le [Tutoriel : Préparation du serveur à la réplication](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Pour utiliser ce tutoriel, votre système doit être doté de SQL Server Management Studio et des composants suivants :  
  
-   Sur le serveur de publication (source)  
  
    -   N’importe quelle édition de SQL Server, à l’exception de SQL Server Express et SQL Server Compact. Ces éditions ne peuvent pas constituer un serveur de publication de réplication.   
    -   Exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut.  
  
-   Serveur de l'Abonné (destination) :  
  
    -   N’importe quelle édition de SQL Server, à l’exception de [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] n'est pas pris en charge par la publication créée dans ce didacticiel. 

- Installez [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Téléchargez un [exemple de base de données AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Pour obtenir des instructions sur la restauration d’une base de données dans SSMS, consultez [Restauration d’une base de données](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).  
 
  
>[!NOTE]
> - La réplication n’est pas prise en charge sur les serveurs SQL Server qui sont séparés de plus de deux versions. Pour plus d’informations, consultez [Supported SQL Versions in Repl Topology](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/) (Versions de SQL prises en charge dans la topologie de réplication).
> - Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez vous connecter au serveur de publication et à l’Abonné à l’aide d’un identifiant de connexion membre du rôle serveur fixe **sysadmin** . Pour plus d’informations sur le rôle sysadmin, consultez [Rôles de niveau serveur](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles).  
  
  
**Durée estimée pour effectuer ce tutoriel : 60 minutes.**  
  
## <a name="configure-a-publisher-for-merge-replication"></a>Configurer un serveur de publication pour la réplication de fusion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Dans cette leçon, vous créez une publication de fusion à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour publier un sous-ensemble des tables **Employee**, **SalesOrderHeader** et **SalesOrderDetail** dans l’exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Ces tables sont filtrées avec des filtres de lignes paramétrables pour que chaque abonnement contienne une partition unique des données. Vous ajoutez également la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée par l’Agent de fusion à la liste d’accès à la publication.  
  
### <a name="create-merge-publication-and-define-articles"></a>Créer une publication de fusion et définir des articles  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2. Pour démarrer **SQL Server Agent**, cliquez dessus avec le bouton droit dans **l’Explorateur d’objets**, puis sélectionnez **Démarrer**. Si l’agent ne démarre pas, vous devez le démarrer manuellement à partir du **Gestionnaire de configuration SQL Server**.  
3. Développez le dossier **Réplication**, cliquez avec le bouton droit sur **Publications locales**, puis sélectionnez **Nouvelle publication**.  L’Assistant Configuration de la publication démarre :  

    ![Assistant Nouvelle publication](media/tutorial-replicating-data-between-continuously-connected-servers/newpublication.png)
  
3.  Dans la page Base de données de publication, sélectionnez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], puis sélectionnez **Suivant**. 

      
4.  Dans la page Type de publication, sélectionnez **Publication de fusion**, puis sélectionnez **Suivant**.  
    A. Dans la page Types d’Abonnés, vérifiez que seul [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure est sélectionné, puis sélectionnez **Suivant** : 

    ![Réplication de fusion](media/tutorial-replicating-data-with-mobile-clients/mergerpl.png)
  
   
6.  Dans la page Articles, développez le nœud **Tables**, puis sélectionnez les trois tables suivantes : **Employee**, **SalesOrderHeader** et **SalesOrderDetail**. Sélectionnez **Suivant** :  

    ![Articles de fusion](media/tutorial-replicating-data-with-mobile-clients/mergearticles.png)

    >[!NOTE]
    > La table Employee contient une colonne (OrganizationNode) avec le type de données hierarchyid, qui est uniquement pris en charge pour la réplication dans SQL 2017. Si vous utilisez une version antérieure à SQL 2017, vous verrez un message au bas de l’écran vous informant que l’utilisation de cette colonne dans une réplication bidirectionnelle peut entraîner une perte de données. Pour les besoins de ce tutoriel, vous pouvez ignorer ce message. Toutefois, vous ne devez pas répliquer ce type de données dans un environnement de production, sauf si vous utilisez la build prise en charge. Pour plus d’informations sur la réplication du type de données hierarchyid, consultez [Utilisation de colonnes hierarchyid dans les tables répliquées](https://docs.microsoft.com/en-us/sql/t-sql/data-types/hierarchyid-data-type-method-reference#using-hierarchyid-columns-in-replicated-tables).
    
  
7.  Dans la page Filtrer les lignes de la table, sélectionnez **Ajouter**, puis **Ajouter un filtre**.  
  
8.  Dans la boîte de dialogue **Ajouter un filtre**, sélectionnez **Employee (HumanResources)** sous **Select the table to filter** (Sélectionnez la table à filtrer). Sélectionnez la colonne **LoginID**, sélectionnez la flèche droite pour ajouter la colonne à la clause WHERE de la requête de filtre, puis modifiez la clause WHERE comme illustré ci-après :  
  
    ```sql 
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
    A. Sélectionnez **Une ligne de cette table ira à un seul abonnement**, puis **OK** :  
 
    ![Ajouter un filtre](media/tutorial-replicating-data-with-mobile-clients/mergeaddfilter.png)

    
  
10. Dans la page **Filtrer les lignes de la table**, sélectionnez **Employee (HumanResources)**. Ensuite, sélectionnez **Ajouter**, puis **Ajouter une jointure pour étendre le filtre sélectionné**.  
  
    A. Dans la boîte de dialogue **Ajouter une jointure**, sélectionnez **Sales.SalesOrderHeader** sous **Table jointe**. Sélectionnez **Write the join statement manually** (Écrire l’instruction de jointure manuellement), puis finalisez l’instruction de jointure de la façon suivante :  
  
    ```sql  
    ON [Employee].[BusinessEntityID] =  [SalesOrderHeader].[SalesPersonID] 
    ```  
  
    B. Dans **Spécifiez les options de jointure**, sélectionnez **Clé unique**, puis sélectionnez **OK** :

    ![Ajouter une jointure au filtre](media/tutorial-replicating-data-with-mobile-clients/mergeaddjoin.png)

  
13. Dans la page Filtrer les lignes de la table, sélectionnez **SalesOrderHeader**. Ensuite, sélectionnez **Ajouter**, puis **Ajouter une jointure pour étendre le filtre sélectionné**.  
  
    A. Dans la boîte de dialogue **Ajouter une jointure** , sélectionnez **Sales.SalesOrderDetail** sous **Table jointe**.    
    B. Sélectionnez **Utiliser le générateur pour créer l’instruction**.  
    c. Dans la zone **d’aperçu**, vérifiez que l’instruction de jointure ressemble à ceci :  
  
    ```sql  
    ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID] 
    ```  
  
    d. Dans **Spécifiez les options de jointure**, sélectionnez **Clé unique**, puis sélectionnez **OK**. Sélectionnez **Suivant** : 

       ![Joindre des tables de commandes client](media/tutorial-replicating-data-with-mobile-clients/joinsalestables.png)
  
21. Sélectionnez **Créer un instantané immédiatement**, décochez **Planifier l’exécution de l’Agent d’instantané aux heures suivantes**, puis sélectionnez **Suivant** :  

    ![Créer un instantané immédiatement](media/tutorial-replicating-data-with-mobile-clients/snapshotagent.png)
  
22. Dans la page Sécurité de l’agent, sélectionnez **Paramètres de sécurité**, tapez <*nom_serveur_de_publication>***\repl_snapshot** dans la zone **Compte de processus**, fournissez le mot de passe du compte, puis sélectionnez **OK**. Sélectionnez **Suivant** :  

    ![Sécurité de l'Agent d'instantané](media/tutorial-replicating-data-with-mobile-clients/snapshotagentsecurity.png)
  
23. Dans la page **Terminer l’Assistant**, entrez **AdvWorksSalesOrdersMerge** dans la zone **Nom de la publication**, puis sélectionnez **Terminer** :  

    ![Nom de la réplication de fusion](media/tutorial-replicating-data-with-mobile-clients/namemergerepl.png)
  
24. Une fois la publication créée, sélectionnez **Fermer**. Sous le nœud **Réplication**, dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur **Publications locales** puis sur **Actualiser** pour afficher la nouvelle réplication de fusion.  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Pour afficher l'état d'une génération d'instantané  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier Publications locales, cliquez avec le bouton droit sur **AdvWorksSalesOrdersMerge**, puis sélectionnez **Afficher l’état de l’Agent d’instantané** :  

    ![Afficher l’état de l’Agent d’instantané](media/tutorial-replicating-data-with-mobile-clients/viewsnapshotagentstatus.png)
  
3.  L'état en cours du travail de l'Agent d'instantané pour la publication s'affiche. Vérifiez que le travail d'instantané a bien réussi avant de passer à la leçon suivante.  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a>Pour ajouter la connexion de l'Agent de fusion à la liste d'accès à la publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier Publications locales, cliquez avec le bouton droit sur **AdvWorksSalesOrdersMerge**, puis sélectionnez **Propriétés**.  
  
    A. Sélectionnez la page **Liste d’accès à la publication**, puis sélectionnez **Ajouter**. 
  
    B. Dans la boîte de dialogue Ajouter un accès à une publication, sélectionnez <*nom_ordinateur_serveur_de_publication>***\repl_merge**, puis sélectionnez **OK**. Sélectionnez **OK** : 

    ![Fusionner la liste d’accès à la publication](media/tutorial-replicating-data-with-mobile-clients/mergepal.png) 

  
**Voir aussi** :  
[Filtrer des données publiées](../../relational-databases/replication/publish/filter-published-data.md)  
[Filtres de lignes paramétrés](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
[Définir un article](../../relational-databases/replication/publish/define-an-article.md)  
  
  
## <a name="creating-a-subscription-to-the-merge-publication"></a>Création d'un abonnement à la publication de fusion
Dans cette section, vous allez ajouter un abonnement à la publication de fusion que vous avez créée. Ce tutoriel utilise l’abonné distant (NODE2\SQL2016). Puis, vous définirez les autorisations sur la base de données d'abonnement et génèrerez manuellement l'instantané filtré des données du nouvel abonnement.   
  
### <a name="add-a-subscriber-for-merge-publication"></a>Ajouter un abonné à la publication de fusion
  
1.  Connectez-vous à l’abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur. Développez le dossier **Réplication**, cliquez avec le bouton droit sur le dossier **Abonnements locaux**, puis sélectionnez **Nouveaux abonnements**. L’Assistant Nouvel abonnement démarre :

    ![Nouvel abonnement](media/tutorial-replicating-data-with-mobile-clients/newsub.png)
  
2.  Dans la page **Publication**, sélectionnez **Rechercher un serveur de publication SQL** dans la liste **Serveur de publication**.  
  
    A. Dans la boîte de dialogue **Se connecter au serveur**, entrez le nom de l’instance du serveur de publication dans la zone **Nom du serveur**, puis sélectionnez **Se connecter** : 

    ![Ajouter un serveur de publication dans la boîte de dialogue Publication](media/tutorial-replicating-data-with-mobile-clients/publication.png)
  
4.  Sélectionnez **AdvWorksSalesOrdersMerge**, puis **Suivant**.  
  
5.  Dans la page Emplacement de l’Agent de fusion, sélectionnez **Exécuter chaque agent sur son Abonné**, puis sélectionnez **Suivant** :  

    ![Abonnement extrait](media/tutorial-replicating-data-with-mobile-clients/pullsub.png)
  
6.  Dans la page Abonnés, sélectionnez le nom d’instance du serveur de l’Abonné, puis, sous **Base de données d’abonnement**, sélectionnez **Nouvelle base de données** dans la liste.  
  
    A. Dans la boîte de dialogue **Nouvelle base de données**, entrez **SalesOrdersReplica** dans la zone **Nom de la base de données**, sélectionnez **OK**, puis **Suivant** : 

    ![Ajouter une base de données à l’abonné](media/tutorial-replicating-data-with-mobile-clients/addsubdb.png)
  
8.  Dans la page Sécurité de l’Agent de fusion, sélectionnez le bouton de sélection (**…**), entrez <*nom_serveur_de_publication>***\repl_merge** dans la zone **Compte de processus**. Fournissez le mot de passe de ce compte, sélectionnez **OK**, **Suivant**, puis une nouvelle fois **Suivant** :  

    ![Sécurité de l'agent de fusion](media/tutorial-replicating-data-with-mobile-clients/mergeagentsecurity.png)

9. Dans **Planification de synchronisation**, configurez la **Planification de l’agent** sur **Run on demand only** (Exécuter uniquement à la demande). Sélectionnez **Suivant** :  

    ![Planification de synchronisation](media/tutorial-replicating-data-with-mobile-clients/mergesyncschedule.png)
  
9. Dans la page Initialiser les abonnements, sélectionnez **Lors de la première synchronisation** dans la liste **À quel moment**, sélectionnez **Suivant**, puis une nouvelle fois **Suivant** : 

    ![Première synchronisation](media/tutorial-replicating-data-with-mobile-clients/firstsync.png)

10. Dans la page Valeurs de HOST_NAME, entrez **adventure-works\pamela0** dans la zone **Valeur de HOST_NAME**, puis sélectionnez **Terminer** :  

    ![HostName](media/tutorial-replicating-data-with-mobile-clients/hostname.png)
  
11. Sélectionnez à nouveau **Terminer** puis, une fois l’abonnement créé, sélectionnez **Fermer**.  

### <a name="setting-server-permissions-at-the-subscriber"></a>Définition des autorisations de serveur pour l’Abonné  
  
1.  Connectez-vous à l’Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis sélectionnez **Nouvelle connexion**.  
  
    A. Dans la page **Général**, sélectionnez **Rechercher**, entrez <*nom_ordinateur_abonné>***\repl_merge** dans le champ **Entrer le nom d’objet à sélectionner**, sélectionnez **Vérifier les noms**, puis sélectionnez **OK** : 
    
    ![Connexion à l’Abonné](media/tutorial-replicating-data-with-mobile-clients/sublogin.png)
  
1. Dans la page **Mappage d’utilisateur**, sélectionnez la base de données **SalesOrdersReplica**, puis sélectionnez le rôle **db_owner**.  Dans la page **Éléments sécurisables**, accordez l’autorisation 'Explicit' à **Alter Trace**. Sélectionnez **OK** :

    ![Configurer la connexion en tant que DBO sur l’Abonné](media/tutorial-replicating-data-with-mobile-clients/setdbo.png)
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>Pour créer l'instantané filtré des données de l'abonnement  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales**, cliquez avec le bouton droit sur la publication **AdvWorksSalesOrdersMerge**, puis sélectionnez **Propriétés**.  
   
    A. Sélectionnez la page **Partitions de données**, puis sélectionnez **Ajouter**.   
    B. Dans la boîte de dialogue **Ajouter une partition de données**, entrez **adventure-works\pamela0** dans la zone **Valeur de HOST_NAME**, puis sélectionnez **OK**.  
    c. Sélectionnez la partition nouvellement ajoutée, sélectionnez **Générer les instantanés sélectionnés maintenant**, puis sélectionnez **OK** : 

    ![Ajouter une partition](media/tutorial-replicating-data-with-mobile-clients/partition.png)
  
  
**Voir aussi** :  
[S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
[Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)  
[Instantanés des publications de fusion avec des filtres paramétrés](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  

## <a name="synchronize-the-subscription-to-the-merge-publication"></a>Synchroniser l’abonnement avec la publication de fusion

Dans cette section, vous allez démarrer l’Agent de fusion pour initialiser l’abonnement à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous allez également utiliser cette procédure pour effectuer la synchronisation avec le serveur de publication.   
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Pour démarrer la synchronisation et initialiser l'abonnement  
  
1.  Connectez-vous à l’Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
2. Vérifiez que **SQL Server Agent** est en cours d’exécution. Si ce n’est pas le cas, cliquez avec le bouton droit sur **SQL Server Agent** dans **l’Explorateur d’objets**, puis sélectionnez **Démarrer**. Si l’agent ne démarre pas, vous devez le démarrer manuellement à partir du **Gestionnaire de configuration SQL Server**. 
  
2.  Développez le nœud **Réplication**. Dans le dossier **Abonnements locaux**, cliquez avec le bouton droit sur l’abonnement de la base de données **SalesOrdersReplica**, puis sélectionnez **Afficher l’état de synchronisation**.  
  
    A. Sélectionnez **Démarrer** pour initialiser l’abonnement : 

    ![État de la synchronisation](media/tutorial-replicating-data-with-mobile-clients/mergesyncstatus.png)
    
  
  
### <a name="next-steps"></a>Next Steps  
Vous avez correctement configuré votre serveur de publication et votre Abonné pour la réplication de fusion.  Vous pouvez aussi insérer, mettre à jour ou supprimer les données des tables **SalesOrderHeader** ou **SalesOrderDetail** sur le serveur de publication ou l’Abonné, répéter cette procédure quand la connexion réseau est disponible pour synchroniser les données entre le serveur de publication et l’Abonné, puis interroger les tables **SalesOrderHeader** ou **SalesOrderDetail** de l’autre serveur pour visualiser les modifications répliquées.  
  
**Voir aussi** :   
[Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Synchronisez les données](../../relational-databases/replication/synchronize-data.md)  
[Synchroniser un abonnement par extraction (pull)](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  
  
