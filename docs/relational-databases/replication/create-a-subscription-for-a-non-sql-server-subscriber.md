---
title: "Cr&#233;er un abonnement pour un Abonn&#233; non-SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "subscriptions [SQL Server replication], non-SQL Server Subscribers"
  - "Subscribers [SQL Server replication], non-SQL Server Subscribers"
  - "abonnés non-SQL Server, abonnements"
ms.assetid: 5020ee68-b988-4d57-8066-67d183e61237
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Cr&#233;er un abonnement pour un Abonn&#233; non-SQL Server
  Cette rubrique explique comment créer un abonnement pour un abonné non-SQL Server dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. La réplication transactionnelle et la réplication d'instantané prennent en charge la publication de données vers des Abonnés non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur les plateformes prises en charge d’abonné, consultez la page [les abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **Dans cette rubrique**  
  
-   **Pour créer une publication destinée à un Abonné non-SQL Server à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Pour créer une publication destinée à un Abonné non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1.  Installez et configurez le logiciel client et le ou les fournisseurs OLE DB approprié sur le serveur de distribution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d'informations, consultez [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) et [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
2.  Créez une publication avec l'Assistant Nouvelle publication. Pour plus d’informations sur la création de publications, consultez [créer une Publication](../../relational-databases/replication/publish/create-a-publication.md) et [créer une Publication à partir d’une base de données Oracle](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md). Spécifiez les options suivantes dans l'Assistant Nouvelle publication :  
  
    -   Dans la page **Type de publication** , sélectionnez **Publication d'instantané** ou **Publication transactionnelle**.  
  
    -   Dans la page **Agent d'instantané** , désactivez **Créer un instantané immédiatement**.  
  
         Vous devez créer l'instantané après avoir activé la publication pour les Abonnés non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de garantir que l'Agent d'instantané génère un instantané et des scripts d'initialisation qui conviennent pour des Abonnés non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Activer la publication pour les non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés à l’aide de le **Propriétés de la Publication - \< PublicationName>** boîte de dialogue. Consultez [Publication Properties, Subscription Options](../../relational-databases/replication/publication-properties-subscription-options.md) pour plus d'informations sur cette étape.  
  
4.  Créez un abonnement avec l'Assistant Nouvel abonnement. Cette rubrique fournit des informations sur cette étape.  
  
5.  (Facultatif) Modifier la **pre_creation_cmd** article propriété pour conserver les tables sur l’abonné. Cette rubrique fournit des informations sur cette étape.  
  
6.  Générez un instantané de la publication. Cette rubrique fournit des informations sur cette étape.  
  
7.  Synchronisez l'abonnement. Pour plus d'informations, voir [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Pour activer une publication pour des Abonnés non-SQL Server  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Avec le bouton droit de la publication, puis cliquez sur **propriétés**.  
  
4.  Sur le **Options d’abonnement** sélectionnez une valeur de **True** pour l’option **Autoriser des abonnés non SQL Server**. Cette option modifie certaines propriétés afin que la publication soit compatible avec les Abonnés non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  En sélectionnant **True** définit la valeur de la **pre_creation_cmd** à « drop » de l’article. Ce paramètre indique que la réplication doit supprimer une table au niveau de l'Abonné si elle correspond au nom de la table dans l'article. Si vous disposez de tables existantes sur l’abonné que vous souhaitez conserver, utilisez la [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) une procédure stockée pour chaque article ; précisez une valeur 'none' pour **pre_creation_cmd**: `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Vous êtes invité à créer un nouvel instantané de la publication. Si vous ne souhaitez pas le faire immédiatement, vous utiliserez plus tard la procédure décrite plus loin dans la prochaine procédure.  
  
#### Pour créer une publication destinée à un Abonné non-SQL Server  
  
1.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
2.  Avec le bouton droit de la publication appropriée, puis cliquez sur **nouveaux abonnements**.  
  
3.  Dans la page **Emplacement de l'Agent de distribution** , vérifiez que **Exécuter tous les agents sur le serveur de distribution** est bien sélectionné. Les Abonnés non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prennent pas en charge les agents qui s'exécutent au niveau de l'Abonné.  
  
4.  Sur le **abonnés** cliquez sur **Ajouter un abonné** puis **Ajouter un abonné non-SQL Server**.  
  
5.  Dans le **Ajouter un abonné non-SQL Server** boîte de dialogue, sélectionnez le type d’abonné.  
  
6.  Entrez une valeur dans **Nom de la source de données**:  
  
    -   Pour Oracle, cette valeur est le nom du TNS (transparent network substrate) que vous avez configuré.  
  
    -   Pour IBM, ce peut être n'importe quel nom. En règle générale, spécifiez l'adresse réseau de l'Abonné.  
  
     Le nom de la source de données entré à cette étape et les informations de connexion spécifiées à l'étape 9 ne sont pas validés par cet Assistant. Ils ne sont pas utilisés par la réplication avant que l'Agent de distribution ne s'exécute pour l'abonnement. Assurez-vous que toutes les valeurs ont été testés par connexion à l’abonné à l’aide d’un outil client (tel que **sqlplus** pour Oracle). Pour plus d'informations, consultez [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) et [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Sur le **abonnés** page de l’Assistant, l’abonné est maintenant affichée dans le **abonné** colonne en lecture seule **(destination par défaut)** dans les **base de données d’abonnement** colonne :  
  
    -   Sur Oracle, un serveur a au plus une base de données, il n'est donc pas nécessaire de la spécifier.  
  
    -   Pour IBM DB2, la base de données est spécifiée dans la propriété **Catalogue initial** de la chaîne de connexion DB2, qui peut être entrée dans le champ **Options de connexion supplémentaires** décrit plus loin.  
  
8.  Sur le **sécurité de l’Agent de Distribution** cliquez sur le bouton des propriétés (**...**) en regard de l’abonné pour accéder à la **sécurité de l’Agent de Distribution** boîte de dialogue.  
  
9. Dans la boîte de dialogue **Sécurité de l'Agent de distribution** :  
  
    -   Dans les champs **Compte de processus**, **Mot de passe**et **Confirmer le mot de passe** , entrez le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows et le mot de passe sous lequel l'Agent de distribution doit s'exécuter et se connecter en local sur le serveur de distribution.  
  
         Le compte requiert les autorisations minimales suivantes : membre de le **db_owner** fixe du rôle de base de données dans la base de données de distribution ; membre de la liste d’accès (aux publications PAL) ; autorisations de lecture sur le partage d’instantané ; et autorisation de lecture sur le répertoire d’installation du fournisseur OLE DB. Pour plus d’informations sur la publication, consultez [sécuriser le serveur de publication](../../relational-databases/replication/security/secure-the-publisher.md).  
  
    -   Sous **Connexion à l'Abonné**, dans les champs **Connexion**, **Mot de passe**et **Confirmer le mot de passe** , entrez la connexion et le mot de passe à utiliser pour se connecter à l'Abonné. Cette connexion devrait déjà être configurée et devrait avoir des autorisations suffisantes pour créer des objets dans la base de données d'abonnement.  
  
    -   Dans la **options de connexion supplémentaires** Indiquez toutes les options de connexion pour l’abonné sous la forme d’une chaîne de connexion (Oracle ne nécessite pas les options supplémentaires). Chaque option doit être délimitée par un point-virgule. Voici un exemple de chaîne de connexion DB2 (les retours à la ligne facilitent la lisibilité) :  
  
        ```  
        Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
        PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
        Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
        Persist Security Info=False;Connection Pooling=True;  
        ```  
  
         La plupart des options de cette chaîne sont spécifiques du serveur DB2 que vous configurez, mais vous devez attribuer à l'option **Traiter les données binaires comme des caractères** la valeur **False**. Une valeur est exigée de façon que l'option **Catalogue initial** identifie la base de données d'abonnement.  
  
10. Sur le **calendrier de synchronisation** sélectionnez une planification pour l’Agent de Distribution à partir de la **planification de l’Agent** menu (la planification est généralement **s’exécutent en continu**).  
  
11. Dans la page **Initialiser les abonnements** , spécifiez si l'abonnement doit être initialisé et, dans ce cas, quand l'initialiser :  
  
    -   Ne désactivez **Initialiser** que si vous avez créé tous les objets et ajouté toutes les données nécessaires dans la base de données d'abonnement.  
  
    -   Sélectionnez **immédiatement** dans la liste déroulante de la **initialiser lorsque** colonne pour que le transfert de l’Agent de Distribution fichiers d’instantanés à l’abonné une fois cet Assistant est terminé. Sélectionnez **Lors de la première synchronisation** pour que l'Agent transfère les fichiers lors de la prochaine exécution planifiée de l'Agent.  
  
12. Sur la page **Actions de l'Assistant** , scriptez en option l'abonnement. Pour plus d’informations, consultez [Scripting Replication](../../relational-databases/replication/scripting-replication.md).  
  
#### Pour conserver les tables sur l'Abonné  
  
-   Par défaut, l’activation d’une publication de non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés définit la valeur de la **pre_creation_cmd** à « drop » de l’article. Ce paramètre indique que la réplication doit supprimer une table au niveau de l'Abonné si elle correspond au nom de la table dans l'article. Si vous disposez de tables existantes sur l’abonné que vous souhaitez conserver, utilisez la [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) une procédure stockée pour chaque article ; précisez une valeur 'none' pour **pre_creation_cmd**. `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.  
  
#### Pour générer un instantané de la publication  
  
1.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
2.  Avec le bouton droit de la publication, puis cliquez sur **Afficher l’état de l’Agent capture instantanée**.  
  
3.  Dans la **Afficher l’état de l’Agent capture instantanée - \< Publication>** boîte de dialogue, cliquez sur **Démarrer**.  
  
 Lorsque l'Agent d'instantané a terminé, un message s'affiche, par exemple, « [100%] Un instantané de 17 articles a été généré. »  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez créer par programme des abonnements par émission de données pour des Abonnés non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant des procédures stockées de réplication.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
#### Pour créer un abonnement par émission de données pour une publication transactionnelle ou d'instantané pour un Abonné non-SQL Server  
  
1.  Installez le fournisseur OLE DB le plus récent pour l'Abonné non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au niveau du serveur de publication et du serveur de distribution. Pour les besoins de réplication pour un fournisseur OLE DB, consultez [les abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md), [abonnés Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md), [des abonnés IBM DB2](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
2.  Le serveur de publication sur la base de données de publication, vérifiez que la publication prend en charge non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés en exécutant [sp_helppublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md).  
  
    -   Si la valeur de **enabled_for_het_sub** est 1, non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés sont pris en charge.  
  
    -   Si la valeur de **enabled_for_het_sub** est 0, exécutez [sp_changepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), en spécifiant **enabled_for_het_sub** pour **@property** et **true** pour **@value**.  
  
        > [!NOTE]  
        >  Avant de modifier le **enabled_for_het_sub** à **true**, vous devez supprimer tous les abonnements existants à la publication. Vous ne pouvez pas définir **enabled_for_het_sub** à **true** lorsque la publication prend également en charge les abonnements avec mise à jour. Modification de **enabled_for_het_sub** affectera d’autres propriétés de la publication. Pour plus d’informations, consultez la page [les abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addsubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Spécifiez **@publication**, **@subscriber**, une valeur de **(destination par défaut)** pour **@destination_db**, une valeur de **push** pour **@subscription_type**, et la valeur 3 pour **@subscriber_type** (spécifie un fournisseur OLE DB).  
  
4.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addpullsubscription_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Spécifiez les éléments suivants :  
  
    -   Les paramètres **@subscriber**et **@publication** .  
  
    -   Une valeur de **(destination par défaut)** pour **@subscriber_db**,  
  
    -   Les propriétés de non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de source de données pour **@subscriber_provider**, **@subscriber_datasrc**, **@subscriber_location**, **@subscriber_provider_string**, et **@subscriber_catalog**.  
  
    -   Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] informations d’identification Windows sous lequel l’Agent de Distribution sur le serveur de distribution s’exécute pour **@job_login** et **@job_password**.  
  
        > [!NOTE]  
        >  Connexions établies à l’aide de l’authentification Windows intégrée toujours utilisent les informations d’identification Windows spécifiées par **@job_login** et **@job_password**. L'Agent de distribution crée toujours la connexion locale au serveur de distribution à l'aide de l'authentification intégrée Windows. Par défaut, l'agent se connecte à l'Abonné à l'aide de ces informations.  
  
    -   Une valeur de **0** pour **@subscriber_security_mode** et les informations de connexion du fournisseur OLE DB pour **@subscriber_login** et **@subscriber_password**.  
  
    -   Planification du travail de l'Agent de distribution pour cet abonnement. Pour plus d'informations, voir [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Lors de la création d’un abonnement envoyé à un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [activer des connexions chiffrées dans le moteur de base de données & #40 ; SQL Server Configuration Manager & #41 ;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
## Voir aussi  
 [Abonnés IBM DB2](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Abonnés Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md)   
 [Autres abonnés non SQL Server](../../relational-databases/replication/non-sql/other-non-sql-server-subscribers.md)   
 [Concepts liés aux procédures stockées système de réplication](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  