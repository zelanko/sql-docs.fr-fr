---
title: "Supprimer un abonnement par &#233;mission (push) | Microsoft Docs"
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
  - "suppression des abonnements"
  - "abonnements par envoi de données (push) [réplication SQL Server], suppression"
  - "suppression d'abonnements"
  - "abonnements [réplication SQL Server], par envoi de données (push)"
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Supprimer un abonnement par &#233;mission (push)
  Cette rubrique explique comment supprimer un abonnement par émission de données (push) dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Pour supprimer un abonnement par émission de données (push) à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Supprimer un abonnement envoyé sur le serveur de publication (à partir de la **Publications locales** dossier [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) ou sur l’abonné (à partir de la **abonnements locaux** dossier). La suppression d'un abonnement ne supprime pas les objets ou les données de ce dernier : ils doivent être supprimés manuellement.  
  
#### Pour supprimer un abonnement par envoi de données au niveau du serveur de publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Développez la publication associée à l'abonnement à supprimer.  
  
4.  Cliquez sur l’abonnement, puis cliquez sur **Supprimer**.  
  
5.  Dans la boîte de dialogue de confirmation, indiquez si vous souhaitez vous connecter à l'Abonné pour supprimer les informations d'abonnement. Si vous désactivez la case à cocher **Se connecter à l'Abonné** , vous devrez vous connecter plus tard à l'Abonné pour supprimer les informations.  
  
#### Pour supprimer un abonnement par envoi de données au niveau de l'Abonné  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Abonnements locaux** .  
  
3.  Cliquez sur l’abonnement que vous souhaitez supprimer, puis cliquez sur **Supprimer**.  
  
4.  Dans la boîte de dialogue de confirmation, indiquez si vous souhaitez vous connecter au serveur de publication pour supprimer les informations d'abonnement. Si vous désactivez la case à cocher **Se connecter au serveur de publication** , vous devez vous connecter ultérieurement au serveur de publication pour supprimer les informations.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les abonnements par émission de données peuvent être supprimés par programme en utilisant des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'abonnement appartient.  
  
#### Pour supprimer un abonnement par émission de données à une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_dropsubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). Spécifiez **@publication** et **@subscriber**. Affectez la valeur **all** à **@article**. (Facultatif) Si le serveur de distribution n’est pas accessible, spécifiez la valeur **1** pour **@ignore_distributor** pour supprimer l’abonnement sans supprimer les objets connexes dans le distributeur.  
  
2.  Sur la base de données d’abonnement de l’abonné, exécutez [sp_subscription_cleanup & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) Pour supprimer les métadonnées de réplication dans la base de données d’abonnement.  
  
#### Pour supprimer un abonnement par émission de données à une publication de fusion  
  
1.  Sur le serveur de publication, exécutez [sp_dropmergesubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md), en spécifiant **@publication**, **@subscriber** et **@subscriber_db**. (Facultatif) Si le serveur de distribution n’est pas accessible, spécifiez la valeur **1** pour **@ignore_distributor** pour supprimer l’abonnement sans supprimer les objets connexes dans le distributeur.  
  
2.  Sur la base de données d’abonnement de l’abonné, exécutez [sp_mergesubscription_cleanup & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md). Spécifiez **@publisher**, **@publisher_db**, et **@publication**. Les métadonnées de fusion sont alors supprimées de la base de données d'abonnement.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple supprime un abonnement par émission de données à une publication transactionnelle.  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_1.sql)]  
  
 Cet exemple supprime un abonnement par émission de données à une publication de fusion.  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Les classes RMO à utiliser pour supprimer un abonnement par émission de données dépendent du type de publication auquel l'abonnement par émission de données est souscrit.  
  
#### Pour supprimer un abonnement par émission de données à une publication transactionnelle ou d'instantané  
  
1.  Créer une connexion à l’abonné à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransSubscription> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, et <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> Propriétés.  
  
4.  Définir le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
5.  Vérifier la <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propriété pour vérifier l’existence de l’abonnement. Si la valeur de cette propriété est **false**, les propriétés de l'abonnement ont été définies de manière incorrecte à l'étape 2, ou l'article n'existe pas.  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> méthode.  
  
#### Pour supprimer un abonnement par émission de données à une publication de fusion  
  
1.  Créer une connexion à l’abonné à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeSubscription> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, et <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> Propriétés.  
  
4.  Définir le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
5.  Vérifier la <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propriété pour vérifier l’existence de l’abonnement. Si la valeur de cette propriété est **false**, les propriétés de l'abonnement ont été définies de manière incorrecte à l'étape 2, ou l'article n'existe pas.  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> méthode.  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Vous pouvez supprimer par programme des abonnements par émission de données à l'aide d'objets RMO (Replication Management Objects).  
  
 [!code-csharp[HowTo#rmo_DropTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpushsub)]  
  
## Voir aussi  
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  