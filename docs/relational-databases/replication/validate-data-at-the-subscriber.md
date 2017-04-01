---
title: "Valider des donn&#233;es sur l&#39;Abonn&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Subscribers [SQL Server replication], data validation"
  - "replication [SQL Server], validating data"
  - "transactional replication, validating data"
  - "validating data"
  - "validation des données de réplication de fusion [réplication SQL Server], SQL Server Management Studio"
ms.assetid: 215b4c9a-0ce9-4c00-ac0b-43b54151dfa3
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Valider des donn&#233;es sur l&#39;Abonn&#233;
  Cette rubrique décrit comment valider les données sur l'abonné dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou des objets RMO (Replication Management Objects).  
  
 La validation des données est en processus comptant trois parties :  
  
1.  Un abonnement unique ou tous les abonnements à une publication sont *marqués* pour la validation. Marquez des abonnements pour validation dans les boîtes de dialogue **Valider l'abonnement**, **Valider les abonnements**et **Valider tous les abonnements** , disponibles dans les dossiers **Publications locales** et **Abonnements locaux** de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez aussi marquer des abonnements à partir de l'onglet **Tous les abonnements** , de l'onglet **Liste de suivi des abonnements** et du nœud des publications dans le Moniteur de réplication. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
2.  Un abonnement est validé lors de sa prochaine synchronisation par l'Agent de distribution (réplication transactionnelle) ou l'Agent de fusion (réplication de fusion). L'Agent de distribution s'exécute généralement en continu, auquel cas la validation se produit immédiatement ; l'Agent de fusion s'exécute généralement à la demande, auquel cas la validation se produit après l'exécution de l'agent.  
  
3.  Affichez les résultats de la validation :  
  
    -   dans la fenêtre détaillée du moniteur de réplication : sous l'onglet **Historique du serveur de distribution vers l'Abonné** pour la réplication transactionnelle et l'onglet **Historique de synchronisation** pour la réplication de fusion ;  
  
    -   dans la boîte de dialogue **Afficher l'état de synchronisation** de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour valider les données sur l'abonné, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les procédures du moniteur de réplication concernent uniquement les abonnements par envoi de données (push) car ce type d'abonnement ne peut pas être synchronisé dans le moniteur de réplication. Vous pouvez toutefois marquer un abonnement pour validation et afficher les résultats de la validation pour les abonnements par extraction de données (pull) dans le moniteur de réplication.  
  
-   Les résultats de la validation indiquent si la validation a échoué ou a raté, mais ne précisent pas les lignes défectueuses en cas d'échec. Pour comparer des données sur le serveur de publication et sur l'Abonné, utilisez l' [tablediff Utility](../../tools/tablediff-utility.md). Pour plus d’informations sur l’utilisation de cet utilitaire avec des données répliquées, consultez [comparer les Tables répliquées pour différences & #40 ; Programmation de la réplication & #41 ;](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour valider les données des abonnements à une publication transactionnelle (Management Studio)  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Avec le bouton droit de la publication pour laquelle vous souhaitez valider les abonnements, puis cliquez sur **valider les abonnements**.  
  
4.  Dans la boîte de dialogue **Valider les abonnements** , sélectionnez les abonnements à valider :  
  
    -   Sélectionnez **Valider tous les abonnements SQL Server**.  
  
    -   Sélectionnez **Valider les abonnements suivants**, puis sélectionnez un ou plusieurs abonnements.  
  
5.  Pour spécifier le type de validation à effectuer (nombre de lignes, ou nombre de lignes et somme de contrôle), cliquez sur **les Options de Validation**, puis spécifiez les options dans la **Options de Validation d’abonnement** boîte de dialogue.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  Affichez les résultats de la validation dans le moniteur de réplication ou dans la boîte de dialogue **Afficher l'état de synchronisation** . Pour chaque abonnement :  
  
    1.  Développez la publication, cliquez sur l’abonnement, puis cliquez sur **Afficher l’état de synchronisation**.  
  
    2.  Si l'agent n'est pas en cours d'exécution, cliquez sur **Démarrer** dans la boîte de dialogue **Afficher l'état de synchronisation** . La boîte de dialogue affiche des messages d'information concernant la validation.  
  
     Si aucun message concernant la validation ne s'affiche, l'agent a déjà consigné un message à ce sujet dans le journal. Dans ce cas, affichez les résultats de la validation dans le moniteur de réplication. Pour plus d'informations, consultez les procédures du moniteur de réplication dans cette rubrique.  
  
#### Pour valider les données d'un abonnement unique à une publication transactionnelle (Management Studio)  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Développez la publication pour laquelle vous souhaitez valider les abonnements, cliquez sur l’abonnement, puis cliquez sur **valider l’abonnement**.  
  
4.  Dans la boîte de dialogue **Valider l'abonnement** , sélectionnez **Valider cet abonnement**.  
  
5.  Pour spécifier le type de validation à effectuer (nombre de lignes, ou nombre de lignes et somme de contrôle), cliquez sur **Options**, puis spécifiez les options dans la **Options de Validation d’abonnement** boîte de dialogue.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  Affichez les résultats de la validation dans le moniteur de réplication ou dans la boîte de dialogue **Afficher l'état de synchronisation** :  
  
    1.  Développez la publication, cliquez sur l’abonnement, puis cliquez sur **Afficher l’état de synchronisation**.  
  
    2.  Si l'agent n'est pas en cours d'exécution, cliquez sur **Démarrer** dans la boîte de dialogue **Afficher l'état de synchronisation** . La boîte de dialogue affiche des messages d'information concernant la validation.  
  
     Si aucun message concernant la validation ne s'affiche, l'agent a déjà consigné un message à ce sujet dans le journal. Dans ce cas, affichez les résultats de la validation dans le moniteur de réplication. Pour plus d'informations, consultez les procédures du moniteur de réplication dans cette rubrique.  
  
#### Pour valider les données de tous les abonnements à une publication transactionnelle (Management Studio)  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Avec le bouton droit de la publication pour laquelle vous souhaitez valider les abonnements, puis cliquez sur **Valider tous les abonnements**.  
  
4.  Dans la **Valider tous les abonnements** boîte de dialogue, spécifiez le type de validation à effectuer (nombre de lignes, ou nombre de lignes et somme de contrôle).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Affichez les résultats de la validation dans le moniteur de réplication ou dans la boîte de dialogue **Afficher l'état de synchronisation** . Pour chaque abonnement :  
  
    1.  Développez la publication, cliquez sur l’abonnement, puis cliquez sur **Afficher l’état de synchronisation**.  
  
    2.  Si l'agent n'est pas en cours d'exécution, cliquez sur **Démarrer** dans la boîte de dialogue **Afficher l'état de synchronisation** . La boîte de dialogue affiche des messages d'information concernant la validation.  
  
     Si aucun message concernant la validation ne s'affiche, l'agent a déjà consigné un message à ce sujet dans le journal. Dans ce cas, affichez les résultats de la validation dans le moniteur de réplication. Pour plus d'informations, consultez les procédures du moniteur de réplication dans cette rubrique.  
  
#### Pour valider les données de tous les abonnements par envoi de données à une publication transactionnelle (moniteur de réplication)  
  
1.  Dans le moniteur de réplication, développez un groupe de serveurs de publication dans le volet gauche, puis développez un serveur de publication.  
  
2.  Avec le bouton droit de la publication pour laquelle vous souhaitez valider les abonnements, puis cliquez sur **valider les abonnements**.  
  
3.  Dans la boîte de dialogue **Valider les abonnements** , sélectionnez les abonnements à valider :  
  
    -   Sélectionnez **Valider tous les abonnements SQL Server**.  
  
    -   Sélectionnez **Valider les abonnements suivants**, puis sélectionnez un ou plusieurs abonnements.  
  
4.  Pour spécifier le type de validation à effectuer (nombre de lignes, ou nombre de lignes et somme de contrôle), cliquez sur **les Options de Validation**, puis spécifiez les options dans la **Options de Validation d’abonnement** boîte de dialogue.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Cliquez sur l'onglet **Tous les abonnements** .  
  
7.  Affichez les résultats de la validation. Pour chaque abonnement par envoi de données :  
  
    1.  Si l’agent ne fonctionne pas, cliquez sur l’abonnement, puis cliquez sur **Démarrer la synchronisation**.  
  
    2.  Cliquez sur l’abonnement, puis cliquez sur **Afficher les détails**.  
  
    3.  Affichez les informations dans l'onglet **Historique du serveur de distribution vers l'Abonné** de la zone de texte **Actions dans la session sélectionnée** .  
  
#### Pour valider les données d'un abonnement unique par envoi de données à une publication de fusion (moniteur de réplication)  
  
1.  Dans le moniteur de réplication, développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
3.  Cliquez sur l’abonnement que vous voulez valider, puis cliquez sur **valider l’abonnement**.  
  
4.  Dans la boîte de dialogue **Valider l'abonnement** , sélectionnez **Valider cet abonnement**.  
  
5.  Pour spécifier le type de validation à effectuer (nombre de lignes, ou nombre de lignes et somme de contrôle), cliquez sur **Options**, puis spécifiez les options dans la **Options de Validation d’abonnement** boîte de dialogue.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  Cliquez sur l'onglet **Tous les abonnements** .  
  
8.  Affichez les résultats de la validation :  
  
    1.  Si l’agent ne fonctionne pas, cliquez sur l’abonnement, puis cliquez sur **Démarrer la synchronisation**.  
  
    2.  Cliquez sur l’abonnement, puis cliquez sur **Afficher les détails**.  
  
    3.  Affichez les informations dans l'onglet **Historique de synchronisation** de la zone de texte **Dernier message de la session sélectionnée** .  
  
#### Pour valider les données de tous les abonnements par envoi de données à une publication de fusion (moniteur de réplication)  
  
1.  Dans le moniteur de réplication, développez un groupe de serveurs de publication dans le volet gauche, puis développez un serveur de publication.  
  
2.  Avec le bouton droit de la publication pour laquelle vous souhaitez valider les abonnements, puis cliquez sur **Valider tous les abonnements**.  
  
3.  Dans la **Valider tous les abonnements** boîte de dialogue, spécifiez le type de validation à effectuer (nombre de lignes, ou nombre de lignes et somme de contrôle).  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Cliquez sur l'onglet **Tous les abonnements** .  
  
6.  Affichez les résultats de la validation. Pour chaque abonnement par envoi de données :  
  
    1.  Si l’agent ne fonctionne pas, cliquez sur l’abonnement, puis cliquez sur **Démarrer la synchronisation**.  
  
    2.  Cliquez sur l’abonnement, puis cliquez sur **Afficher les détails**.  
  
    3.  Affichez les informations dans l'onglet **Historique de synchronisation** de la zone de texte **Dernier message de la session sélectionnée** .  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour valider les données de tous les articles d'une publication transactionnelle  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_publication_validation & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md). Spécifiez **@publication** et une de ces valeurs pour **@rowcount_only**:  
  
    -   **1** -contrôle du nombre de lignes uniquement (par défaut)  
  
    -   **2** -total de contrôle du nombre de lignes et binaires.  
  
    > [!NOTE]  
    >  Lorsque vous exécutez [sp_publication_validation & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md), [sp_article_validation & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) est exécuté pour chaque article de la publication. Pour exécuter correctement [sp_publication_validation & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md), vous devez disposer des autorisations SELECT sur toutes les colonnes dans les tables de base publiées.  
  
2.  (Facultatif) Démarrez l'Agent de distribution pour chaque abonnement s'il n'est pas déjà en cours d'exécution. Pour plus d'informations, consultez [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) et [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
3.  Vérifiez la sortie de l'agent pour le résultat de la validation. Pour plus d’informations, consultez [valider les données répliquées](../../relational-databases/replication/validate-replicated-data.md).  
  
#### Pour valider les données d'un seul article d'une publication transactionnelle  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_article_validation & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md). Spécifiez **@publication**, le nom de l’article pour **@article**, et une de ces valeurs pour **@rowcount_only**:  
  
    -   **1** -contrôle du nombre de lignes uniquement (par défaut)  
  
    -   **2** -nombre de lignes et somme de contrôle binaire.  
  
    > [!NOTE]  
    >  Pour exécuter correctement [sp_article_validation & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), vous devez disposer des autorisations SELECT sur toutes les colonnes de la table de base publiée.  
  
2.  (Facultatif) Démarrez l'Agent de distribution pour chaque abonnement s'il n'est pas déjà en cours d'exécution. Pour plus d'informations, consultez [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) et [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
3.  Vérifiez la sortie de l'agent pour le résultat de la validation. Pour plus d’informations, consultez [valider les données répliquées](../../relational-databases/replication/validate-replicated-data.md).  
  
#### Pour valider les données d'un seul abonné d'une publication transactionnelle  
  
1.  Sur la base de données de publication de l’éditeur, ouvrez une transaction explicite à l’aide [BEGIN TRANSACTION & #40 ; Transact-SQL & #41 ;](../../t-sql/language-elements/begin-transaction-transact-sql.md).  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_marksubscriptionvalidation & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md). Spécifier la publication pour **@publication**, le nom de l’abonné pour **@subscriber**, et le nom de la base de données d’abonnement pour **@destination_db**.  
  
3.  (Facultatif) Répétez l'étape 2 pour chaque abonnement en cours de validation.  
  
4.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_article_validation & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md). Spécifiez **@publication**, le nom de l’article pour **@article**, et une de ces valeurs pour **@rowcount_only**:  
  
    -   **1** -contrôle du nombre de lignes uniquement (par défaut)  
  
    -   **2** -nombre de lignes et somme de contrôle binaire.  
  
    > [!NOTE]  
    >  Pour exécuter correctement [sp_article_validation & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), vous devez disposer des autorisations SELECT sur toutes les colonnes de la table de base publiée.  
  
5.  Sur la base de données de publication de l’éditeur, validez la transaction à l’aide [COMMIT TRANSACTION & #40 ; Transact-SQL & #41 ;](../../t-sql/language-elements/commit-transaction-transact-sql.md).  
  
6.  (Facultatif) Répétez les étapes 1 à 5 pour chaque article en cours de validation.  
  
7.  (Facultatif) Démarrez l'Agent de distribution s'il n'est pas déjà en cours d'exécution. Pour plus d'informations, consultez [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) et [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
8.  Vérifiez la sortie de l'agent pour le résultat de la validation. Pour plus d'informations, voir [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
#### Pour valider les données de tous les abonnements à une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_validatemergepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-validatemergepublication-transact-sql.md). Spécifiez **@publication** et l'une des valeurs suivantes pour **@level**:  
  
    -   **1** -validation du nombre de lignes uniquement.  
  
    -   **3** -validation de somme de contrôle binaire du nombre de lignes.  
  
     Tous les abonnements sont ainsi marqués pour la validation.  
  
2.  Démarrez l'agent de fusion pour chaque abonnement. Pour plus d'informations, consultez [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) et [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
3.  Vérifiez la sortie de l'agent pour le résultat de la validation. Pour plus d'informations, voir [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
#### Pour valider les données des abonnements sélectionnés à une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_validatemergesubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-validatemergesubscription-transact-sql.md). Spécifiez **@publication**, le nom de l’abonné pour **@subscriber**, le nom de la base de données d’abonnement pour **@subscriber_db**, et une de ces valeurs pour **@level**:  
  
    -   **1** -validation du nombre de lignes uniquement.  
  
    -   **3** -validation de somme de contrôle binaire du nombre de lignes.  
  
     Les abonnements sélectionnés sont ainsi marqués pour la validation.  
  
2.  Démarrez l'agent de fusion pour chaque abonnement. Pour plus d'informations, consultez [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) et [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
3.  Vérifiez la sortie de l'agent pour le résultat de la validation.  
  
4.  Répétez les étapes 1 à 3 pour chaque abonnement en cours de validation.  
  
> [!NOTE]  
>  Un abonnement à une publication de fusion peut également être validé à la fin d’une synchronisation en spécifiant le **-Valider** paramètre lors de l’exécution du [l’Agent de réplication de fusion](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
#### Pour valider les données d'un abonnement à l'aide de paramètres de l'Agent de fusion  
  
1.  Démarrez l'Agent de fusion sur l'Abonné (abonnement par extraction) ou sur le serveur de distribution (abonnement par émission de données) à partir de l'invite de commandes de l'une des façons suivantes.  
  
    -   La valeur **1** (rowcount) ou **3** (somme de contrôle du nombre de lignes et binaire) pour la **-Valider** paramètre.  
  
    -   Spécification de **la validation du nombre de lignes** ou **validation du nombre de lignes et somme de contrôle** pour la **- ProfileName** paramètre.  
  
     Pour plus d'informations, consultez [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) ou [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 La réplication permet d'utiliser les objets RMO (Replication Management Objects) pour vérifier par programmation que les données de l'Abonné correspondent à celles du serveur de publication. Les objets que vous utilisez dépendent du type de topologie de réplication. La réplication transactionnelle requiert la validation de tous les abonnements à une publication.  
  
> [!NOTE]  
>  Pour obtenir un exemple, consultez [exemple (RMO)](#RMOExample), plus loin dans cette section.  
  
#### Pour valider les données de tous les articles d'une publication transactionnelle  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransPublication> classe. Définir le <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication. Définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode permettant d’obtenir les propriétés restantes de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.TransPublication.ValidatePublication%2A> (méthode). Passez les éléments suivants :  
  
    -   <xref:Microsoft.SqlServer.Replication.ValidationOption>  
  
    -   <xref:Microsoft.SqlServer.Replication.ValidationMethod>  
  
    -   Une valeur booléenne qui indique s'il faut arrêter l'Agent de distribution une fois la validation terminée.  
  
     Cela marque les articles pour la validation.  
  
5.  S'il n'est pas déjà en cours d'exécution, démarrez l'Agent de distribution pour synchroniser chaque abonnement. Pour plus d'informations, consultez [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md) ou [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md). Le résultat de l'opération de validation est écrit dans l'historique de l'agent. Pour plus d'informations, voir [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
#### Pour valider les données de tous les abonnements à une publication de fusion  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe. Définir le <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication. Définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode permettant d’obtenir les propriétés restantes de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.MergePublication.ValidatePublication%2A> (méthode). Passer à l’élément <xref:Microsoft.SqlServer.Replication.ValidationOption>.  
  
5.  Exécutez l'Agent de fusion pour chaque abonnement pour démarrer la validation ou attendez que l'agent planifié suivant ne s'exécute. Pour plus d'informations, consultez [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) et [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md). Le résultat de l'opération de validation est écrit dans l'historique de l'agent, que vous affichez en utilisant le moniteur de réplication. Pour plus d'informations, voir [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
#### Pour valider les données d'un seul abonnement à une publication de fusion  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe. Définir le <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication. Définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode permettant d’obtenir les propriétés restantes de l’objet. Si cette méthode retourne **false**, soit les propriétés de la publication ont été définies de manière incorrecte à l'étape 2, soit la publication n'existe pas.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.MergePublication.ValidateSubscription%2A> (méthode). Passez le nom de la base de données d’abonnés et d’abonnements en cours de validation et les <xref:Microsoft.SqlServer.Replication.ValidationOption>.  
  
5.  Exécutez l'Agent de fusion de l'abonnement pour démarrer la validation ou attendez que l'agent planifié suivant ne s'exécute. Pour plus d'informations, consultez [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) et [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md). Le résultat de l'opération de validation est écrit dans l'historique de l'agent, que vous affichez en utilisant le moniteur de réplication. Pour plus d'informations, voir [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
###  <a name="RMOExample"></a> Exemple (RMO)  
 Cet exemple marque tous les abonnements à une publication transactionnelle pour une validation du nombre de lignes.  
  
 [!code-csharp[HowTo#rmo_ValidateTranPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_validatetranpub)]  
  
 [!code-vb[HowTo#rmo_vb_ValidateTranPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_validatetranpub)]  
  
 Cet exemple marque un abonnement spécifique à une publication de fusion pour une validation du nombre de lignes.  
  
 [!code-csharp[HowTo#rmo_ValidateMergeSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_validatemergesub)]  
  
 [!code-vb[HowTo#rmo_vb_ValidateMergeSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_validatemergesub)]  
  
  