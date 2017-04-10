---
title: "Afficher et modifier les propri&#233;t&#233;s d&#39;un abonnement par extraction (pull) | Microsoft Docs"
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
  - "modifying subscriptions"
  - "viewing replication properties"
  - "modifying replication properties, pull subscriptions"
  - "pull subscriptions [SQL Server replication], modifying"
  - "subscriptions [SQL Server replication], pull"
  - "pull subscriptions [SQL Server replication], properties"
  - "modification des abonnements, SQL Server Management Studio"
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Afficher et modifier les propri&#233;t&#233;s d&#39;un abonnement par extraction (pull)
  Cette rubrique décrit comment afficher et modifier les propriétés de l'abonnement par extraction (pull) dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Pour afficher et modifier les propriétés d'un abonnement par extraction à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Afficher les propriétés d’un abonnement par extraction de données à partir de l’éditeur ou l’abonné dans la **Propriétés de l’abonnement - \< serveur de publication>: \< Basedonnéespublication>** boîte de dialogue, qui est disponible à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez modifier des propriétés ou en afficher d'autres sur l'Abonné. Vous pouvez également afficher des propriétés à partir du serveur de publication sous l'onglet **Tous les abonnements** , disponible dans le moniteur de réplication. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Pour afficher des propriétés d'extraction d'abonnement à partir du serveur de publication dans Management Studio  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Développez la publication appropriée, avec le bouton droit à un abonnement, puis cliquez sur **propriétés**.  
  
4.  Affichez les propriétés, puis cliquez sur **OK**.  
  
#### Pour afficher et modifier des propriétés d'extraction d'abonnement à partir de l'Abonné dans Management Studio  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Abonnements locaux** .  
  
3.  Avec le bouton droit à un abonnement, puis cliquez sur **propriétés**.  
  
4.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
#### Pour afficher des propriétés d'extraction d'abonnement à partir du serveur de publication dans le moniteur de réplication  
  
1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
3.  Avec le bouton droit à un abonnement, puis cliquez sur **propriétés**.  
  
4.  Affichez les propriétés, puis cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Il est possible de modifier des abonnements par extraction et d'accéder par programme à leurs propriétés en utilisant des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'abonnement appartient.  
  
#### Pour afficher les propriétés d'un abonnement par extraction à une publication transactionnelle ou d'instantané  
  
1.  Sur l’abonné, exécutez [sp_helppullsubscription](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md). Spécifiez **@publisher**, **@publisher_db**, et **@publication**. Des informations relatives à l'abonnement qui est stocké dans les tables système de l'Abonné sont alors renvoyées.  
  
2.  Sur l’abonné, exécutez [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md). Spécifiez **@publisher**, **@publisher_db**, **@publication**, et une de ces valeurs pour **@publication_type**:  
  
    -   **0** -abonnement appartient à une publication transactionnelle.  
  
    -   **1** -abonnement appartient à une publication d’instantané.  
  
3.  Sur le serveur de publication, exécutez [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md). Spécifiez **@publication** et **@subscriber**.  
  
4.  Sur le serveur de publication, exécutez [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), en spécifiant **@subscriber**. Des informations relatives à l'Abonné sont alors affichées.  
  
#### Pour modifier les propriétés d'un abonnement par extraction à une publication transactionnelle ou d'instantané  
  
1.  Sur l’abonné, exécutez [sp_change_subscription_properties](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), en spécifiant **@publisher**, **@publisher_db**, **@publication**, une valeur **0** (transactionnelle) ou **1** (instantané) pour **@publication_type**, la propriété d’abonnement en cours de modification en tant que **@property**, et la nouvelle valeur comme **@value**.  
  
2.  (Facultatif) Sur la base de données d’abonnement de l’abonné, exécutez [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md). Spécifiez l’ID de la tâche de l’Agent de Distribution pour **@jobid**, et la suivante Services DTS (Data Transformation) les propriétés de package :  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     Cela modifie les propriétés de package DTS d'un abonnement.  
  
    > [!NOTE]  
    >  La tâche ID peut être obtenu en exécutant [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md).  
  
#### Pour afficher les propriétés d'un abonnement par extraction à une publication de fusion  
  
1.  Sur l’abonné, exécutez [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md). Spécifiez **@publisher**, **@publisher_db**, et **@publication**.  
  
2.  Sur l’abonné, exécutez [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md). Spécifiez **@publisher**, **@publisher_db**, **@publication**, et la valeur 2 pour **@publication_type**.  
  
3.  Sur le serveur de publication, exécutez [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md) pour afficher les informations d’abonnement. Pour retourner des informations sur un abonnement spécifique, vous devez spécifier **@publication**, **@subscriber**, et la valeur **extraction** pour **@subscription_type**.  
  
4.  Sur le serveur de publication, exécutez [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), en spécifiant **@subscriber**. Des informations relatives à l'Abonné sont alors affichées.  
  
#### Pour modifier les propriétés d'un abonnement par extraction à une publication de fusion  
  
1.  Sur l’abonné, exécutez [sp_changemergepullsubscription](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md). Spécifiez **@publication**, **@publisher**, **@publisher_db**, la propriété d’abonnement en cours de modification en tant que **@property**, et la nouvelle valeur comme **@value**.  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Les classes RMO à utiliser pour afficher ou modifier les propriétés d'abonnements par extraction dépendent du type de publication auquel l'abonnement par extraction est souscrit.  
  
#### Pour afficher ou modifier les propriétés d'un abonnement par extraction à une publication transactionnelle ou d'instantané  
  
1.  Créer une connexion à l’abonné à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransPullSubscription> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, et <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> Propriétés.  
  
4.  Configuration de la connexion à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de l’abonnement ont été définies de manière incorrecte à l’étape 3, soit l’abonnement n’existe pas sur le serveur.  
  
6.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l’un de le <xref:Microsoft.SqlServer.Replication.TransPullSubscription> propriétés qui peuvent être définies, puis appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (méthode).  
  
7.  (Facultatif) Pour afficher les nouveaux paramètres, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> méthode pour recharger les propriétés de l’article.  
  
8.  Fermez toutes les connexions.  
  
#### Pour afficher ou modifier les propriétés d'un abonnement par extraction à une publication de fusion  
  
1.  Créer une connexion à l’abonné à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePullSubscription> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, et <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> Propriétés.  
  
4.  Configuration de la connexion à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de l’abonnement ont été définies de manière incorrecte à l’étape 3, soit l’abonnement n’existe pas sur le serveur.  
  
6.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l’un de le <xref:Microsoft.SqlServer.Replication.MergePullSubscription> propriétés qui peuvent être définies, puis appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (méthode).  
  
7.  (Facultatif) Pour afficher les nouveaux paramètres, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> méthode pour recharger les propriétés de l’article.  
  
8.  Fermez toutes les connexions.  
  
## Voir aussi  
 [Afficher des informations et effectuer des tâches pour un abonnement & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  