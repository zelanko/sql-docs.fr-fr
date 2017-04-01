---
title: "Afficher et modifier les propri&#233;t&#233;s d&#39;un abonnement par &#233;mission (push) | Microsoft Docs"
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
  - "viewing replication properties"
  - "push subscriptions [SQL Server replication], properties"
  - "subscriptions [SQL Server replication], push"
  - "push subscriptions [SQL Server replication], modifying"
  - "modifying replication properties, push subscriptions"
  - "modification des abonnements, SQL Server Management Studio"
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Afficher et modifier les propri&#233;t&#233;s d&#39;un abonnement par &#233;mission (push)
  Cette rubrique décrit comment afficher et modifier les propriétés de l'abonnement par émission (push) dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Pour afficher et modifier les propriétés d'un abonnement par émission (push) à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Affichez et modifiez les propriétés d'abonnement par envoi de données (push) du serveur de publication dans :  
  
-   Le **Propriétés de l’abonnement - \< serveur de publication>: \< Basedonnéespublication>** boîte de dialogue, qui est disponible à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   L'onglet **Tous les abonnements** , disponible dans le Moniteur de réplication. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Pour afficher et modifier les propriétés d'abonnement par envoi de données (push) dans Management Studio  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Développez la publication appropriée, avec le bouton droit à un abonnement, puis cliquez sur **propriétés**.  
  
4.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
#### Pour afficher et modifier les propriétés d'abonnement par envoi de données (push) dans le Moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
3.  Avec le bouton droit à un abonnement, puis cliquez sur **propriétés**.  
  
4.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Il est possible de modifier des abonnements par émission de données et d'accéder à leurs propriétés, par programme, à l'aide des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'abonnement appartient.  
  
#### Pour afficher les propriétés d'un abonnement par émission de données à une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md). Spécifiez **@publication**, **@subscriber**et la valeur **all** pour **@article**.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), en spécifiant **@subscriber**.  
  
#### Pour modifier les propriétés d'un abonnement par émission de données à une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changesubscriber](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md), en spécifiant **@subscriber** et des paramètres pour les propriétés de l’abonné en cours de modification.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md). Spécifiez **@publication**, **@subscriber**, **@destination_db**, une valeur de **tous les** pour **@article**, la propriété d’abonnement en cours de modification en tant que **@property**, et la nouvelle valeur comme **@value**. Cela modifie les paramètres de sécurité de l'abonnement par émission de données.  
  
3.  (Facultatif) Pour modifier les propriétés du package Data Transformation Services (DTS) d’un abonnement, exécutez [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md) sur l’abonné sur la base de données d’abonnement. Spécifiez l'ID du travail de l'Agent de distribution pour **@jobid** et les propriétés de package DTS suivantes :  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     Cela modifie les propriétés de package DTS d'un abonnement.  
  
    > [!NOTE]  
    >  La tâche ID peut être obtenu en exécutant [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md).  
  
#### Pour afficher les propriétés d'un abonnement par émission de données à une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md). Spécifiez **@publication** et **@subscriber**.  
  
2.  Sur le serveur de publication, exécutez [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), en spécifiant **@subscriber**.  
  
#### Pour modifier les propriétés d'un abonnement par émission de données à une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md). Spécifiez **@publication**, **@subscriber**, **@subscriber_db**, la propriété d’abonnement en cours de modification en tant que **@property**, et la nouvelle valeur comme **@value**.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Les classes RMO à utiliser pour afficher ou modifier les propriétés d'un abonnement par émission de données dépendent du type de publication auquel l'abonnement par émission de données a été souscrit.  
  
#### Pour afficher ou modifier les propriétés d'un abonnement par émission de données à une publication transactionnelle ou d'instantané  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransSubscription> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, et <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> Propriétés.  
  
4.  Définir le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> paramètre de la propriété.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de l’abonnement ont été définies de manière incorrecte à l’étape 3, soit l’abonnement n’existe pas.  
  
6.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l’un de le <xref:Microsoft.SqlServer.Replication.TransSubscription> propriétés qui peuvent être définies, puis appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (méthode).  
  
7.  (Facultatif) Pour afficher les nouveaux paramètres, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> méthode pour recharger les propriétés de l’abonnement.  
  
#### Pour afficher ou modifier les propriétés d'un abonnement par émission de données à une publication de fusion  
  
1.  Créer une connexion à l’abonné à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeSubscription> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, et <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> Propriétés.  
  
4.  Définir le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> paramètre de la propriété.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de l’abonnement ont été définies de manière incorrecte à l’étape 3, soit l’abonnement n’existe pas.  
  
6.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l’un de le <xref:Microsoft.SqlServer.Replication.MergeSubscription> propriétés qui peuvent être définies, puis appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (méthode).  
  
7.  (Facultatif) Pour afficher les nouveaux paramètres, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> méthode pour recharger les propriétés de l’abonnement.  
  
## Voir aussi  
 [Afficher des informations et effectuer des tâches pour un abonnement & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  