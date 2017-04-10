---
title: "D&#233;sactiver la publication et la distribution | Microsoft Docs"
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
  - "désactivation de la publication"
  - "publication [réplication SQL Server], désactivation"
  - "distribution, désactiver [réplication SQL Server]"
  - "suppression de la réplication"
  - "réplication [SQL Server], suppression"
  - "désactivation de la réplication"
  - "désactivation de la distribution"
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# D&#233;sactiver la publication et la distribution
  Cette rubrique explique comment désactiver la publication et la distribution dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 Vous pouvez effectuer les opérations suivantes :  
  
-   Supprimer toutes les bases de données de distribution sur le serveur de distribution.  
  
-   Désactiver tous les serveurs de publication utilisant le serveur de distribution et supprimer toutes les publications situées sur ces serveurs de publication.  
  
-   Supprimer tous les abonnements aux publications. Les données des bases de données de publication et d'abonnement ne sont pas supprimées ; elles perdent toutefois leur lien de synchronisation aux bases de données de publication. Si vous souhaitez supprimer les données de l'Abonné, faites-le manuellement.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Configuration requise](#Prerequisites)  
  
-   **Pour désactiver la publication et la distribution à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Configuration requise  
  
-   Pour désactiver la publication et la distribution, toutes les bases de données de distribution et de publication doivent être en ligne. S'il existe des *instantanés de base de données* pour les bases de données de distribution ou de publication, vous devez les supprimer avant de désactiver la publication et la distribution. Un instantané de base de données est une copie hors ligne en lecture seule d'une base de données et n'a pas de lien avec un instantané de réplication. Pour plus d’informations, consultez [instantanés de base de données & #40 ; SQL Server & #41 ;](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Désactivez la publication et la distribution à l'aide de l'Assistant Désactivation de publication et de distribution.  
  
#### Pour désactiver la publication et la distribution  
  
1.  Connectez-vous au serveur de publication ou au serveur de distribution que vous souhaitez désactiver dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Avec le bouton droit le **réplication** puis cliquez sur **désactiver la publication et Distribution**.  
  
3.  Exécutez les étapes de l'Assistant Désactivation de la publication et de la distribution.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 La publication et la distribution peuvent être désactivées par programme à l'aide des procédures stockées de réplication.  
  
#### Pour désactiver la publication et la distribution  
  
1.  Arrêtez tous les travaux liés à la réplication. Pour obtenir la liste des noms de travaux, consultez la section « Sécurité de l'Agent dans l'Agent SQL Server » de [Modèle de sécurité de l'Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
2.  Sur chaque abonné sur la base de données d’abonnement, exécutez [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) pour supprimer les objets de réplication de la base de données. Cette procédure stockée ne supprimera pas les travaux de réplication sur le serveur de distribution.  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) pour supprimer les objets de réplication de la base de données.  
  
4.  Si le serveur de publication utilise un serveur de distribution distant, exécutez [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md).  
  
5.  Sur le serveur de distribution, exécutez [sp_dropdistpublisher](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md). Cette procédure stockée doit être exécutée une fois pour chaque serveur de publication inscrit sur le serveur de distribution.  
  
6.  Sur le serveur de distribution, exécutez [sp_dropdistributiondb](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md) pour supprimer la base de données de distribution. Cette procédure stockée doit être exécutée une fois pour chaque base de données de distribution sur le serveur de distribution. Cela supprime également tous les travaux de l'Agent de lecture de la file d'attente associés à la base de données de distribution.  
  
7.  Sur le serveur de distribution, exécutez [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md) pour supprimer la désignation du serveur de distribution à partir du serveur.  
  
    > [!NOTE]  
    >  Si tous les objets de publication et la distribution de réplication ne sont pas supprimés avant d’exécuter [sp_dropdistpublisher](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md) et [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md), ces procédures retourneront une erreur. Pour supprimer les objets toutes liées à la réplication lorsqu’un serveur de publication ou de distribution est supprimée, le **@no_checks** paramètre doit être défini sur **1**. Si un serveur de publication ou de distribution est hors connexion ou inaccessible, le **@ignore_distributor** paramètre peut être défini sur **1** afin qu’ils puissent être supprimés ; Cependant, toute publication et distribuer des objets conservés doivent être supprimés manuellement.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple de script supprime des objets de réplication de la base de données d'abonnement.  
  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/disable-publishing-and-d_1.sql)]  
  
 Cet exemple de script désactive la publication et la distribution sur un serveur faisant office de serveur de publication et de serveur de distribution et supprime la base de données de distribution.  
  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/disable-publishing-and-d_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
  
#### Pour désactiver la publication et la distribution  
  
1.  Supprimez tous les abonnements aux publications qui utilisent le serveur de distribution. Pour plus d'informations, consultez [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md) et [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md).  
  
2.  Supprimez toutes les publications qui utilisent le serveur de distribution et désactivez la publication pour toutes les bases de données si le serveur de publication et le serveur de distribution se trouvent sur le même serveur. Pour plus d'informations, voir [Delete a Publication](../../relational-databases/replication/publish/delete-a-publication.md).  
  
3.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
4.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.DistributionPublisher> classe. Spécifiez le <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> propriété, puis transmettez la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet de l’étape 3.  
  
5.  (Facultatif) Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet et vérifiez que le serveur de publication existe. Si cette méthode retourne **false**, le nom du serveur de publication défini à l'étape 4 est incorrect ou le serveur de publication n'est pas utilisé par ce serveur de distribution.  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> méthode. Passez la valeur **true** pour *force* si le serveur de publication et le serveur de distribution se trouvent sur des serveurs différents, et lorsque le serveur de publication doit être désinstallé au niveau du serveur de distribution sans commencer par vérifier que les publications n'existent plus sur le serveur de publication.  
  
7.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationServer> classe. Passez le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet de l’étape 3.  
  
8.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> (méthode). Passez la valeur **true** pour *force* pour supprimer tous les objets de réplication au niveau du serveur de distribution sans commencer par vérifier que toutes les bases de données de publication locales ont été désactivées et que les bases de données de distribution ont été désinstallées.  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple supprime l'inscription du serveur de publication au niveau du serveur de distribution, supprime la base de données de distribution et désinstalle le serveur de distribution.  
  
 [!code-csharp[HowTo#rmo_DropDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 Cet exemple désinstalle le serveur de distribution sans commencer par désactiver les bases de données de publication locales ni supprimer la base de données de distribution.  
  
 [!code-csharp[HowTo#rmo_DropDistPubForce](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## Voir aussi  
 [Concepts liés à Replication Management Objects](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Concepts liés aux procédures stockées système de réplication](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  