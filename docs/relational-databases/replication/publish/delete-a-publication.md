---
title: "Supprimer une publication | Microsoft Docs"
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
  - "suppression de publications"
  - "publications [réplication SQL Server], suppression"
  - "articles [réplication SQL Server], suppression"
  - "suppression de publications"
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Supprimer une publication
  Cette rubrique explique comment supprimer une publication dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Pour supprimer une publication à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Supprimer les publications dans le dossier **Publications locales** de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
#### Pour supprimer une publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Avec le bouton droit de la publication que vous souhaitez supprimer, puis cliquez sur **Supprimer**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Il est possible de supprimer des publications par programme en utilisant les procédures stockées de réplication. Les procédures stockées à utiliser dépendent du type de publication à supprimer.  
  
> [!NOTE]  
>  La suppression d'une publication ne supprime pas les objets publiés de la base de données de publication ni les objets correspondants de la base de données d'abonnement. Utilisez la commande `DROP <object>` pour supprimer manuellement ces objets, si nécessaire.  
  
#### Pour supprimer une publication d'instantané ou une publication transactionnelle  
  
1.  Procédez de l'une des manières suivantes :  
  
    -   Pour supprimer une publication, exécutez [sp_droppublication](../../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md) sur le serveur de publication sur la base de données de publication.  
  
    -   Pour supprimer toutes les publications d’et tous les objets de réplication à partir d’une base de données publiée, exécutez [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) sur le serveur de publication. Spécifiez la valeur **tran** pour **@type**. (Facultatif) Si le serveur de distribution n’est pas accessible ou si l’état de la base de données est suspect ou hors connexion, spécifiez une valeur de **1** pour **@force**. (Facultatif) Spécifiez le nom de la base de données **@dbname** Si [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) n’est pas exécuté sur la base de données de publication.  
  
        > [!NOTE]  
        >  La valeur **1** pour **@force** peut laisser des objets liés à la réplication de publication dans la base de données.  
  
2.  (Facultatif) Si aucune autre publication de cette base de données, exécutez [sp_replicationdboption & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Pour désactiver la publication de la base de données actuelle à l’aide de la réplication transactionnelle ou capture instantanée.  
  
3.  (Facultatif) Sur la base de données d’abonnement de l’abonné, exécutez [sp_subscription_cleanup](../../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) pour supprimer les métadonnées de réplication restantes dans la base de données d’abonnement.  
  
#### Pour supprimer une publication de fusion  
  
1.  Procédez de l'une des manières suivantes :  
  
    -   Pour supprimer une publication, exécutez [sp_dropmergepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md) sur la base de données de publication de l’éditeur.  
  
    -   Pour supprimer toutes les publications d’et tous les objets de réplication à partir d’une base de données publiée, exécutez [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) sur le serveur de publication. Spécifiez la valeur **merge** pour **@type**. (Facultatif) Si le serveur de distribution n’est pas accessible ou si l’état de la base de données est suspect ou hors connexion, spécifiez une valeur de **1** pour **@force**. (Facultatif) Spécifiez le nom de la base de données **@dbname** Si [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) n’est pas exécuté sur la base de données de publication.  
  
        > [!NOTE]  
        >  La valeur **1** pour **@force** peut laisser des objets liés à la réplication de publication dans la base de données.  
  
2.  (Facultatif) Si aucune autre publication de cette base de données, exécutez [sp_replicationdboption & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) Pour désactiver la publication de la base de données actuelle à l’aide de la réplication de fusion.  
  
3.  (Facultatif) Sur la base de données d’abonnement de l’abonné, exécutez [sp_mergesubscription_cleanup & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md) Pour supprimer les métadonnées de réplication restantes dans la base de données d’abonnement.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple montre comment supprimer une publication transactionnelle et désactiver la publication transactionnelle d'une base de données. Cet exemple suppose que tous les abonnements ont été supprimés précédemment. Pour plus d'informations, consultez [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) ou [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_droppublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_1.sql)]  
  
 Cet exemple montre comment supprimer une publication de fusion et désactiver la publication de fusion d'une base de données. Cet exemple suppose que tous les abonnements ont été supprimés précédemment. Pour plus d'informations, consultez [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) ou [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md).  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez supprimer des publications par programme à l'aide d'objets RMO (Replication Management Objects). Les classes RMO que vous utilisez pour supprimer une publication dépendent du type de publication que vous supprimez.  
  
#### Pour supprimer une publication transactionnelle ou d'instantané  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransPublication> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication et définissez la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
4.  Vérifier la <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propriété pour vérifier que la publication existe. Si la valeur de cette propriété est **false**, les propriétés de la publication définies à l'étape 3 sont incorrectes ou la publication n'existe pas.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> méthode.  
  
6.  (Facultatif) Si aucune autre publication transactionnelle n'existe pour cette base de données, vous pouvez désactiver la base de données pour la publication transactionnelle en procédant comme suit :  
  
    1.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> classe. Définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à l’instance de <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1.  
  
    2.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode. Si cette méthode retourne **false**, confirmez que la base de données existe.  
  
    3.  Définir le <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> propriété **false**.  
  
    4.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (méthode).  
  
7.  Fermez les connexions.  
  
#### Pour supprimer une publication de fusion  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> et <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propriétés de la publication et définissez la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
4.  Vérifier la <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propriété pour vérifier que la publication existe. Si la valeur de cette propriété est **false**, les propriétés de la publication définies à l'étape 3 sont incorrectes ou la publication n'existe pas.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> méthode.  
  
6.  (Facultatif) Si aucune autre publication de fusion n'existe pour cette base de données, vous pouvez désactiver la base de données pour la publication de fusion en procédant comme suit :  
  
    1.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> classe. Définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à l’instance de <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1.  
  
    2.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode. Si cette méthode retourne **false**, vérifiez que la base de données existe.  
  
    3.  Définir le <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> propriété **false**.  
  
    4.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (méthode).  
  
7.  Fermez les connexions.  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 L'exemple suivant supprime une publication transactionnelle. Si aucune autre publication transactionnelle n'existe pour cette base de données, la publication transactionnelle est également désactivée.  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 L'exemple suivant supprime une publication de fusion. Si aucune autre publication de fusion n'existe pour cette base de données, la publication de fusion est également désactivée.  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## Voir aussi  
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  