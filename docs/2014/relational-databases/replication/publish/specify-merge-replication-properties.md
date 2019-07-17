---
title: Spécifiez les propriétés de réplication de fusion | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], about merge replication
- merge replication [SQL Server replication]
ms.assetid: ff87c368-4c00-4e48-809d-ea752839551e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 22460851ce3136301beaf5d94e7b0a3b39f8217c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68199295"
---
# <a name="specify-merge-replication-properties"></a>Spécifiez les propriétés de réplication de fusion
Cette rubrique explique comment spécifier différentes propriétés pour votre réplication de fusion. 


## <a name="download-only"></a>Téléchargement seul
  Cette section explique comment spécifier qu’un article de table de fusion est en téléchargement seul dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Les articles en téléchargement uniquement sont conçus pour les applications dont les données ne sont pas mises à jour au niveau des Abonnés. Pour plus d’informations, consultez [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](../merge/optimize-merge-replication-performance-with-download-only-articles.md).  
 
  
###  <a name="limitations-and-restrictions"></a>Limitations et restrictions  
  
-   Si vous spécifiez qu'un article est en téléchargement seul après l'initialisation des abonnements, tous les abonnements client qui ont reçu l'aticle doivent être réinitialisés. Les abonnements serveur n'ont pas besoin d'être réinitialisés. Pour plus d’informations sur les effets des modifications de propriétés, consultez [Changer des propriétés de publication et d’article](change-publication-and-article-properties.md).  
  
### <a name="using-sql-server-management-studio"></a>Utilisation de SQL Server Management Studio  
 Spécifiez qu’un article est en téléchargement seul dans la page **Articles** de l’Assistant Nouvelle publication ou sous l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article - \<Article>** . Cette boîte de dialogue est disponible dans l’Assistant Nouvelle publication et dans la boîte de dialogue **Propriétés de la publication - \<Publication>** . Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication](../publish/create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](../publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-articles-page"></a>Pour spécifier qu'un article est en téléchargement seul dans la page Articles  
  
-   Dans la page **Articles** de l'Assistant Nouvelle publication, sélectionnez une table, puis activez la case à cocher **La table sélectionnée est en téléchargement seul**. 
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-properties-tab-of-the-article-properties---article-dialog-box"></a>Pour spécifier qu’un article est en téléchargement seul sous l’onglet Propriétés de la boîte de dialogue Propriétés de l’article - \<Article>  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>** , sélectionnez une table, puis cliquez sur **Propriétés de l’article**.    
2.  Cliquez sur **Définir les propriétés de l'article de la table en surbrillance** ou **Définir les propriétés de tous les articles de la table**.    
3.  Dans la section **Objet de destination** de l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article - \<Article>** , spécifiez l’une des valeurs suivantes pour **Direction de la synchronisation** :    
    -   **Téléchargement seul pour l'Abonné, interdire les modifications de l'Abonné**    
    -   **Téléchargement seul pour l'Abonné, autoriser les modifications de l'Abonné**  
  
4.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>** , cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.    

###  <a name="using-transact-sql"></a>Utilisation de Transact-SQL  
  
#### <a name="to-specify-that-a-new-merge-table-article-is-download-only"></a>Pour spécifier qu'une nouvelle table de fusion est en téléchargement uniquement    
1.  Exécutez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), en affectant la valeur **1** ou de **2** au paramètre **@subscriber_upload_options** . Ces chiffres correspondent aux comportements suivants :  
  
    -   **0** - aucune restriction (valeur par défaut). Les modifications sur l'abonné sont téléchargées par le serveur de publication.    
    -   **1** -  modifications autorisées au niveau de l'Abonné, mais elles ne sont pas téléchargées sur le serveur de publication.    
    -   **2** - modifications interdites au niveau de l'Abonné.  
  
        > [!NOTE]  
        >  Si la table source d'un article est déjà publiée dans une autre publication, la valeur de **@subscriber_upload_options** doit être la même pour les deux articles.  
  
#### <a name="to-modify-an-existing-merge-table-article-to-be-download-only"></a>Pour modifier un article de table fusion existant en article en téléchargement uniquement  
  
1.  Pour déterminer si un article est en téléchargement uniquement, exécutez [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql). Notez la valeur de **upload_options** pour l'article dans le jeu de résultats.    
2.  Si la valeur retournée à l'étape 1 est **0**, exécutez [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), en affectant la valeur **subscriber_upload_options** à **@property** , la valeur **1** à **@force_invalidate_snapshot** et **@force_reinit_subscription** , et la valeur **1** ou de **2** à **@value** , qui correspondent aux comportements suivants :  
  
    -   **1** -  modifications autorisées au niveau de l'Abonné, mais elles ne sont pas téléchargées sur le serveur de publication.    
    -   **2** - modifications interdites au niveau de l'Abonné.  
  
        > [!NOTE]  
        >  Si la table source d'un article est déjà publiée dans une autre publication, les deux articles doivent être en téléchargement uniquement ou ne pas l'être.  
 
## <a name="interactive-conflict-resolution">Résolution de conflits interactive</a>
La réplication[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] propose un programme de résolution interactif qui vous permet de résoudre manuellement des conflits au cours d'une synchronisation à la demande dans le Gestionnaire de synchronisation [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Quand la résolution de conflits est activée, résolvez les conflits de façon interactive au cours de la synchronisation, à l'aide du résolveur interactif. Le résolveur interactif est disponible via le Gestionnaire de synchronisation [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Pour plus d’informations, consultez [Synchroniser un abonnement à l’aide du Gestionnaire de synchronisation Windows &#40;Windows Synchronization Manager&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
    
###  <a name="Recommendations"></a> Recommandations  
  
-   Si une synchronisation est effectuée en dehors du Gestionnaire de synchronisation Windows (comme une synchronisation planifiée ou à la demande dans SQL Server Management Studio ou le moniteur de réplication), les conflits sont résolus automatiquement sans intervention de l'utilisateur, en utilisant l'outil de résolution des conflits par défaut spécifié pour l'article. Pour plus d’informations, consultez [Interactive Conflict Resolution](../merge/advanced-merge-replication-conflict-interactive-resolution.md).  
  
###  <a name="using-sql-server-management-studio"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="enable-interactive-conflict-resolution-for-an-article"></a>Activer la résolution de conflits interactive pour un article  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>** , sélectionnez une table. Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication](create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](view-and-modify-publication-properties.md).    
2.  Cliquez sur **Propriétés de l'article**, puis cliquez sur **Définir les propriétés de l'article de Table en surbrillance** ou sur **Définir les propriétés de tous les articles de table**.    
3.  Dans la page **Propriétés de l’article - \<Article>** ou **Propriétés de l’article - \<TypeArticle>** , cliquez sur l’onglet **Résolveur**.    
4.  Sélectionnez **Autoriser l'abonné à résoudre les conflits de manière interactive au cours de la synchronisation à la demande**.    
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]    
6.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>** , cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
#### <a name="to-specify-that-a-subscription-should-use-interactive-conflict-resolution"></a>Pour spécifier qu'un abonnement doit utiliser la résolution de conflits interactive  
  
1.  Dans la boîte de dialogue **Propriétés de l’abonnement - \<Abonné> : \<Base_de_données_abonnement>** , affectez la valeur **True** à l’option **Résoudre les conflits interactivement**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Push Subscription Properties](../view-and-modify-push-subscription-properties.md) et [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md). 
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="using-transact-sql"></a>Utilisation de Transact-SQL  
 Vous pouvez spécifier par programme qu'un Abonné utilisera cette interface graphique pour résoudre les conflits dans les articles lorsqu'un abonnement par extraction à une publication de fusion est créé. Seuls les conflits dans les articles qui prennent en charge cette option seront affichés dans le programme de résolution interactif.  
  
#### <a name="create-a-merge-pull-subscription-that-uses-the-interactive-resolver"></a>Créer un abonnement de fusion par extraction qui utilise l’outil de résolution interactif  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), en spécifiant **@publication** . Notez la valeur de **allow_interactive_resolver** pour chaque article du jeu de résultats pour lequel le programme de résolution interactif sera utilisé.    
    -   Si cette valeur est **1**, le programme de résolution interactif sera utilisé.    
    -   Si cette valeur est **0**, vous devez tout d'abord activer le programme de résolution interactif pour chaque article. Pour cela, exécutez [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), en spécifiant **@publication** , **@article** , en affectant la valeur **allow_interactive_resolver** à **@property** la valeur **true** à **@value** .    
2.  Dans la base de données d'abonnement de l'Abonné, exécutez [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql). Pour plus d’informations, consultez [Créer un abonnement par extraction de données (pull)](../create-a-pull-subscription.md).    
3.  Dans la base de données d'abonnement de l'Abonné, exécutez [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql), en spécifiant les paramètres suivants :  
  
    -   **@publisher** , **@publisher_db** (la base de données publiée) et **@publication** .    
    -   La valeur **true** à **@enabled_for_syncmgr** .    
    -   La valeur **true** à **@use_interactive_resolver** .    
    -   Les informations de compte de sécurité requises par l'Agent de fusion. Pour plus d’informations, consultez [Create a Pull Subscription](../create-a-pull-subscription.md).    
4.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql).  
  
#### <a name="define-an-article-that-supports-the-interactive-resolver"></a>Définir un article qui prend en charge l’outil de résolution interactif  
  
Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Spécifiez le nom de la publication à laquelle l'article appartient pour **@publication** , le nom de l'article pour **@article** , l'objet de base de données qui est publié pour **@source_object** la valeur **true** à **@allow_interactive_resolver** . Pour plus d'informations, voir [Define an Article](define-an-article.md).  

## <a name="specify-the-conflict-tracking-and-resolution-level"></a>Spécifier le niveau de résolution et le suivi des conflits 
Lorsqu'un abonnement à une publication de fusion est synchronisé, la réplication vérifie la présence de conflits faisant suite à de la modification des mêmes données au niveau du serveur de publication et de l'Abonné. Vous pouvez spécifier si les conflits sont détectés au niveau de la ligne, auquel cas toute modification apportée à la ligne est considérée comme un conflit, ou au niveau de la colonne, auquel cas seules les modifications apportées aux mêmes ligne et colonne sont considérées comme un conflit. La résolution des conflits pour les articles est réalisée au niveau de la ligne. Pour plus d'informations sur la détection et la résolution des conflits avec des enregistrements logiques, consultez [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).  
  

  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si vous modifiez le niveau de suivi une fois les abonnements initialisés, ces derniers doivent être réinitialisés. Pour plus d’informations sur les effets des modifications de propriétés, consultez [Changer des propriétés de publication et d’article](../publish/change-publication-and-article-properties.md).    
-   Avec le suivi au niveau des lignes et des colonnes, la résolution des conflits est toujours effectuée au niveau des lignes : la ligne gagnante remplace la ligne perdante. La réplication de fusion vous permet également de spécifier que les conflits sont suivis et résolus au niveau des enregistrements logiques, mais ces options ne sont pas disponibles à partir de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Pour plus d'informations sur la définition de ces options à partir des procédures stockées de réplication, consultez [Définir une relation d’enregistrement logique entre des articles de table de fusion](../publish/define-a-logical-record-relationship-between-merge-table-articles.md).  
  
###  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifiez le suivi au niveau des lignes ou des colonnes pour les articles de fusion sous l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article**, disponible dans l’Assistant Nouvelle publication et la boîte de dialogue **Propriétés de la publication - \<Publication>** . Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication](create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](../publish/view-and-modify-publication-properties.md).  
  
#### <a name="specify-row--or-column-level-tracking"></a>Spécifier le suivi au niveau des lignes ou des colonnes  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>** , sélectionnez une table.    
2.  Cliquez sur **Propriétés de l'article**, puis cliquez sur **Définir les propriétés de l'article de Table en surbrillance** ou sur **Définir les propriétés de tous les articles de table**.   
3.  Sous l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article\<Article>** , sélectionnez l’une des valeurs suivantes pour la propriété **Niveau de suivi** : **Suivi au niveau des lignes** ou **Suivi au niveau des colonnes**.    
4.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>** , cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
###  <a name="using-transact-sql"></a>Utilisation de Transact-SQL  
  
#### <a name="specify-conflict-tracking-options-for-a-new-merge-article"></a>Spécifier des options pour un nouvel article de fusion de suivi des conflits  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) et spécifiez l'une des valeurs suivantes pour **@column_tracking** :  
  
    -   **true** - utiliser le suivi au niveau des colonnes pour l'article.    
    -   **false** - utiliser le suivi au niveau des lignes, qui est la valeur par défaut.  
  
#### <a name="change-conflict-tracking-options-for-a-merge-article"></a>Changer les options de suivi des conflits pour un article de fusion  
  
1.  Pour déterminer les options de suivi des conflits pour un article de fusion, exécutez [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql). Notez la valeur de l'option **column_tracking** dans le jeu de résultats de l'article. La valeur **1** indique que le suivi au niveau des colonnes est utilisé, tandis que la valeur **0** indique que le suivi au niveau des lignes est utilisé.    
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Affectez la valeur **column_tracking** à **@property** et l'une des valeurs suivantes à **@value** :
    -   **true** - utiliser le suivi au niveau des colonnes pour l'article.
    -   **false** - utiliser le suivi au niveau des lignes, qui est la valeur par défaut.  
  
     Affectez la valeur **1** à **@force_invalidate_snapshot** et **@force_reinit_subscription** .  

## <a name="tracking-deletes"></a>Le suivi des suppressions

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Par défaut, la réplication de fusion synchronise les commandes DELETE entre le serveur de publication et l'Abonné. La réplication de fusion vous permet de conserver des lignes qui ont été supprimées de la publication dans la base de données d'abonnement, et vice versa. Vous pouvez spécifier par programme que les commandes DELETE doivent être ignorées lors de la création d'un article ou vous pouvez activer cette fonctionnalité ultérieurement à l'aide de procédures stockées de réplication.  
  
> [!IMPORTANT]  
>  L'activation de cette fonctionnalité conduit à une non-convergence ; autrement dit, les données présentes au niveau de l'Abonné ne reflèteront pas correctement les données présentes au niveau du serveur de publication. Vous devez implémenter votre propre mécanisme de manière à supprimer manuellement les lignes supprimées.  
  
### <a name="specify-that-deletes-be-ignored-for-a-new-merge-article"></a>Spécifier que les suppressions doivent être ignorées pour un nouvel article de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Spécifiez la valeur `false` pour **@delete_tracking** . Pour plus d'informations, voir [Define an Article](../publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Si la table source d'un article est déjà publiée dans une autre publication, la valeur de **delete_tracking** doit être la même pour les deux articles.  
  
### <a name="specify-that-deletes-be-ignored-for-an-existing-merge-article"></a>Spécifier que les suppressions doivent être ignorées pour un article de fusion existant  
  
1.  Pour déterminer si la compensation d’erreur est activée pour un article, exécutez [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) et notez la valeur de **delete_tracking** dans le jeu de résultats. Si cette valeur est **0**, les suppressions sont déjà ignorées.    
2.  Si la valeur à l’étape 1 est **1**, exécutez [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) sur la base de données de publication au niveau du serveur de publication. Spécifiez la valeur **delete_tracking** pour **@property** et la valeur `false` pour **@value** .  
  
    > [!NOTE]  
    >  Si la table source d'un article est déjà publiée dans une autre publication, la valeur de **delete_tracking** doit être la même pour les deux articles.  
  
## <a name="processing-order"></a>Ordre de traitement
  La réplication de fusion vous permet de spécifier l'ordre dans lequel les articles sont traités par l'Agent de fusion pendant le processus de synchronisation. Vous pouvez attribuer par programme un ordre à chaque article lors de la création de l'article à l'aide des procédures stockées de réplication. Les articles sont traités à partir de la valeur la plus faible vers la valeur la plus élevée. Si deux articles ont la même valeur, ils sont traités simultanément. Pour plus d’informations, consultez [Spécifier les propriétés de la réplication de fusion](../publish/specify-merge-replication-properties.md).  

  À partir de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], il est possible de remplacer l'ordre de traitement par défaut des articles pour les publications de fusion. Ceci est utile par exemple si vous définissez une intégrité référentielle via des déclencheurs et que ces déclencheurs doivent s'exécuter dans un certain ordre. 

### <a name="how-processing-order-is-determined"></a>Détermination de l'ordre de traitement  
 Lors d'une synchronisation de fusion, les articles sont par défaut traités dans l'ordre requis par les dépendances entre les objets, et notamment les contraintes d'intégrité référentielle déclarative (DRI, Declarative Referential Integrity) définies sur les tables de base de données. Le traitement implique l'énumération des modifications apportées à une table, puis l'application de ces modifications. Si aucune intégrité référentielle déclarative n'est présente mais que des filtres de jointure ou des enregistrements logiques existent entre les articles des tables, les articles sont traités dans l'ordre requis par les filtres et les enregistrements logiques. Les articles non liés à d’autres articles via une intégrité référentielle déclarative, des filtres de jointure, des enregistrements logiques ou d’autres dépendances sont traités en fonction du surnom de l’article dans la table système [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql).  
  
 Supposons une publication qui contient les tables **SalesOrderHeader** et **SalesOrderDetail** avec une colonne clé primaire **SalesOrderID** pour la table **SalesOrderHeader** et une colonne clé étrangère **SalesOrderID** pour la table **SalesOrderDetail** . Lors de la synchronisation, la réplication de fusion empêche les violations de clé étrangère en insérant toutes les nouvelles lignes dans **SalesOrderHeader** avant d'insérer les lignes associées dans **SalesOrderDetail**. De la même façon, les lignes sont supprimées dans **SalesOrderDetail** avant que la ligne associée soit supprimée dans **SalesOrderHeader**.  
  
 Cependant, dans certaines applications, l'intégrité référentielle est appliquée via des déclencheurs de base de données ou bien au niveau de l'application, et non pas via une intégrité référentielle déclarative. Étant donnée la publication décrite plus haut, à la place de l'intégrité référentielle déclarative, la table **SalesOrderDetail** pourrait avoir un déclencheur d'insertion qui vérifie que la ligne associée dans la table **SalesOrderHeader** existe avant d'autoriser une insertion. **SalesOrderHeader** pourrait avoir un déclencheur de suppression qui vérifie qu'il n' y a pas de ligne associée dans la table **SalesOrderDetail** avant d'autoriser une suppression. La réplication de fusion ne prend pas en compte les déclencheurs lors de la détermination de l'ordre de traitement des articles car elle ne peut pas déterminer ce que sera le résultat du déclencheur avant qu'il soit exécuté. De la même façon, la réplication ne peut pas prendre en compte les contraintes définies au niveau de l'application.  
  
 Quand l'intégrité référentielle est gérée via des déclencheurs ou au niveau de l'application, vous devez spécifier l'ordre dans lequel les articles doivent être traités. Dans l'exemple avec les déclencheurs, vous pouvez spécifier que la table **SalesOrderHeader** doit être traitée avant **SalesOrderDetail**, car l'ordre des articles est basé sur l'ordre d'insertion. La réplication de fusion inverse automatiquement l'ordre pour les suppressions. La réplication de fusion n'échoue pas s'il n'y a pas d'ordre pour les articles, car l'Agent de fusion continue à traiter les articles si une violation de contrainte se produit ; il essaye ensuite à nouveau toutes les opérations qui ont échoué, après le traitement des autres articles. La spécification de l'ordre des articles évite simplement les nouveaux essais et le temps de traitement supplémentaire qui y est associé. Si vous spécifiez un ordre incorrect (par exemple un ordre tel que les enregistrements de détail soient traités avant les enregistrements d'en-tête), la réplication de fusion essaye à nouveau le traitement jusqu'à ce qu'il réussisse.  

### <a name="new-article"></a>Nouvel Article
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Spécifiez une valeur entière qui représente l'ordre de traitement de l'article pour **@processing_order** . Pour plus d'informations, voir [Define an Article](define-an-article.md).  
  
    > [!NOTE]  
    >  Lorsque vous créez des articles ordonnés, vous devez laisser des intervalles entre les valeurs d'ordre des articles. Cela permet de définir facilement de nouvelles valeurs dans le futur. Par exemple, si vous avez trois articles pour lesquels vous devez spécifier un ordre de traitement fixe, affectez à **@processing_order** les valeurs 10, 20 et 30 plutôt que 1, 2 et 3, respectivement.  
  
### <a name="existing-article"></a>Article existant
  
1.  Pour déterminer l’ordre de traitement d’un article, exécutez [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) et notez la valeur de **processing_order** dans le jeu de résultats.  
  
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Spécifiez une valeur de **processing_order** pour **@property** et une valeur entière qui représente l'ordre de traitement pour **@value** .  



## <a name="see-also"></a>Voir aussi  
 [Optimiser les performances de la réplication de fusion avec le suivi conditionnel des suppressions](../merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
 [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md)   
 [Définir une relation d’enregistrement logique entre des articles de table de fusion](define-a-logical-record-relationship-between-merge-table-articles.md)   
 [Détecter et résoudre les conflits de réplication de fusion](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](../merge/optimize-merge-replication-performance-with-download-only-articles.md)   
 [Define an Article](define-an-article.md)   
 [Afficher et modifier les propriétés d’un article](view-and-modify-article-properties.md)  