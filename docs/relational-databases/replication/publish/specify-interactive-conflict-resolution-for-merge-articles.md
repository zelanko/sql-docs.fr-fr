---
title: "Sp&#233;cifier la r&#233;solution interactive des conflits pour les articles de fusion | Microsoft Docs"
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
  - "résolution des conflits de réplication de fusion [réplication SQL Server], programmes de résolution interactifs"
  - "résolution interactive des conflits [réplication SQL Server]"
  - "articles [réplication SQL Server], résolution des conflits"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
ms.assetid: e298dea0-b5ef-4907-a745-cfad9793653f
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Sp&#233;cifier la r&#233;solution interactive des conflits pour les articles de fusion
  Cette rubrique explique comment spécifier la résolution interactive des conflits pour les articles de fusion dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la réplication fournit un résolveur interactif, ce qui permet de résoudre manuellement les conflits pendant la synchronisation à la demande dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] le Gestionnaire de synchronisation Windows. Quand la résolution de conflits est activée, résolvez les conflits de façon interactive au cours de la synchronisation, à l'aide du résolveur interactif. Le résolveur interactif est disponible via le Gestionnaire de synchronisation [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Pour plus d’informations, consultez [synchroniser Gestionnaire de synchronisation Windows utilisant un abonnement & #40 ; Le Gestionnaire de synchronisation Windows & #41 ;](../../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour spécifier la résolution interactive des conflits pour les articles de fusion, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Si une synchronisation est effectuée en dehors du Gestionnaire de synchronisation Windows (comme une synchronisation planifiée ou à la demande dans SQL Server Management Studio ou le moniteur de réplication), les conflits sont résolus automatiquement sans intervention de l'utilisateur, en utilisant l'outil de résolution des conflits par défaut spécifié pour l'article. Pour plus d’informations, consultez [Interactive Conflict Resolution](../../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour activer la résolution de conflits interactive pour un article  
  
1.  Sur le **Articles** page de l’Assistant Nouvelle Publication ou le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une table. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
2.  Cliquez sur **Propriétés de l'article**, puis cliquez sur **Définir les propriétés de l'article de Table en surbrillance** ou sur **Définir les propriétés de tous les articles de table**.  
  
3.  Sur le **Propriétés de l’Article - \< Article>** ou **Propriétés de l’Article - \< ArticleType>** cliquez sur le **résolution** onglet.  
  
4.  Sélectionnez **Autoriser l’abonné à résoudre les conflits interactivement pendant la synchronisation à la demande**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### Pour spécifier qu'un abonnement doit utiliser la résolution de conflits interactive  
  
1.  Dans la **Propriétés de l’abonnement - \< abonné>: \< BasededonnéesAbonnement>** boîte de dialogue, spécifiez une valeur de **True** pour la **résoudre les conflits interactivement** option. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Push Subscription Properties](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md) et [View and Modify Pull Subscription Properties](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez spécifier par programme qu'un Abonné utilisera cette interface graphique pour résoudre les conflits dans les articles lorsqu'un abonnement par extraction à une publication de fusion est créé. Seuls les conflits dans les articles qui prennent en charge cette option seront affichés dans le programme de résolution interactif.  
  
#### Pour créer un abonnement de fusion par extraction qui utilise le programme de résolution interactif  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), en spécifiant **@publication**. Notez la valeur de **allow_interactive_resolver** pour chaque article dans le jeu de résultats pour qui le résolveur interactif est utilisé.  
  
    -   Si cette valeur est **1**, le programme de résolution interactif sera utilisé.  
  
    -   Si cette valeur est **0**, vous devez tout d'abord activer le programme de résolution interactif pour chaque article. Pour ce faire, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), en spécifiant **@publication**, **@article**, une valeur de **allow_interactive_resolver** pour **@property**, et la valeur **true** pour **@value**.  
  
2.  Sur la base de données d’abonnement de l’abonné, exécutez [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Pour plus d’informations, consultez [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
3.  Sur la base de données d’abonnement de l’abonné, exécutez [sp_addmergepullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md), spécifiez les paramètres suivants :  
  
    -   **@publisher**, **@publisher_db** (la base de données publiée), et **@publication**.  
  
    -   Valeur **true** pour **@enabled_for_syncmgr**.  
  
    -   Valeur **true** pour **@use_interactive_resolver**.  
  
    -   Les informations de compte de sécurité requises par l'Agent de fusion. Pour plus d’informations, consultez [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
4.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md).  
  
#### Pour définir un article qui prend en charge le programme de résolution interactif  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Spécifiez le nom de la publication à laquelle l’article appartient pour **@publication**, un nom de l’article pour **@article**, l’objet de base de données qui est publiée pour **@source_object**, et la valeur **true** pour **@allow_interactive_resolver**. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
## Voir aussi  
 [Afficher et résoudre les conflits de données pour les Publications de fusion & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/view and resolve data conflicts for merge publications.md)   
 [Résolution interactive des conflits](../../../relational-databases/replication/merge/interactive-conflict-resolution.md)  
  
  