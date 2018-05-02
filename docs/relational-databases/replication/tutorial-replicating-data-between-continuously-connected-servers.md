---
title: 'Tutoriel : Configurer la réplication entre deux serveurs intégralement connectés (réplication transactionnelle) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: de374f4372f62741ff3c49a9433cf339cecf3d26
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-configure-replication-between-two-fully-connected-servers-transactional"></a>Tutoriel : Configurer la réplication entre deux serveurs intégralement connectés (réplication transactionnelle)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
La réplication transactionnelle constitue une bonne solution au problème de transfert de données entre serveurs connectés en permanence. À l’aide de l’Assistant Réplication, vous pouvez aisément configurer et administrer une topologie de réplication. Ce tutoriel vous explique comment configurer une topologie de réplication transactionnelle dans le cas de serveurs connectés en permanence. Pour plus d’informations sur le fonctionnement de la réplication transactionnelle, consultez [Vue d’ensemble de la réplication transactionnelle](https://docs.microsoft.com/en-us/sql/relational-databases/replication/transactional/transactional-replication). 
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
Ce didacticiel vous explique comment publier des données d'une base de données sur une autre à l'aide de la réplication transactionnelle. 

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> * Créer un serveur de publication par le biais de la réplication transactionnelle
> * Créer un Abonné pour le serveur de publication transactionnelle
> * Valider l’abonnement et mesurer la latence
> * Utiliser une méthodologie de résolution des erreurs
  
  
## <a name="prerequisites"></a>Prerequisites  
Ce didacticiel est destiné aux utilisateurs qui sont familiers des opérations élémentaires de base de données, mais dont l'expérience en matière de réplication est limitée. Pour suivre ce didacticiel, vous devez avoir terminé le didacticiel précédent, [Préparation du serveur pour la réplication](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Pour que vous puissiez utiliser ce tutoriel, votre système doit être doté de SQL Server Management Studio (SSMS) et des composants suivants :  
  
-   Sur le serveur de publication (source)  
  
    -   Toute édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l’exception de SQL Server Express ou SQL Compact. Ces éditions ne peuvent pas constituer des serveurs de publication de réplication.   
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] : exemple de base de données. Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut.  
  
-   Serveur de l'Abonné (destination) :  
  
    -   Toute édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sauf [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] ne peut pas être un abonné dans une réplication transactionnelle.  
  
- Installez [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Téléchargez un [exemple de base de données AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Pour obtenir des instructions sur la restauration d’une base de données dans SSMS, consultez [Restauration d’une base de données](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 
 
>[!NOTE]
> - La réplication n’est pas prise en charge sur les serveurs SQL Server qui sont séparés de plus de deux versions. Pour plus d’informations, consultez [Supported SQL Versions in Repl Topology](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/) (Versions de SQL prises en charge dans la topologie de réplication).
> - Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez vous connecter au serveur de publication et à l’Abonné à l’aide d’un identifiant de connexion membre du rôle serveur fixe **sysadmin** . Pour plus d’informations sur le rôle sysadmin, consultez [Rôles de niveau serveur](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles).  
  
  
**Durée estimée pour effectuer ce tutoriel : 60 minutes.**  
  
## <a name="configure-the-publisher-for-transactional-replication"></a>Configurer le serveur de publication pour la réplication transactionnelle
Dans cette section, vous créez une publication transactionnelle en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour publier un sous-ensemble filtré de la table **Product** de l’exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Vous allez aussi ajouter à la liste d'accès à la publication le compte de connexion SQL Server utilisée par l'Agent de distribution. Avant de commencer ce didacticiel, vous devez avoir terminé le didacticiel précédent, [Préparation du serveur à la réplication](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).


### <a name="create-a-publication-and-define-articles"></a>Créer une publication et définir des articles
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2. Cliquez avec le bouton droit sur **SQL Server Agent** et sélectionnez **Démarrer**. SQL Server Agent doit être en cours d’exécution pour que vous puissiez créer la publication. Si l’agent ne démarre pas, vous devez le démarrer manuellement à partir du **Gestionnaire de configuration SQL Server**. 
3. Développez le dossier **Réplication**, cliquez avec le bouton droit sur le dossier **Publications locales**, puis sélectionnez **Nouvelle publication**.  Cette opération démarre l’Assistant Configuration de la publication :  

    ![Nouvelle publication](media/tutorial-replicating-data-between-continuously-connected-servers/newpublication.png)
  
  
3. Dans la page Base de données de publication, sélectionnez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], puis sélectionnez **Suivant**.  
  
4. Dans la page Type de publication, sélectionnez **Publication transactionnelle**, puis sélectionnez **Suivant** :  

    ![Réplication transactionnelle](media/tutorial-replicating-data-between-continuously-connected-servers/tranrepl.png)
  
5. Dans la page Articles, développez le nœud **Tables**, puis cochez la case **Product**. Ensuite, développez **Product** et décochez les cases en regard de **ListPrice** et **StandardCost**. Sélectionnez **Suivant** :  

    ![Articles à publier](media/tutorial-replicating-data-between-continuously-connected-servers/replarticles.png)
  
6. Dans la page Filtrer les lignes de la table, sélectionnez **Ajouter**.   
  
7. Dans la boîte de dialogue **Ajouter un filtre**, sélectionnez la colonne **SafetyStockLevel**, puis sélectionnez la flèche droite pour ajouter la colonne à la clause WHERE de la requête de filtre. Ensuite, entrez le modificateur de la clause WHERE comme suit :  
  
    ```sql  
    WHERE [SafetyStockLevel] < 500  
    ```
  
    ![Instruction de filtrage](media/tutorial-replicating-data-between-continuously-connected-servers/filter.png)
  
8. Sélectionnez **OK**, puis **Suivant**.  
  
9. Cochez la case **Créer un instantané immédiatement et garder ce dernier disponible pour l’initialisation des abonnements** et sélectionnez **Suivant** :  

    ![Agent d'instantané](media/tutorial-replicating-data-between-continuously-connected-servers/snapshot.png)
  
10. Dans la page Sécurité de l’agent, décochez la case **Utiliser les paramètres de sécurité de l’Agent d’instantané** .   
  
    A. Sélectionnez **Paramètres de sécurité** pour l’Agent d’instantané, entrez <*nom_ordinateur_serveur_de_publication>***\repl_snapshot** dans la zone **Compte de processus**, spécifiez le mot de passe du compte, puis sélectionnez **OK** :  

    ![Sécurité de l'Agent d'instantané](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagentsecurity.png)
  
12. Répétez l’étape précédente pour définir <*nom_ordinateur_serveur_de_publication*>**\repl_logreader** comme compte de processus de l’Agent de lecture du journal, puis sélectionnez **OK** :  

    ![Sécurité de l'Agent de lecture du journal](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderagentsecurity.png)   

  
13. Dans la page Terminer l’Assistant, entrez **AdvWorksProductTrans** dans la zone **Nom de la publication**, puis sélectionnez **Terminer** :  

    ![Nommer la publication](media/tutorial-replicating-data-between-continuously-connected-servers/advworksproducttrans.png)
  
14. Une fois la publication créée, sélectionnez **Fermer** pour terminer l’Assistant. 

    Vous pouvez rencontrer l’erreur suivante si SQL Server Agent n’est pas en cours d’exécution quand vous essayez de créer la publication. Cette erreur indique que votre publication a été créée avec succès, mais que l’Agent d’instantané n’a pas pu démarrer. Dans ce cas, vous devez démarrer SQL Server Agent, puis démarrer manuellement l’Agent d’instantané. La section suivante indique comment procéder : 

    ![L’Agent d’instantané ne peut pas démarrer](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagenterror.png)
    
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Pour afficher l'état d'une génération d'instantané  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales**, cliquez avec le bouton droit sur **AdvWorksProductTrans**, puis sélectionnez **Afficher l’état de l’Agent d’instantané** :  

    ![État de l’Agent d’instantané](media/tutorial-replicating-data-between-continuously-connected-servers/viewsnapshot.png)
  
3.  L'état en cours du travail de l'Agent d'instantané pour la publication s'affiche. Vérifiez que le travail d’instantané a bien réussi avant de passer à la section suivante.
          
    Si SQL Server Agent n’était pas en cours d’exécution quand vous avez créé la publication, une mention indique que l’Agent d’instantané n’a jamais été exécuté quand vous vérifiez **l’État de l’Agent d’instantané** pour la publication. Dans ce cas, sélectionnez **Démarrer** pour démarrer l’Agent d’instantané : 

       ![Démarrer l’Agent d’instantané](media/tutorial-replicating-data-between-continuously-connected-servers/startsnapshotagent.png)
     
       Si une erreur apparaît, consultez [Résoudre les erreurs liées à l’Agent d’instantané](#troubleshoot-erros-with-snapshot-agent). 

  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a>Pour ajouter la connexion de l'Agent de distribution à la liste d'accès à la publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales**, cliquez avec le bouton droit sur **AdvWorksProductTrans**, puis sélectionnez **Propriétés**.  La boîte de dialogue **Propriétés de la publication** s’affiche.    
  
    A. Sélectionnez la page **Liste d’accès à la publication**, puis sélectionnez **Ajouter**.  
    B. Dans la boîte de dialogue **Ajouter un accès à une publication**, sélectionnez <*nom_ordinateur_serveur_de_publication>***\repl_distribution** et sélectionnez **OK**. Sélectionnez **OK** :

   
   ![Ajouter la connexion à la liste d’accès à la publication](media/tutorial-replicating-data-between-continuously-connected-servers/tranreplproperties.png)

**Voir aussi** :  
[Concepts de programmation en matière de réplication](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  

## <a name="create-a-subscription-to-the-transactional-publication"></a>Créer un abonnement à la publication transactionnelle
Dans cette section, vous allez ajouter un Abonné à la publication qui a été créée. Ce tutoriel utilise un Abonné distant (NODE2\SQL2016), mais vous pouvez également ajouter un abonnement localement au serveur de publication. 

### <a name="to-create-the-subscription"></a>Pour créer l'abonnement  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales**, cliquez avec le bouton droit sur la publication **AdvWorksProductTrans**, puis sélectionnez **Nouveaux abonnements**.  L’Assistant Nouvel abonnement démarre : 
 
    ![Nouvel abonnement](media/tutorial-replicating-data-between-continuously-connected-servers/newsub.png)     
  
3.  Dans la page Publication, sélectionnez **AdvWorksProductTrans**, puis sélectionnez **Suivant** :  

    ![Sélectionner le serveur de publication Trans](media/tutorial-replicating-data-between-continuously-connected-servers/selectpub.png)
  
4.  Dans la page Emplacement de l’Agent de distribution, sélectionnez **Exécuter tous les agents sur le serveur de distribution**, puis sélectionnez **Suivant**.  Pour plus d’informations sur les abonnements par extraction et par émission de données, consultez [S’abonner à des publications](https://docs.microsoft.com/en-us/sql/relational-databases/replication/subscribe-to-publications) :

    ![Exécuter des agents sur le serveur de distribution](media/tutorial-replicating-data-between-continuously-connected-servers/runagentsatdist.png)
  
5.  Dans la page Abonnés, si le nom de l’instance de l’Abonné n’est pas affiché, sélectionnez **Ajouter un Abonné**, puis sélectionnez **Ajouter un Abonné SQL Server** dans la liste déroulante. Cette opération ouvre la boîte de dialogue **Se connecter au serveur**. Entrez le nom de l’instance de l’Abonné, puis sélectionnez **Se connecter**.  
    
    A. Une fois l’Abonné ajouté, cochez la case en regard du nom de son instance. Ensuite, sélectionnez **Nouvelle base de données** sous **Base de données d’abonnement** :   

  ![Ajouter un Abonné SQL Server](media/tutorial-replicating-data-between-continuously-connected-servers/addsub.png)

7. Cette action ouvre la boîte de dialogue **Nouvelle base de données**. Entrez **ProductReplica** dans la zone **Nom de la base de données**, sélectionnez **OK**, puis sélectionnez **suivant** : 
  
    ![Base de données ProductReplica](media/tutorial-replicating-data-between-continuously-connected-servers/productreplica.png)
  
8.  Dans la boîte de dialogue **Sécurité de l’Agent de distribution**, sélectionnez le bouton représentant des points de suspension (**…**). Entrez <*nom_ordinateur_serveur_de_publication>***\repl_distribution** dans la zone **Compte de processus**, entrez le mot de passe du compte, sélectionnez **OK**, puis **Suivant** :

    ![Ajouter un compte de distribution](media/tutorial-replicating-data-between-continuously-connected-servers/adddistaccount.png)
  
9. Sélectionnez **Terminer** pour accepter les valeurs par défaut des pages restantes et terminer l’Assistant.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Définition des autorisations de base de données sur l'Abonné  
  
1.  Connectez-vous à l’Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis sélectionnez **Nouvelle connexion**.     
  
    A. Dans la page **Général**, sous **Nom de connexion**, sélectionnez **Rechercher**, puis ajoutez le nom de connexion pour <*nom_ordinateur_Abonné>***\repl_distribution**.
    B. Dans la page **Mappages d’utilisateur**, accordez la connexion **db_owner** pour la base de données **ProductReplica** : 

    ![Connexion à l’Abonné](media/tutorial-replicating-data-between-continuously-connected-servers/loginforsub.png)

2. Sélectionnez **OK** pour fermer la boîte de dialogue **Nouvelle connexion**. 

  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>Pour afficher l'état de synchronisation de l'abonnement  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales**, développez la publication **AdvWorksProductTrans**, cliquez avec le bouton droit sur l’abonnement dans la base de données **ProductReplica**, puis sélectionnez **Afficher l’état de synchronisation**. L’état de synchronisation de l’abonnement s’affiche :  
    ![Afficher l’état de synchronisation](media/tutorial-replicating-data-between-continuously-connected-servers/viewsyncstatus.png)
3.  Si l’abonnement n’apparaît pas sous **AdvWorksProductTrans**, appuyez sur F5 pour actualiser la liste.  
  
**Voir aussi** :  
[Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)  
[S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  

## <a name="measuring-replication-latency"></a>Mesure de la latence de la réplication
Dans cette section, vous allez utiliser les jetons de suivi pour vérifier que les modifications sont bien répliquées sur l’Abonné et pour déterminer la latence. La latence est le temps nécessaire pour qu’une modification apportée sur le serveur de publication apparaisse sur l’Abonné.
  
1. Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, cliquez avec le bouton droit sur le dossier **Réplication**, puis sélectionnez **Lancer le moniteur de réplication** :

    ![Lancer le moniteur de réplication](media/tutorial-replicating-data-between-continuously-connected-servers/launchreplmonitor.png)

2. Développez un groupe de serveurs de publication dans le volet gauche, développez une instance du serveur de publication, puis sélectionnez la publication **AdvWorksProductTrans**.  
  
    A. Sélectionnez l’onglet **Jetons de suivi**.  
    B. Sélectionnez **Insérer un suivi**.    
    c. Affichez le temps écoulé pour le jeton de suivi dans les colonnes suivantes : **Du serveur de publication vers le serveur de distribution**, **Du serveur de distribution vers l'Abonné**et **Latence totale**. Une valeur **En attente** indique que le jeton n’a pas atteint un point donné :


   ![Jeton de suivi](media/tutorial-replicating-data-between-continuously-connected-servers/tracertoken.png)


**Voir aussi**   
[Mesurer la latence et valider les connexions pour la réplication transactionnelle](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

## <a name="error-troubleshooting-methodology"></a>Utiliser une méthodologie de résolution des erreurs
Cette section explique comment résoudre les échecs de synchronisation de réplication de base. Notez que cette section est destinée à vous montrer comment résoudre des problèmes à partir des composants de la réplication. Toutefois, les erreurs que vous êtes susceptible de rencontrer peuvent différer de celles décrites ici et, donc, nécessiter une résolution différente. Si tel est le cas, vous devez effectuer une résolution spécifique qui n’entre pas dans le cadre de ce tutoriel. 


### <a name="troubleshoot-errors-with-snapshot-agent"></a>Résoudre les erreurs liées à l’Agent d’instantané
**L’Agent d’instantané** est l’agent qui génère l’instantané et qui l’écrit dans le dossier d’instantanés spécifié. 

1. Pour voir l’état de l’Agent d’instantané, développez le nœud **Publications locales** sous Réplication, cliquez avec le bouton droit sur votre publication **AdvWorksProductTrans** > **Afficher l’état de l’Agent d’instantané**. 
2. Si une erreur est signalée dans **l’État de l’Agent d’instantané**, vous trouverez plus de détails dans l’historique des travaux **Agent d’instantané**. Pour y accéder, développez **SQL Server Agent** dans **l’Explorateur d’objets**, puis ouvrez le **Moniteur d’activité des travaux**. 

    A. Triez par **Catégorie** et identifiez **l’Agent d’instantané** d’après la catégorie REPL-Instantané. 

    B. Cliquez avec le bouton droit sur **l’Agent d’instantané**, puis choisissez **Afficher l’historique** : 

   ![Historique de l’Agent d’instantané](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagenthistory.png)
    
1. Dans **l’historique de l’Agent d’instantané**, sélectionnez l’entrée de journal appropriée. Elle se trouve généralement une ou deux lignes *avant* l’entrée indiquant l’erreur (les erreurs sont indiquées par une icône en forme de croix blanche sur fond rouge).  Passez en revue le texte du message dans la zone de texte sous les journaux : 

    ![Agent d’instantané : accès refusé](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotaccessdenied.png)

        The replication agent had encountered an exception.
        Exception Message: Access to path '\\node1\repldata.....' is denied.


  Si vos autorisations Windows ne sont pas configurées correctement pour le dossier d’instantanés, une erreur « accès refusé » apparaît pour **l’Agent d’instantané**. Vous devez alors vérifier les autorisations pour le compte <*nom_ordinateur_serveur_de_publication>***\repl_snapshot** sur le dossier repldata. Pour plus d’informations, consultez [Créer un partage pour le dossier d’instantanés et attribuer les autorisations](tutorial-preparing-the-server-for-replication.md#create-a-share-for-the-snapshot-folder-and-assign-permissions).

### <a name="troubleshoot-errors-with-log-reader-agent"></a>Résoudre les erreurs liées à l’Agent de lecture du journal
**L’Agent de lecture du journal** se connecte à votre base de données du serveur de publication, puis recherche, dans le journal des transactions, celles marquées pour la réplication. Il ajoute ensuite ces transactions à la base de données **Distribution**. 

1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, cliquez avec le bouton droit sur le dossier **Réplication**, puis sélectionnez **Lancer le moniteur de réplication** :  

    ![Lancer le moniteur de réplication](media/tutorial-replicating-data-between-continuously-connected-servers/launchreplmonitor.png)
  
    Le moniteur de réplication démarre : ![Moniteur de réplication](media/tutorial-replicating-data-between-continuously-connected-servers/replmonitor.png) 
   
2. L’icône en forme de croix blanche sur fond rouge indique que la publication ne se synchronise pas. Développez **Mes serveurs de publication** sur le gauche côté, puis développez le serveur de publication approprié.  
  
3.  Sélectionnez la publication **AdvWorksProductTrans** sur la gauche, puis recherchez l’icône en forme de croix blanche sur fond rouge sur l’un des onglets pour identifier l’emplacement du problème. En l’occurrence, cette icône se trouve sur l’onglet **Agents**, indiquant que l’un des Agents fait face à un problème : 

    ![Erreur d’agent](media/tutorial-replicating-data-between-continuously-connected-servers/agenterror.png)

4. Sélectionnez l’onglet **Agents** pour identifier l’Agent en question : 

    ![Échec de lecture du journal](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderagentfailure.png)


5. Cette vue montre deux Agents : **l’Agent d’instantané** et **l’Agent de lecture du journal**. Celui qui rencontre une erreur porte l’icône en forme de croix blanche sur fond rouge. En l’occurrence, il s’agit de **l’Agent de lecture du journal**. Double-cliquez sur la ligne qui signale l’erreur, en l’occurrence celle de **l’Agent de lecture du journal**. Cette action lance **l’Historique de l’Agent** associé à l’Agent que vous avez sélectionné ; en l’occurrence, il s’agit de l’historique de **l’Agent de lecture du journal**. Celui-ci fournit des informations détaillées sur l’erreur : 
    
    ![Erreur affectant l’Agent de lecture du journal](media/tutorial-replicating-data-between-continuously-connected-servers/logreadererror.png)

       Status: 0, code: 20011, text: 'The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.'.
       The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.
       Status: 0, code: 15517, text: 'Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission.'.
       Status: 0, code: 22037, text: 'The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.'.        

6. L’erreur susmentionnée est généralement due au fait que le propriétaire de la base de données du serveur de publication n’est pas défini correctement. En général, elle se produit quand une base de données a été restaurée. Pour vérifier ce point, développez **Bases de données** dans **l’Explorateur d’objets**, puis cliquez avec le bouton droit sur **AdventureWorks2012** > **Propriétés**. Vérifiez qu’un propriétaire existe sous la page **Fichiers**. Si ce champ est vide, c’est la cause probable du problème : 

    ![Propriétés de la base de données](media/tutorial-replicating-data-between-continuously-connected-servers/dbproperties.png)

7. Si le propriétaire est vide dans la page **Fichiers**, ouvrez une **Fenêtre de nouvelle requête** dans le contexte de la base de données **AdventureWorks2012**. Exécutez l’extrait de code T-SQL suivant :

    ```sql
    -- set the owner of the database to 'sa' or a specific user account, without the brackets. 
    EXEC sp_changedbowner '<useraccount>'
    -- example for sa: exec sp_changedbowner 'sa'
    -- example for user account: exec sp_changedbowner 'sqlrepro\administrator' 
    ```

8. Vous devez redémarrer **l’Agent de lecture du journal**. Pour ce faire, développez le nœud **SQL Server Agent** dans **l’Explorateur d’objets**, puis ouvrez le **Moniteur d’activité des travaux**. Triez par **Catégorie** et identifiez **l’Agent de lecture du journal** d’après la catégorie **REPL-LogReader**. Cliquez avec le bouton droit sur le travail **Agent de lecture du journal** et choisissez **Démarrer le travail à l’étape** : 

    ![Redémarrer l’Agent de lecture du journal](media/tutorial-replicating-data-between-continuously-connected-servers/startjobatstep.png)

9. Vérifiez que votre publication est maintenant en cours de synchronisation en rouvrant le **moniteur de réplication**. S’il n’est pas déjà ouvert, vous pouvez y accéder en cliquant avec le bouton droit sur **Réplication** dans **l’Explorateur d’objets**. 
10. Sélectionnez la publication **AdvWorksProductTrans**, sélectionnez l’onglet **Agents**, puis double-sélectionnez **l’Agent de lecture du journal** pour ouvrir l’historique de l’agent. Vous devez maintenant voir que **l’Agent de lecture du journal** est en cours d’exécution et soit qu’il réplique des commandes, soit qu’il ne dispose pas de transactions répliquées :

    ![Exécution de l’Agent de lecture du journal](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderrunning.png)

### <a name="troubleshoot-errors-with-distribution-agent"></a>Résoudre les erreurs liées à l’Agent de distribution
**L’agent de distribution** accepte des données qu’il trouve dans la base de données **Distribution**, puis les applique à l’Abonné. 

1. Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, cliquez avec le bouton droit sur le dossier **Réplication**, puis sélectionnez **Lancer le moniteur de réplication**.  
2. Dans **Moniteur de réplication**, sélectionnez la publication **AdvWorksProductTrans**, puis sélectionnez l’onglet **Tous les abonnements**. Cliquez avec le bouton droit sur l’abonnement, puis choisissez **Afficher les détails** :

    ![Afficher les détails du serveur de distribution](media/tutorial-replicating-data-between-continuously-connected-servers/viewdetails.png)

2. La boîte de dialogue **Historique du serveur de distribution vers l’Abonné** s’ouvre et donne des indications sur l’erreur à laquelle est confronté l’Agent : 

     ![Erreur dans l’historique de l’Agent de distribution](media/tutorial-replicating-data-between-continuously-connected-servers/disthistoryerror.png)
    
        Error messages:
        Agent 'NODE1\SQL2016-AdventureWorks2012-AdvWorksProductTrans-NODE2\SQL2016-7' is retrying after an error. 89 retries attempted. See agent job history in the Jobs folder for more details.

3. L’erreur indique que l’**Agent de distribution** fait une nouvelle tentative. Pour obtenir plus d’informations, développez **SQL Server Agent** dans **l’Explorateur d’objets** > **Moniteur d’activité des travaux**. Triez les travaux par **Catégorie**. 

    A. Identifiez **l’Agent de distribution** d’après la catégorie **REPL-Distribution**. Cliquez avec le bouton droit sur l’Agent, puis choisissez **Afficher l’historique** :

    ![Voir l’historique de l’Agent de distribution](media/tutorial-replicating-data-between-continuously-connected-servers/viewdistagenthistory.png)

5. Sélectionnez une des entrées d’erreur et consultez le texte de l’erreur en bas de la fenêtre :  

    ![Mot de passe incorrect pour l’Agent de distribution](media/tutorial-replicating-data-between-continuously-connected-servers/distpwwrong.png)
    
        Message:
        Unable to start execution of step 2 (reason: Error authenticating proxy NODE1\repl_distribution, system error: The user name or password is incorrect.)

6. Cette erreur indique que le mot de passe utilisé par **l’Agent de distribution** est incorrect. Pour résoudre ce problème, développez le nœud **Réplication** dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur l’abonnement, puis choisissez **Propriétés**. Sélectionnez le bouton représentant des points de suspension (...) à côté de **Compte de processus de l’agent**, puis modifiez le mot de passe :

    ![Modifier le mot de passe de l’Agent de distribution](media/tutorial-replicating-data-between-continuously-connected-servers/distagentpwchange.png)

7. Revenez au **moniteur de réplication**, en cliquant avec le bouton droit sur **Réplication** dans **l’Explorateur d’objets**. Une icône en forme de croix blanche sur fond rouge sous **Tous les abonnements** indique que **l’Agent de distribution** rencontre toujours une erreur. Ouvrez l’historique **Du serveur de distribution vers l’Abonné** en cliquant avec le bouton droit sur l’abonnement dans **Moniteur de réplication** > **Afficher les détails**. Ici, l’erreur est désormais différente : 

    ![L’Agent de distribution ne peut pas se connecter](media/tutorial-replicating-data-between-continuously-connected-servers/distagentcantconnect.png)
           
        Connecting to Subscriber 'NODE2\SQL2016'        
        Agent message code 20084. The process could not connect to Subscriber 'NODE2\SQL2016'.
        Number:  18456
        Message: Login failed for user 'NODE2\repl_distribution'.

8. Cette erreur indique que **l’Agent de distribution** n’a pas pu se connecter à l’Abonné, la connexion ayant échoué pour l’utilisateur **NODE2\repl_distribution**. Pour en savoir plus, connectez-vous à l’Abonné et ouvrez le **journal des erreurs SQL** *Actuel* sous le nœud **Gestion** dans **l’Explorateur d’objets** : 

    ![Échec de la connexion pour l’Abonné](media/tutorial-replicating-data-between-continuously-connected-servers/loginfailed.png) Si vous voyez cette erreur, cela signifie que la connexion est manquante sur l’Abonné. Pour résoudre ce problème, consultez [Définition des autorisations de base de données sur l’Abonné](#setting-database-permissions-at-the-subscriber).

9. Une fois que l’erreur de connexion a été résolue, revenez au **Moniteur de réplication**. Si tous les problèmes ont été traités, vous devez voir une flèche verte à côté du **Nom de la publication** et l’état **En cours d’exécution** sous **Tous les abonnements**. Cliquez avec le bouton droit sur **l’abonnement** pour relancer l’historique **Du serveur de distribution vers l’Abonné** afin de vérifier que tout est résolu. S’il s’agit de la première exécution de l’Agent de distribution, vous pouvez constater que l’instantané a été copié en bloc vers l’Abonné, comme indiqué dans l’image ci-dessous : 

     ![Réussite de l’Agent de distribution](media/tutorial-replicating-data-between-continuously-connected-servers/distagentsuccess.png)   

  ## <a name="next-steps"></a>Étapes suivantes
Vous avez correctement configuré votre serveur de publication et votre Abonné pour la réplication transactionnelle.  Vous pouvez maintenant insérer, mettre à jour ou supprimer des données dans la table **Product** sur le serveur de publication. Ensuite, vous pouvez interroger la table **Product** sur l’Abonné pour voir les modifications répliquées. L’article suivant va vous apprendre à configurer la réplication de fusion.  

Passez à l’article suivant pour en savoir plus
> [!div class="nextstepaction"]
> [Étapes suivantes](tutorial-replicating-data-with-mobile-clients.md)

  
