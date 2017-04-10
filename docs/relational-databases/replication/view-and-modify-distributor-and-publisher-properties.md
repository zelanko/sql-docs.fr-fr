---
title: "Afficher et modifier les propri&#233;t&#233;s d&#39;un serveur de distribution ou d&#39;un serveur de publication | Microsoft Docs"
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
  - "viewing replication properties"
  - "Distributors [SQL Server replication], modifying"
  - "modifying replication properties, Distributors"
  - "distributeurs [réplication SQL Server], propriétés"
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# Afficher et modifier les propri&#233;t&#233;s d&#39;un serveur de distribution ou d&#39;un serveur de publication
  Cette rubrique décrit comment afficher et modifier les propriétés du serveur de distribution et du serveur de publication dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour afficher et modifier les propriétés d'un serveur de publication ou d'un serveur de distribution à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Pour les serveurs de publication exécutant des versions antérieures à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], un utilisateur du rôle serveur fixe **sysadmin** peut enregistrer des abonnés sur la page **Abonnés** . À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], il n'est plus nécessaire d'inscrire de manière explicite les abonnés pour la réplication.  
  
###  <a name="Security"></a> Sécurité  
 Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour afficher et modifier les propriétés du serveur de distribution  
  
1.  Connectez-vous au serveur de distribution dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Avec le bouton droit le **réplication** puis cliquez sur **des propriétés de serveur de distribution**.  
  
3.  Afficher et modifier les propriétés dans le **Propriétés du serveur de distribution - \< serveur de distribution>** boîte de dialogue.  
  
    -   Pour afficher et modifier les propriétés d’une base de données de distribution, cliquez sur le bouton des propriétés (**...**) pour la base de données sur le **Général** page de boîte de trouve.  
  
    -   Pour afficher et modifier les propriétés de l’éditeur associées avec le serveur de distribution, cliquez sur le bouton des propriétés (**...**) pour le serveur de publication sur le **éditeurs** page de la boîte de dialogue.  
  
    -   Pour accéder aux profils des agents de réplication, cliquez sur le bouton **Profils par défaut** sur la page **Général** de la boîte de dialogue. Pour plus d'informations, voir [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
    -   Pour modifier le mot de passe du compte utilisé lors de l'exécution des procédures stockées administratives sur le serveur de publication et de la mise à jour des informations sur le serveur de distribution, entrez un nouveau mot de passe dans les zones **Mot de passe** et **Confirmer le mot de passe** sur la page **Serveurs de publication** de la boîte de dialogue. Pour plus d’informations, consultez [sécuriser le serveur de distribution](../../relational-databases/replication/security/secure-the-distributor.md).  
  
4.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
#### Pour afficher et modifier les propriétés du serveur de publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Avec le bouton droit le **réplication** puis cliquez sur **Propriétés de l’éditeur**.  
  
3.  Afficher et modifier les propriétés dans le **des propriétés de serveur de publication - \< publication >** boîte de dialogue.  
  
    -   Un utilisateur du rôle serveur fixe **sysadmin** peut activer des bases de données pour la réplication sur la page **Bases de données de publication** . L’activation d’une base de données ne publie pas cette base de données ; au lieu de cela, il permet à un utilisateur le **db_owner** rôle de base de données fixe pour cette base de données créer une ou plusieurs publications dans la base de données.  
  
4.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les propriétés du serveur de publication et du serveur de distribution peuvent être affichées par programme en utilisant des procédures stockées de réplication.  
  
#### Pour afficher les propriétés du serveur de distribution et de la base de données de distribution  
  
1.  Exécutez [sp_helpdistributor](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md) pour renvoyer des informations sur le serveur de distribution, la base de données de distribution et le répertoire de travail.  
  
2.  Exécutez [sp_helpdistributiondb](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md) pour renvoyer les propriétés d’une base de données de distribution spécifié.  
  
#### Pour modifier les propriétés du serveur de distribution et de la base de données de distribution  
  
1.  Sur le serveur de distribution, exécutez [sp_changedistributor_property](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md) pour modifier les propriétés du serveur de distribution.  
  
2.  Sur le serveur de distribution, exécutez [sp_changedistributiondb](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md) pour modifier les propriétés de base de données de distribution.  
  
3.  Sur le serveur de distribution, exécutez [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md) pour modifier le mot de passe du serveur de distribution.  
  
    > [!IMPORTANT]  
    >  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez stocker des informations d'identification dans un fichier de script, sécurisez le fichier pour empêcher tout accès non autorisé.  
  
4.  Sur le serveur de distribution, exécutez [sp_changedistpublisher](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md) pour modifier les propriétés d’un serveur de publication à l’aide du serveur de distribution.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 L'exemple de script [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant retourne des informations sur le serveur de distribution et sur la base de données de distribution.  
  
 [!code-sql[HowTo#sp_helpdistributor](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_1.sql)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_2.sql)]  
  
 Cet exemple modifie les périodes de rétention du serveur de distribution, le mot de passe utilisé lors de la connexion au serveur de distribution et l'intervalle auquel le serveur de distribution vérifie l'état de différents Agents de réplication (également appelé intervalle d'interrogation).  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez stocker des informations d'identification dans un fichier de script, sécurisez le fichier pour empêcher tout accès non autorisé.  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_3.sql)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_4.sql)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_5.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
  
#### Pour afficher et modifier les propriétés du serveur de distribution  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationServer> classe. Passez le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet de l’étape 1.  
  
3.  (Facultatif) Vérifier la <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> propriété pour vérifier que le serveur actuellement connecté est un serveur de distribution.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> méthode pour obtenir les propriétés du serveur.  
  
5.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour une ou plusieurs des propriétés du serveur de distribution qui peuvent être définies sur le <xref:Microsoft.SqlServer.Replication.ReplicationServer> objet.  
  
6.  (Facultatif) Si le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> propriété sur le <xref:Microsoft.SqlServer.Replication.ReplicationServer> a l’objet **true**, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> méthode à valider les modifications sur le serveur.  
  
#### Pour afficher et modifier les propriétés de base de données de distribution  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.DistributionDatabase> classe. Spécifiez la propriété name et transmettez le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet de l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés du serveur. Si cette méthode retourne **false**, la base de données avec le nom spécifié n’existe pas sur le serveur.  
  
4.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l’un de le <xref:Microsoft.SqlServer.Replication.DistributionDatabase> Propriétés pouvant être définies.  
  
5.  (Facultatif) Si le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> propriété sur le <xref:Microsoft.SqlServer.Replication.DistributionDatabase> a l’objet **true**, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> méthode à valider les modifications sur le serveur.  
  
#### Pour afficher et modifier les propriétés du serveur de publication  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.DistributionPublisher> classe. Spécifiez le <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> propriété et passez le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet de l’étape 1.  
  
3.  (Facultatif) Pour modifier les propriétés, définissez une nouvelle valeur pour l’un de le <xref:Microsoft.SqlServer.Replication.DistributionPublisher> Propriétés pouvant être définies.  
  
4.  (Facultatif) Si le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> propriété sur le <xref:Microsoft.SqlServer.Replication.DistributionPublisher> a l’objet **true**, appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> méthode à valider les modifications sur le serveur.  
  
#### Pour modifier le mot de passe pour la connexion administrative du serveur de publication au serveur de distribution  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationServer> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 1.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> méthode pour obtenir les propriétés de l’objet.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> (méthode). Passez la nouvelle valeur de mot de passe pour le paramètre *password* .  
  
    > [!IMPORTANT]  
    >  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez stocker des informations d'identification, utilisez les [Services de chiffrement](http://go.microsoft.com/fwlink/?LinkId=34733) fournis par [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
6.  (Facultatif) Effectuez la procédure suivante pour modifier le mot de passe sur chaque serveur de publication distant qui utilise ce serveur de distribution :  
  
    1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
    2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationServer> classe.  
  
    3.  Définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété à la connexion créée à l’étape 6 a.  
  
    4.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> méthode pour obtenir les propriétés de l’objet.  
  
    5.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> (méthode). Passez la nouvelle valeur de mot de passe spécifiée à l'étape 5 pour le paramètre *password* .  
  
###  <a name="PShellExample"></a> Exemple (RMO)  
 Cet exemple montre comment modifier les propriétés du serveur de distribution et de la base de données de distribution.  
  
> [!IMPORTANT]  
>  Pour éviter de stocker les informations d'identification dans le code, le nouveau mot de passe du serveur de distribution est fourni au moment de l'exécution.  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## Voir aussi  
 [Concepts liés à Replication Management Objects](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Désactiver la publication et la distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Concepts liés à Replication Management Objects](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Script d'information du serveur de distribution et du serveur de publication](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [Concepts liés aux procédures stockées système de réplication](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Afficher des informations et effectuer des tâches pour un serveur de publication & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
  
  