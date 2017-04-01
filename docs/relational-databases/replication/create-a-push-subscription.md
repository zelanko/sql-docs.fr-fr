---
title: "Cr&#233;er un abonnement par &#233;mission (push) | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "push subscriptions [SQL Server replication], creating"
  - "merge replication subscribing [SQL Server replication], push subscriptions"
  - "subscriptions [SQL Server replication], push"
  - "snapshot replication [SQL Server], subscribing"
  - "réplication transactionnelle, abonnement"
ms.assetid: adfbbc61-58d1-4330-9ad6-b14ab1142e2b
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Cr&#233;er un abonnement par &#233;mission (push)
  Cette rubrique décrit comment créer un abonnement envoyé dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], ou Replication Management Objects (RMO). Pour plus d’informations sur la création d’un abonnement envoyé pour un[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonné, consultez la page [créer un abonnement pour un abonné Non SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
 
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Créez un abonnement envoyé sur le serveur de publication ou l'Abonné à l'aide de l'Assistant Nouvel abonnement. Exécutez les étapes de l'Assistant pour :  
  
-   Spécifier le serveur de publication et la publication.  
  
-   Sélectionner l'emplacement d'exécution des Agents de réplication. Pour un abonnement envoyé, sélectionnez **exécuter tous les agents du serveur de distribution (abonnements)** sur le **l’Agent de distribution** page ou **emplacement de l’Agent de fusion** page, selon le type de publication.  
  
-   Spécifiez des Abonnés et des bases de données d'abonnement.  
  
-   Spécifiez les noms de connexion et mots de passe utilisés pour les connexions établies par les Agents de réplication :  
  
    -   Pour les abonnements aux publications d'instantané et transactionnelles, spécifiez les informations d'identification dans la page **Sécurité de l'Agent de distribution** .  
  
    -   Pour les abonnements aux publications de fusion, spécifiez les informations d'identification dans la page **Sécurité de l'Agent de fusion** .  
  
     Pour plus d’informations sur les autorisations requises par chaque agent, consultez [modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Spécifiez une planification de la synchronisation et le moment choisi pour initialiser l'Abonné.  
  
-   Spécifiez les autres options pour les publications de fusion : type d'abonnement et valeurs pour le filtrage paramétré.  
  
-   Spécifiez les autres options pour les publications transactionnelles qui autorisent la mise à jour des abonnements : si les Abonnés doivent valider immédiatement les modifications sur le serveur de publication ou les écrire dans une file d'attente ou encore les informations d'identification utilisées pour la connexion de l'Abonné au serveur de publication.  
  
-   Créez éventuellement un script pour l'abonnement.  
  
#### Pour créer un abonnement envoyé à partir du serveur de publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Avec le bouton droit de la publication pour laquelle vous souhaitez créer un ou plusieurs abonnements, puis cliquez sur **nouveaux abonnements**.  
  
4.  Exécutez les étapes de l'Assistant Nouvel abonnement.  
  
#### Pour créer un abonnement envoyé à partir de l'Abonné  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** .  
  
3.  Cliquez sur le **abonnements locaux** puis cliquez sur **nouveaux abonnements**.  
  
4.  Sur le **Publication** page de l’Assistant Nouvel abonnement, sélectionnez **\< Rechercher un serveur de publication SQL>** ou **\< Rechercher le serveur de publication Oracle>** à partir de la **Publisher** liste déroulante.  
  
5.  Connectez-vous au serveur de publication dans la boîte de dialogue **Se connecter au serveur** .  
  
6.  Sélectionnez une publication dans la page **Publication** .  
  
7.  Exécutez les étapes de l'Assistant Nouvel abonnement.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les abonnements par envoi de données peuvent être créés par programmation en utilisant des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'abonnement appartient.  
  
> **IMPORTANT !** Lorsque cela est possible, invitez les utilisateurs à saisir leurs informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
#### Pour créer un abonnement par envoi de données vers un instantané ou une publication transactionnelle  
  
1.  Le serveur de publication sur la base de données de publication, vérifiez que la publication prend en charge les abonnements envoyés par l’exécution de [sp_helppublication](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md).  
  
    -   Si la valeur de **allow_push** est **1**, abonnements sont pris en charge.  
  
    -   Si la valeur de **allow_push** est **0**, exécutez [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), en spécifiant **allow_push** pour **@property** et **true** pour **@value**.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addsubscription](https://msdn.microsoft.com/library/ms181702.aspx). Spécifiez **@publication**, **@subscriber** et **@destination_db**. Spécifiez la valeur **push** pour **@subscription_type**. Pour plus d’informations sur la mise à jour des abonnements, consultez [créer un abonnement à une Publication transactionnelle actualisable](https://msdn.microsoft.com/library/ms152769.aspx).  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Spécifiez les éléments suivants :  
  
    -   Le **@subscriber**, **@subscriber_db**, et **@publication** paramètres.  
  
    -   Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] informations d’identification Windows sous lequel l’Agent de Distribution sur le serveur de distribution s’exécute pour **@job_login** et **@job_password**.  
  
        > **Remarque :** connexions établies à l’aide de l’authentification Windows intégrée toujours utilisent les informations d’identification Windows spécifiées par **@job_login** et **@job_password**. L'Agent de distribution crée toujours la connexion locale au serveur de distribution à l'aide de l'authentification intégrée Windows. Par défaut, l'agent se connecte à l'Abonné à l'aide de ces informations.  
  
    -   (Facultatif) Une valeur de **0** pour **@subscriber_security_mode** et [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informations de connexion pour **@subscriber_login** et **@subscriber_password**. Spécifiez ces paramètres si vous devez utiliser l'authentification SQL Server lors de la connexion à l'abonné.  
  
    -   Planification du travail de l'Agent de distribution pour cet abonnement. Pour plus d'informations, voir [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > **IMPORTANT** Lors de la création d’un abonnement envoyé à un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Pour créer un abonnement par envoi de données vers une publication de fusion  
  
1.  Le serveur de publication sur la base de données de publication, vérifiez que la publication prend en charge les abonnements envoyés par l’exécution de [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md).  
  
    -   Si la valeur de **allow_push** est **1**, la publication prend en charge les abonnements envoyés.  
  
    -   Si la valeur de **allow_push** n’est pas **1**, exécutez [sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), en spécifiant **allow_push** pour **@property** et **true** pour **@value**.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md), spécifiez les paramètres suivants :  
  
    -   **@publication**. Il s'agit du nom de la publication.  
  
    -   **@subscriber_type**. Pour un abonnement client, spécifiez **local** , et, pour un abonnement serveur, spécifiez **global**.  
  
    -   **@subscription_priority**. Pour un abonnement serveur, spécifiez la priorité de l’abonnement (**0,00** à **99,99**).  
  
         Pour plus d’informations, consultez [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md). Spécifiez les éléments suivants :  
  
    -   Le **@subscriber**, **@subscriber_db**, et **@publication** paramètres.  
  
    -   Les informations d’identification Windows sous lequel l’Agent de fusion sur le serveur de distribution s’exécute pour **@job_login** et **@job_password**.  
  
        > **Remarque :**  connexions établies à l’aide de l’authentification Windows intégrée toujours utilisent les informations d’identification Windows spécifiées par **@job_login** et **@job_password**. L'Agent de fusion crée toujours la connexion locale au serveur de distribution à l'aide de l'authentification intégrée Windows. Par défaut, l'agent se connecte à l'Abonné à l'aide de ces informations.  
  
    -   (Facultatif) Une valeur de **0** pour **@subscriber_security_mode** et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les informations de connexion pour **@subscriber_login** et **@subscriber_password**. Spécifiez ces paramètres si vous devez utiliser l'authentification SQL Server lors de la connexion à l'abonné.  
  
    -   (Facultatif) Une valeur de **0** pour **@publisher_security_mode** et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les informations de connexion pour **@publisher_login** et **@publisher_password**. Spécifiez ces valeurs si vous devez utiliser l'authentification SQL Server lors de la connexion à l'abonné.  
  
    -   Une planification du travail de l'Agent de fusion pour cet abonnement. Pour plus d'informations, voir [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > **IMPORTANT** Lors de la création d’un abonnement envoyé à un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 L'exemple suivant crée un abonnement par envoi de données vers une publication transactionnelle. Les valeurs de connexion et de mot de passe sont fournies lors de l'exécution à l'aide des variables de script **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_1.sql)]  
  
 L'exemple suivant crée un abonnement par envoi de données vers une publication de fusion. Les valeurs de connexion et de mot de passe sont fournies lors de l'exécution à l'aide des variables de script **sqlcmd** .  
  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez créer par programme des abonnements par émission de données (push) à l'aide d'objets RMO (Replication Management Objects). Les classes RMO que vous utilisez pour créer un abonnement par envoi de données dépendent du type de publication sur laquelle l'abonnement a été créé.  
  
> **IMPORTANT !** Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez stocker des informations d'identification, utilisez les [Services de chiffrement](http://go.microsoft.com/fwlink/?LinkId=34733) fournis par [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### Pour créer un abonnement par envoi de données vers un instantané ou une publication transactionnelle  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransPublication> classe à l’aide de la connexion du serveur de publication de l’étape 1. Spécifiez <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, et <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode. Si cette méthode retourne **false**, soit les propriétés spécifiées à l’étape 2 sont incorrectes, soit la publication n’existe pas sur le serveur.  
  
4.  Exécuter une opération AND logique au niveau du bit (**&** en Visual c# et **et** en Visual Basic) entre la <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propriété et <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Si le résultat est <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, définissez <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> au résultat d’un opérateur logique OR au niveau du bit (**|** en Visual c# et **ou** en Visual Basic) entre <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> et <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Ensuite, appelez <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> pour activer les abonnements envoyés.  
  
5.  Si la base de données d’abonnement n’existe pas, créez-le à l’aide de la <xref:Microsoft.SqlServer.Management.Smo.Database> classe. Pour plus d’informations, consultez [Création, modification et suppression de bases de données de](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransSubscription> classe.  
  
7.  Définissez les propriétés suivantes des abonnements :  
  
    -   Le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> au serveur de publication créé à l’étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Nom de la base de données d’abonnement pour <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Nom de l’abonné pour <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   Nom de la base de données de publication pour <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Nom de la publication pour <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Le <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> et <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> ou <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> champs de <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> pour fournir les informations d’identification pour le [!INCLUDE[msCoName](../../includes/msconame-md.md)] compte Windows sous lequel l’Agent de Distribution s’exécute sur le serveur de distribution. Ce compte permet de créer des connexions locales avec le serveur de distribution et des connexions distantes à l'aide de l'authentification Windows.  
  
        > **Remarque :** paramètre <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> n’est pas requise lorsque l’abonnement est créé par un membre de la **sysadmin** rôle de serveur fixe, mais il est néanmoins recommandé. Dans ce cas, l'Agent va emprunter l'identité du compte de l'Agent SQL Server. Pour plus d’informations, consultez [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facultatif) Valeur **true** (la valeur par défaut) pour <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> pour créer un travail de l’agent qui est utilisé pour synchroniser l’abonnement. Si vous spécifiez **false**, l’abonnement peut uniquement être synchronisé par le biais de la programmation.  
  
    -   (Facultatif) Définir le <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> et <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> ou <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> champs de <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> lors de l’utilisation de l’authentification SQL Server pour se connecter à l’abonné.  
  
8.  Appelez le <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> méthode.  
  
    > **IMPORTANT !**Lors de la création d’un abonnement envoyé à un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour toutes les propriétés, y compris <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et serveur de distribution distant avant d’appeler le <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> méthode. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
#### Pour créer un abonnement par envoi de données vers une publication de fusion  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe à l’aide de la connexion du serveur de publication de l’étape 1. Spécifiez <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, et <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode. Si cette méthode retourne **false**, soit les propriétés spécifiées à l’étape 2 sont incorrectes, soit la publication n’existe pas sur le serveur.  
  
4.  Exécuter une opération AND logique au niveau du bit (**&** en Visual c# et **et** en Visual Basic) entre la <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propriété et <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Si le résultat est <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, définissez <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> au résultat d’un opérateur logique OR au niveau du bit (**|** en Visual c# et **ou** en Visual Basic) entre <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> et <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>. Ensuite, appelez <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> pour activer les abonnements envoyés.  
  
5.  Si la base de données d’abonnement n’existe pas, créez-le à l’aide de la <xref:Microsoft.SqlServer.Management.Smo.Database> classe. Pour plus d’informations, consultez [Création, modification et suppression de bases de données de](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md).  
  
6.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeSubscription> classe.  
  
7.  Définissez les propriétés suivantes des abonnements :  
  
    -   Le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> au serveur de publication créé à l’étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
    -   Nom de la base de données d’abonnement pour <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Nom de l’abonné pour <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   Nom de la base de données de publication pour <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Nom de la publication pour <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Le <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> et <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> ou <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> champs de <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> pour fournir les informations d’identification pour le [!INCLUDE[msCoName](../../includes/msconame-md.md)] compte Windows sous lequel l’Agent de fusion s’exécute sur le serveur de distribution. Ce compte permet de créer des connexions locales avec le serveur de distribution et des connexions distantes à l'aide de l'authentification Windows.  
  
        > **Remarque :** paramètre <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> n’est pas requise lorsque l’abonnement est créé par un membre de la **sysadmin** rôle de serveur fixe, mais il est néanmoins recommandé. Dans ce cas, l'Agent va emprunter l'identité du compte de l'Agent SQL Server. Pour plus d’informations, consultez [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
    -   (Facultatif) Valeur **true** (la valeur par défaut) pour <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> pour créer un travail de l’agent qui est utilisé pour synchroniser l’abonnement. Si vous spécifiez **false**, l’abonnement peut uniquement être synchronisé par le biais de la programmation.  
  
    -   (Facultatif) Définir le <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> et <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> ou <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> champs de <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> lors de l’utilisation de l’authentification SQL Server pour se connecter à l’abonné.  
  
    -   (Facultatif) Définir le <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> et <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> ou <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> champs de <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> lors de l’utilisation de l’authentification SQL Server pour se connecter au serveur de publication.  
  
8.  Appelez le <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> méthode.  
  
    > **IMPORTANT !**  Lors de la création d’un abonnement envoyé à un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour toutes les propriétés, y compris <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, sont envoyées au serveur de distribution en tant que texte brut. Vous devez chiffrer la connexion entre le serveur de publication et serveur de distribution distant avant d’appeler le <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> méthode. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple crée un nouvel abonnement par envoi de données vers une publication transactionnelle. Les informations d'identification du compte Windows que vous utilisez pour exécuter le travail de l'Agent de distribution sont transmises lors de l'exécution.  
  
 [!code-csharp[HowTo#rmo_CreateTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpushsub)]  
  
 Cet exemple crée un nouvel abonnement par envoi de données vers une publication de fusion. Les informations d'identification du compte Windows que vous utilisez pour exécuter le travail de l'Agent de fusion sont transmises lors de l'exécution.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## Voir aussi  
 [Afficher et modifier les propriétés d'un abonnement par émission (push)](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Concepts liés à Replication Management Objects](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Synchroniser un abonnement par émission (push)](../../relational-databases/replication/synchronize-a-push-subscription.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [Utiliser sqlcmd avec des variables de script](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  