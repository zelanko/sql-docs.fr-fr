---
title: Supprimer un abonnement par extraction | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- deleting subscriptions
- pull subscriptions [SQL Server replication], deleting
- subscriptions [SQL Server replication], pull
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ac5d4f7d199e3ee3de6ffb43e2c43e232681b0d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721459"
---
# <a name="delete-a-pull-subscription"></a>Supprimer un abonnement par extraction
  Cette rubrique explique comment supprimer un abonnement par extraction de données (pull) dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Pour supprimer un abonnement par extraction de données (pull) à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Supprimez un abonnement par extraction de données (pull) sur le serveur de publication (à partir du dossier **Publications locales** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) ou sur l'Abonné (à partir du dossier **Abonnements locaux** ). La suppression d'un abonnement ne supprime pas les objets ou les données de ce dernier : ils doivent être supprimés manuellement.  
  
#### <a name="to-delete-a-pull-subscription-at-the-publisher"></a>Pour supprimer un abonnement extrait sur le serveur de publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Développez la publication associée à l'abonnement à supprimer.  
  
4.  Cliquez avec le bouton droit sur l'abonnement puis cliquez sur **Supprimer**.  
  
5.  Dans la boîte de dialogue de confirmation, indiquez si vous souhaitez vous connecter à l'Abonné pour supprimer les informations d'abonnement. Si vous désactivez la case à cocher **Se connecter à l'Abonné** , vous devez vous connecter ultérieurement à l'Abonné pour supprimer les informations.  
  
#### <a name="to-delete-a-pull-subscription-at-the-subscriber"></a>Pour supprimer un abonnement extrait sur l'Abonné  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Abonnements locaux** .  
  
3.  Cliquez avec le bouton droit sur l'abonnement à supprimer, puis cliquez sur **Supprimer**.  
  
4.  Dans la boîte de dialogue de confirmation, indiquez si vous souhaitez vous connecter au serveur de publication pour supprimer les informations d'abonnement. Si vous désactivez la case à cocher **Se connecter au serveur de publication** , vous devez vous connecter ultérieurement au serveur de publication pour supprimer les informations.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les abonnements par extraction peuvent être supprimés par programme en utilisant des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'abonnement appartient.  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Pour supprimer un abonnement par extraction à une publication transactionnelle ou d'instantané  
  
1.  Dans la base de données d’abonnement de l’Abonné, exécutez [sp_droppullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql). Specify **@publication** , de **@publisher** et **@publisher_db** .  
  
2.  Dans la base de données de publication du serveur de publication, exécutez [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql). Spécifiez **@publication** et **@subscriber** . Affectez la valeur **all** à **@article** . (Facultatif) Si le serveur de distribution n'est pas accessible, affectez la valeur **1** à **@ignore_distributor** pour supprimer l'abonnement sans supprimer les objets connexes au niveau du serveur de distribution.  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a>Pour supprimer un abonnement par extraction à une publication de fusion  
  
1.  Dans la base de données d’abonnement de l’Abonné, exécutez [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql). Spécifiez **@publication** , de **@publisher** et **@publisher_db** .  
  
2.  Dans la base de données de publication du serveur de publication, exécutez [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql). Specify **@publication** , de **@subscriber** et **@subscriber_db** . Affectez la valeur **pull** à **@subscription_type** . (Facultatif) Si le serveur de distribution n'est pas accessible, affectez la valeur **1** à **@ignore_distributor** pour supprimer l'abonnement sans supprimer les objets connexes au niveau du serveur de distribution.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 L'exemple suivant supprime un abonnement par extraction à une publication transactionnelle. Le premier lot est exécuté sur l'Abonné, le second sur le serveur de publication.  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptranpullsubscription)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 L'exemple suivant supprime un abonnement par extraction à une publication de fusion. Le premier lot est exécuté sur l'Abonné, le second sur le serveur de publication.  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergepullsubscription)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez supprimer par programme des abonnements par extraction à l'aide d'objets RMO (Replication Management Objects). Les classes RMO utilisées pour supprimer un abonnement par extraction dépendent du type de publication auquel l'abonnement par extraction est souscrit.  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Pour supprimer un abonnement par extraction à une publication transactionnelle ou d'instantané  
  
1.  Créez une connexion à l'Abonné et au serveur de publication à l'aide de la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.TransPullSubscription> et définissez les propriétés <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>et <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> . Utilisez la connexion à l'Abonné créée à l'étape 1 pour définir la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
3.  Vérifiez la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> pour vous assurer que l'abonnement existe. Si la valeur de cette propriété est `false`, les propriétés de l'abonnement ont été définies de manière incorrecte à l'étape 2, ou l'article n'existe pas.  
  
4.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> .  
  
5.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.TransPublication> en utilisant la connexion au serveur de publication de l'étape 1. Spécifiez <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> et <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Si cette méthode retourne `false`, les propriétés spécifiées à l'étape 5 sont incorrectes ou la publication n'existe pas sur le serveur.  
  
7.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> . Spécifiez le nom de l'Abonné et la base de données d'abonnement pour les paramètres *subscriber* et *subscriberDB* .  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a>Pour supprimer un abonnement par extraction à une publication de fusion  
  
1.  Créez une connexion à l'Abonné et au serveur de publication à l'aide de la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.MergePullSubscription> et définissez les propriétés <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>et <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> . Utilisez la connexion créée l'étape 1 pour définir la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
3.  Vérifiez la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> pour vous assurer que l'abonnement existe. Si la valeur de cette propriété est `false`, les propriétés de l'abonnement ont été définies de manière incorrecte à l'étape 2, ou l'article n'existe pas.  
  
4.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> .  
  
5.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.MergePublication> en utilisant la connexion au serveur de publication de l'étape 1. Spécifiez <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> et <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Si cette méthode retourne `false`, les propriétés spécifiées à l'étape 5 sont incorrectes ou la publication n'existe pas sur le serveur.  
  
7.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> . Spécifiez le nom de l'Abonné et la base de données d'abonnement pour les paramètres *subscriber* et *subscriberDB* .  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple supprime un abonnement par extraction à une publication transactionnelle et supprime l'inscription de l'abonnement au niveau du serveur de publication.  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 Cet exemple supprime un abonnement par extraction à une publication de fusion et supprime l'inscription de l'abonnement au niveau du serveur de publication.  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## <a name="see-also"></a>Voir aussi  
 [S’abonner à des publications](subscribe-to-publications.md)   
 [Bonnes pratiques en matière de sécurité de la réplication](security/replication-security-best-practices.md)  
  
  
