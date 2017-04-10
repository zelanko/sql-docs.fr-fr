---
title: "Sp&#233;cifier un programme de r&#233;solution d&#39;articles de fusion | Microsoft Docs"
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
  - "articles [réplication SQL Server], résolution des conflits"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
  - "résolution des conflits de réplication de fusion [réplication SQL Server], résolveurs d'articles de fusion"
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Sp&#233;cifier un programme de r&#233;solution d&#39;articles de fusion
  Cette rubrique explique comment spécifier un programmes de résolution d'articles de fusion dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour spécifier un programme de résolution d'articles de fusion à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   La réplication de fusion accepte les types de programmes de résolution d'articles suivants :  
  
    -   Programme de résolution par défaut. Le comportement du programme de résolution par défaut varie selon que l'abonnement est un abonnement client ou serveur. Pour plus d’informations sur la spécification du type d’abonnement, consultez [spécifier un Type d’abonnement de fusion et de priorité pour la résolution des conflits & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md).  
  
    -   Programme de résolution personnalisé que vous avez écrit. Il peut s'agir d'un gestionnaire de logique métier (écrit en code managé) ou d'un programme de résolution COM personnalisé. Pour plus d’informations, consultez [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md). Si vous devez implémenter une logique personnalisée qui est exécutée pour chaque ligne répliquée, pas seulement pour les lignes en conflit, consultez [implémenter un gestionnaire de logique métier pour un Article de fusion](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
    -   Un résolveur de basé sur COM standard, qui est inclus dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Pour utiliser un programme de résolution autre que le programme de résolution par défaut, vous devez le copier sur l'ordinateur exécutant l'Agent de fusion et l'inscrire (si vous utilisez un gestionnaire de logique métier, il doit être également inscrit sur le serveur de publication). L'Agent de fusion s'exécute sur :  
  
    -   le serveur de distribution pour un abonnement envoyé ;  
  
    -   l'Abonné pour un abonnement extrait ;  
  
    -   le serveur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] IIS (Internet Information Services) pour un abonnement extrait qui utilise la synchronisation Web.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Après avoir enregistré le programme de résolution, spécifier qu’un article doit l’utiliser sur le **résolveur** onglet du **Propriétés de l’Article - \< Article>** boîte de dialogue, qui est disponible dans l’Assistant Nouvelle Publication et la **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [Création d’une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour spécifier un programme de résolution  
  
1.  Sur le **Articles** page de l’Assistant Nouvelle Publication ou le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une table.  
  
2.  Cliquez sur **Propriétés de l'article**puis sur **Définir les propriétés de l'article de la table en surbrillance**.  
  
3.  Sur le **Propriétés de l’Article - \< Article>** cliquez sur le **résolution** onglet.  
  
4.  Sélectionnez **utiliser un résolveur personnalisé (inscrit sur le serveur de distribution)**, et puis dans la liste, cliquez sur le programme de résolution.  
  
5.  Si le programme de résolution nécessite une entrée (par exemple, un nom de colonne), spécifiez-le dans le **Entrez les informations requises par le résolveur** zone de texte.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  Répétez la procédure pour chaque article exigeant un programme de résolution.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour inscrire un outil personnalisé de résolution des conflits  
  
1.  Si vous projetez d'inscrire votre propre outil personnalisé de résolution des conflits, créez-en un répondant à l'un des types suivants :  
  
    -   Programme de résolution s'appuyant sur le code managé, comme un gestionnaire de logique métier. Pour plus d'informations, voir [Implement a Business Logic Handler for a Merge Article](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
    -   Programme de résolution s'appuyant sur des procédures stockées et sur COM. Pour plus d'informations, voir [Implement a Custom Conflict Resolver for a Merge Article](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md).  
  
2.  Pour déterminer si le programme de résolution souhaité est déjà inscrit, exécutez [sp_enumcustomresolvers & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) sur une base de données de l’éditeur. Une description du programme de résolution personnalisé est alors affichée, de même que le CLSID de chaque programme de résolution s'appuyant sur l'architecture COM inscrit sur le serveur de distribution ou des informations sur l'assembly managé pour chaque gestionnaire de logique métier inscrit sur le serveur de distribution.  
  
3.  Si le programme de résolution personnalisé souhaité n’est pas déjà inscrit, exécutez [sp_registercustomresolver & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md) sur le serveur de distribution. Spécifiez un nom pour le programme de résolution pour **@article_resolver**; pour un gestionnaire de logique métier, c’est le nom convivial de l’assembly. Pour les programmes de résolution COM, spécifiez le CLSID de la DLL pour **@resolver_clsid**, et pour un gestionnaire de logique métier, spécifiez la valeur **true** pour **@is_dotnet_assembly**, le nom de l’assembly pour **@dotnet_assembly_name**, et le nom qualifié complet de la classe qui remplace <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> de **@dotnet_class_name**.  
  
    > [!NOTE]  
    >  Si un assembly de gestionnaire de logique métier n’est pas déployé dans le même répertoire que l’exécutable de l’Agent de fusion, dans le même répertoire que l’application qui démarre de façon synchrone l’Agent de fusion ou dans le global assembly cache (GAC), vous devez spécifier le chemin d’accès complet avec le nom de l’assembly pour **@dotnet_assembly_name**.  
  
4.  Si le programme de résolution est un programme de résolution s'appuyant sur l'architecture COM :  
  
    -   Copiez la DLL de programme de résolution personnalisé sur le serveur de distribution pour les abonnements par émission de données ou sur l'Abonné pour les abonnements par extraction.  
  
        > [!NOTE]  
        >  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] résolveurs personnalisés se trouve dans le [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]répertoire COM.  
  
    -   Utilisez regsvr32.exe pour inscrire la DLL du programme de résolution personnalisé auprès du système d'exploitation. Par exemple, l'exécution de la commande suivante à partir de l'invite de commandes inscrit l'Outil de résolution des conflits d'addition [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  Si le programme de résolution est un gestionnaire de logique métier, déployez l’assembly dans le même dossier que l’exécutable de l’Agent de fusion (replmerg.exe), dans le même dossier qu’une application qui appelle l’Agent de fusion, ou dans le dossier spécifié pour le **@dotnet_assembly_name** à l’étape 3.  
  
    > [!NOTE]  
    >  L'emplacement d'installation par défaut du fichier exécutable de l'Agent de fusion est [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.  
  
#### Pour spécifier un programme de résolution personnalisé lors de la définition d'un article de fusion  
  
1.  Si vous projetez d'utiliser un outil personnalisé de résolution des conflits, créez et inscrivez le programme de résolution à l'aide de la procédure précitée.  
  
2.  Sur le serveur de publication, exécutez [sp_enumcustomresolvers & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) Notez le nom du programme de résolution personnalisé souhaité dans la **valeur** champ du jeu de résultats.  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Spécifiez le nom du programme de résolution de l’étape 2 pour **@article_resolver** et toute entrée requise pour le programme de résolution personnalisé à l’aide de la **@resolver_info** paramètre. Pour stockée résolveurs personnalisés sur des procédures, **@resolver_info** est le nom de la procédure stockée. Pour plus d’informations sur les entrées requises pour les programmes de résolution fournis par [!INCLUDE[msCoName](../../../includes/msconame-md.md)], consultez [Microsoft résolveurs COM](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
#### Pour spécifier ou modifier un programme de résolution personnalisé pour un article de fusion existant  
  
1.  Pour déterminer si un programme de résolution personnalisé a été défini pour un article, ou pour obtenir le nom du programme de résolution, exécutez [sp_helpmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). S’il existe un programme de résolution personnalisé défini pour l’article, son nom s’affichera dans le **article_resolver** champ. Toute entrée fournie pour le programme de résolution s’affichera dans le **resolver_info** champ du jeu de résultats.  
  
2.  Sur le serveur de publication, exécutez [sp_enumcustomresolvers & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) Notez le nom du programme de résolution personnalisé souhaité dans la **valeur** champ du jeu de résultats.  
  
3.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez la valeur **article_resolver**, y compris le chemin d’accès complet pour les gestionnaires de logique métier pour **@property**, et le nom du programme de résolution personnalisé souhaité à l’étape 2 pour **@value**.  
  
4.  Pour modifier toute entrée requise pour le programme de résolution personnalisé, exécutez [sp_changemergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) encore une fois. Spécifiez la valeur **resolver_info** pour **@property** et toute entrée requise pour le programme de résolution personnalisé pour **@value**. Pour stockée résolveurs personnalisés sur des procédures, **@resolver_info** est le nom de la procédure stockée. Pour plus d’informations sur les entrées requises, consultez la page [Microsoft résolveurs COM](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
#### Pour annuler l'inscription d'un outil personnalisé de résolution des conflits  
  
1.  Sur le serveur de publication, exécutez [sp_enumcustomresolvers & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) Notez le nom du programme de résolution personnalisé à supprimer dans la **valeur** champ du jeu de résultats.  
  
2.  Exécutez [sp_unregistercustomresolver & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md) sur le serveur de distribution. Spécifiez le nom complet du programme de résolution personnalisé à l’étape 1 pour **@article_resolver**.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple crée un article et spécifie que l'Outil de résolution des conflits de moyenne [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit être utilisé pour calculer la moyenne de la colonne **UnitPrice** en cas de conflit.  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../relational-databases/replication/codesnippet/tsql/specify-a-merge-article-_1.sql)]  
  
 Cet exemple modifie un article de manière à spécifier que l'Outil de résolution des conflits d'addition [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit être utilisé pour calculer la somme de la colonne **UnitsOnOrder** en cas de conflit.  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../relational-databases/replication/codesnippet/tsql/specify-a-merge-article-_2.sql)]  
  
## Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Implémenter un gestionnaire de logique métier pour un article de fusion](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
  