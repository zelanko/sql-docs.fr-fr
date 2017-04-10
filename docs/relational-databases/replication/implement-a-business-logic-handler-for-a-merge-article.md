---
title: "Impl&#233;menter un gestionnaire de logique m&#233;tier pour un article de fusion | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "résolution des conflits de réplication de fusion [réplication SQL Server], gestionnaires de logique métier"
  - "gestionnaires de logique métier de réplication de fusion [réplication SQL Server]"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
  - "gestionnaires de logique métier [réplication SQL Server]"
  - "BusinessLogicModule, classe"
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Impl&#233;menter un gestionnaire de logique m&#233;tier pour un article de fusion
  Cette rubrique décrit comment implémenter un gestionnaire de logique métier pour un article de fusion dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de la programmation de réplication ou d'objets RMO (Replication Management Objects).  
  
 Le <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> espace de noms implémente une interface qui vous permet d’écrire une logique métier complexe pour gérer les événements qui se produisent pendant le processus de synchronisation de la réplication de fusion. Les méthodes dans le gestionnaire de logique métier peuvent être appelées par le processus de réplication pour chaque ligne modifiée qui est répliquée pendant la synchronisation.  
  
 La procédure globale permettant d'implémenter un gestionnaire de logique métier est la suivante :  
  
1.  Créez l'assembly du gestionnaire de logique métier.  
  
2.  Inscrivez l'assembly sur le serveur de distribution.  
  
3.  Déployez l'assembly sur le serveur où l'Agent de fusion s'exécute. Pour un abonnement par extraction, l'agent s'exécute sur l'Abonné, alors que pour un abonnement par émission de données, il s'exécute sur le serveur de distribution. Lorsque vous utilisez la synchronisation Web, l'agent s'exécute sur le serveur Web.  
  
4.  Créez un article qui utilise le gestionnaire de logique métier ou modifiez un article existant pour utiliser le gestionnaire de logique métier.  
  
 Le gestionnaire de logique métier que vous spécifiez est exécuté pour chaque ligne faisant l'objet d'une synchronisation. Une logique complexe et des appels à d'autres applications ou services réseau peuvent avoir une incidence sur les performances. Pour plus d’informations sur les gestionnaires de logique métier, consultez [exécution logique au cours de fusion synchronisation professionnels](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
 **Dans cette rubrique**  
  
-   **Pour implémenter un gestionnaire de logique métier pour un article de fusion à l'aide de :**  
  
     [Programmation de la réplication](#ReplProg)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="ReplProg"></a> Utilisation de la programmation de la réplication  
  
#### Pour créer et déployer un gestionnaire de logique métier  
  
1.  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, créez un projet pour l'assembly .NET contenant le code qui implémente le gestionnaire de logique métier.  
  
2.  Ajoutez des références au projet pour les espaces de noms ci-dessous.  
  
    |Référence d'assembly|Emplacement|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (installation par défaut)|  
    |<xref:System.Data>|GAC (composant du .NET Framework)|  
    |<xref:System.Data.Common>|GAC (composant du .NET Framework)|  
  
3.  Ajouter une classe qui remplace le <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> (classe).  
  
4.  Implémentez la <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> pour indiquer les types de modifications qui sont gérés.  
  
5.  Remplacer une ou plusieurs des méthodes suivantes de la <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> classe :  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> -appelée lors d’une modification de données est validée pendant la synchronisation.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> -méthode appelée lorsqu’une erreur se produit lorsqu’une instruction DELETE est en cours de téléchargement ou de transfert.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> -méthode appelée lorsque des instructions DELETE sont chargés ou téléchargés.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> -méthode appelée lorsqu’une erreur se produit lorsqu’une instruction INSERT est en cours de téléchargement ou de transfert.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> -méthode appelée lorsque les instructions INSERT sont chargés ou téléchargés.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> -appelé lorsque les instructions de mise à jour en conflit se produisent sur l’éditeur et l’abonné.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> -appelée lorsque des instructions UPDATE entrent en conflit avec des instructions DELETE sur l’éditeur et l’abonné.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> -méthode appelée lorsqu’une erreur se produit lorsqu’une instruction UPDATE est en cours de téléchargement ou de transfert.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> -méthode appelée lorsque les instructions UPDATE sont chargés ou téléchargés.  
  
6.  Générez le projet pour créer l'assembly du gestionnaire de logique métier.  
  
7.  Déployez l'assembly dans le répertoire contenant le fichier exécutable de l'Agent de fusion (replmerg.exe), qui est pour une installation par défaut [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM, ou installez-le dans le .NET Global Assembly Cache (GAC). Vous devez installer l'assembly dans le GAC seulement si des applications autres que l'Agent de fusion requièrent l'accès à l'assembly. L’assembly peut être installé dans le GAC à l’aide de l’outil Global Assembly Cache (**Gacutil.exe)** fourni dans le SDK .NET Framework.  
  
    > [!NOTE]  
    >  Un gestionnaire de logique métier doit être déployé sur chaque serveur sur lequel l'Agent de fusion s'exécute, ce qui inclut le serveur IIS qui héberge replisapi.dll lors de l'utilisation de la synchronisation Web.  
  
#### Pour inscrire un gestionnaire de logique métier  
  
1.  Sur le serveur de publication, exécutez [sp_enumcustomresolvers & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) Pour vérifier que l’assembly n’a pas déjà été inscrit comme un gestionnaire de logique métier.  
  
2.  Sur le serveur de distribution, exécutez [sp_registercustomresolver & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md), en spécifiant un nom convivial pour le Gestionnaire de logique métier pour **@article_resolver**, une valeur de **true** pour **@is_dotnet_assembly**, le nom de l’assembly pour **@dotnet_assembly_name**, et le nom qualifié complet de la classe qui substitue <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> de **@dotnet_class_name**.  
  
    > [!NOTE]  
    >  Si l’assembly n’est pas déployé dans le même répertoire que l’exécutable de l’Agent de fusion, dans le même répertoire que l’application qui démarre de façon synchrone l’Agent de fusion ou dans le global assembly cache (GAC), vous devez spécifier le chemin d’accès complet avec le nom de l’assembly pour **@dotnet_assembly_name**. Lorsque vous utilisez la synchronisation Web, vous devez spécifier l'emplacement de l'assembly sur le serveur Web.  
  
#### Pour utiliser un gestionnaire de logique métier avec un nouvel article de table  
  
1.  Exécutez [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Pour définir un article, en spécifiant le nom convivial du Gestionnaire de logique métier pour **@article_resolver**. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Pour utiliser un gestionnaire de logique métier avec un article de table existant  
  
1.  Exécutez [sp_changemergearticle & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), en spécifiant **@publication**, **@article**, une valeur de **article_resolver** pour **@property**, et le nom convivial du Gestionnaire de logique métier pour **@value**.  
  
###  <a name="TsqlExample"></a> Exemples (programmation de la réplication)  
 Cet exemple illustre un gestionnaire de logique métier qui crée un journal d'audit.  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 L'exemple ci-dessous inscrit un assembly du gestionnaire de logique métier sur le serveur de distribution et modifie un article de fusion existant afin d'utiliser cette logique métier personnalisée.  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../relational-databases/replication/codesnippet/tsql/implement-a-business-log_3.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
  
#### Pour créer un gestionnaire de logique métier  
  
1.  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, créez un projet pour l'assembly .NET contenant le code qui implémente le gestionnaire de logique métier.  
  
2.  Ajoutez des références au projet pour les espaces de noms ci-dessous.  
  
    |Référence d'assembly|Emplacement|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (installation par défaut)|  
    |<xref:System.Data>|GAC (composant du .NET Framework)|  
    |<xref:System.Data.Common>|GAC (composant du .NET Framework)|  
  
3.  Ajouter une classe qui remplace le <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> (classe).  
  
4.  Implémentez la <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> pour indiquer les types de modifications qui sont gérés.  
  
5.  Remplacer une ou plusieurs des méthodes suivantes de la <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> classe :  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> -appelée lors d’une modification de données est validée pendant la synchronisation.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> -appelée si une erreur se produit lorsqu’une instruction DELETE est en cours de téléchargement ou de transfert.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> -méthode appelée lorsque des instructions DELETE sont chargés ou téléchargés.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> -méthode appelée si une erreur se produit lorsqu’une instruction INSERT est en cours de téléchargement ou de transfert.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> -méthode appelée lorsque les instructions INSERT sont chargés ou téléchargés.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> -appelé lorsque les instructions de mise à jour en conflit se produisent sur l’éditeur et l’abonné.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> -appelée lorsque des instructions UPDATE entrent en conflit avec des instructions DELETE sur l’éditeur et l’abonné.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> -méthode appelée si une erreur se produit lorsqu’une instruction UPDATE est en cours de téléchargement ou de transfert.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> -méthode appelée lorsque les instructions UPDATE sont chargés ou téléchargés.  
  
    > [!NOTE]  
    >  Tous les conflits d'un article qui ne sont pas gérés explicitement par votre logique métier personnalisée sont gérés par le programme de résolution par défaut pour l'article.  
  
6.  Générez le projet pour créer l'assembly du gestionnaire de logique métier.  
  
#### Pour inscrire un gestionnaire de logique métier  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationServer> classe. Passez le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1.  
  
3.  Appelez <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> et vérifiez retourné <xref:System.Collections.ArrayList> objet pour s’assurer que l’assembly n’a pas déjà été inscrit comme un gestionnaire de logique métier.  
  
4.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> (classe). Spécifiez les propriétés suivantes :  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> -le nom de l’assembly .NET. Si l'assembly n'est pas déployé dans le même répertoire que l'exécutable de l'Agent de fusion, dans le même répertoire que l'application qui démarre de façon synchrone l'Agent de fusion ou dans le GAC, vous devez inclure le chemin d'accès complet avec le nom de l'assembly. Vous devez inclure le chemin d'accès complet avec le nom de l'assembly lorsque vous utilisez un gestionnaire de logique métier avec la synchronisation Web ;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> -le nom qualifié complet de la classe qui substitue <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> et implémente le Gestionnaire de logique métier.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> -un nom convivial que vous utilisez lorsque vous accédez à Gestionnaire de logique métier.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> -valeur **true**.  
  
#### Pour déployer un gestionnaire de logique métier  
  
1.  Déployez l'assembly sur le serveur où l'Agent de fusion s'exécute, dans l'emplacement de fichier qui a été spécifié quand le gestionnaire de logique métier a été inscrit sur le serveur de distribution. Pour un abonnement par extraction, l'agent s'exécute sur l'Abonné, alors que pour un abonnement par émission de données, il s'exécute sur le serveur de distribution. Lorsque vous utilisez la synchronisation Web, l'agent s'exécute sur le serveur Web. Si le chemin d'accès complet n'a pas été inclus avec le nom de l'assembly lorsque le gestionnaire de logique métier a été inscrit, déployez l'assembly dans le même répertoire que l'exécutable de l'Agent de fusion, dans le même répertoire que l'application qui démarre de façon synchrone l'Agent de fusion. Vous pouvez installer l'assembly dans le GAC si plusieurs applications utilisent le même assembly.  
  
#### Pour utiliser un gestionnaire de logique métier avec un nouvel article de table  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeArticle> classe. Définissez les propriétés suivantes :  
  
    -   Le nom de l’article pour <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Le nom de la publication pour <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   Le nom de la base de données de publication pour <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>.  
  
    -   Le nom convivial du Gestionnaire de logique métier (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) pour <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.Article.Create%2A> méthode. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Pour utiliser un gestionnaire de logique métier avec un article de table existant  
  
1.  Créer une connexion au serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeArticle> classe.  
  
3.  Définir le <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, et <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Propriétés.  
  
4.  Configuration de la connexion à l’étape 1 pour les <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode pour obtenir les propriétés de l’objet. Si cette méthode retourne **false**, soit les propriétés de l'article ont été définies de manière incorrecte à l'étape 3, soit l'article n'existe pas. Pour plus d'informations, voir [View and Modify Article Properties](../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
6.  Définissez le nom convivial du Gestionnaire de logique métier pour <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>. C’est la valeur de la <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> propriété spécifiée lors de l’inscription du Gestionnaire de logique métier.  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple illustre un gestionnaire de logique métier qui enregistre les informations sur les insertions, les mises à jour et les suppressions sur l'Abonné.  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 Cet exemple illustre l'inscription d'un gestionnaire de logique métier sur le serveur de distribution.  
  
 [!code-csharp[HowTo#rmo_RegisterBLH_10](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 Cet exemple illustre la modification d'un article existant pour utiliser le gestionnaire de logique métier.  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## Voir aussi  
 [Implémenter un outil personnalisé de résolution des conflits pour un article de fusion](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [Déboguer un gestionnaire de logique métier & #40 ; Programmation de la réplication & #41 ;](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Concepts liés à Replication Management Objects](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)  
  
  