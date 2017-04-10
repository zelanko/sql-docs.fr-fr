---
title: "D&#233;tection et r&#233;solution avanc&#233;es des conflits de r&#233;plication de fusion | Microsoft Docs"
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
  - "résolution des conflits de réplication de fusion [réplication SQL Server], à propos de la résolution des conflits"
  - "résolveur de conflits par défaut"
  - "suivi des conflits au niveau des colonnes"
  - "suivi des conflits au niveau des lignes"
  - "affichage des conflits de réplication de fusion"
  - "résolution des conflits de réplication de fusion"
  - "suivi des conflits au niveau des enregistrements logiques [réplication SQL Server]"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
ms.assetid: 063d3d9c-ccb5-4fab-9d0c-c675997428b4
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# D&#233;tection et r&#233;solution avanc&#233;es des conflits de r&#233;plication de fusion
  Lorsqu'un serveur de publication et un Abonné sont connectés et que la synchronisation se produit, l'Agent de fusion détecte la présence d'éventuels conflits. Si tel est le cas, l'Agent de fusion utilise un programme de résolution de conflits (spécifié lorsqu'un article est ajouté à une publication) pour déterminer les données qui doivent être acceptées et propagées aux autres sites.  
  
> [!NOTE]  
>  Bien qu'un Abonné se synchronise avec le serveur de publication, des conflits surviennent généralement entre les mises à jour effectuées par différents Abonnés plutôt qu'entre les mises à jour effectuées par l'Abonné et le serveur de publication.  
  
 Le comportement de la détection et de la résolution des conflits est lié aux options suivantes, décrites dans cette rubrique :  
  
-   que vous définissiez le suivi au niveau des colonnes, au niveau des lignes ou au niveau des enregistrements logiques,  
  
-   que vous définissiez le mécanisme de résolution par défaut basé sur les priorités ou un programme de résolution d'articles, un programme de résolution d'articles peut être :  
  
    -   Un *Gestionnaire de logique métier* écrits en code managé.  
  
    -   Com. *résolveur personnalisé*.  
  
    -   Un programme de résolution basé sur COM fourni par [!INCLUDE[msCoName](../../../includes/msconame-md.md)]  
  
     Si le mécanisme de résolution par défaut est utilisé, le comportement est également déterminé par le type d'abonnement utilisé : client ou serveur.  
  
## Détection des conflits  
 Qu'une modification de données soit considérée comme un conflit dépend du type de suivi des conflits défini pour un article :  
  
-   si vous sélectionnez le suivi des conflits au niveau des colonnes, il y a conflit si des modifications sont apportées à la même colonne d'une même ligne sur plusieurs nœuds de réplication ;  
  
-   si vous sélectionnez le suivi au niveau des lignes, il y a conflit si des modifications sont apportées à des colonnes quelconques d'une même ligne sur plusieurs nœuds de réplication (les colonnes affectées dans les lignes correspondantes ne doivent pas être identiques) ;  
  
-   si vous sélectionnez le suivi au niveau des enregistrements logiques, il y a conflit si des modifications sont apportées à des lignes quelconques d'un même enregistrement logique sur plusieurs nœuds de réplication (les colonnes affectées dans les lignes correspondantes ne doivent pas être identiques).  
  
 Pour plus d'informations, voir [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
 Pour spécifier le niveau de suivi et de résolution des conflits pour un article, consultez [Specify the Conflict Tracking and Resolution Level for Merge Articles](../../../relational-databases/replication/publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md).  
  
## Résolution de conflits  
 Après la détection d'un conflit, l'Agent de fusion lance le programme de résolution de conflits sélectionné afin pour déterminer le « vainqueur du conflit ». La ligne gagnante est appliquée au serveur de publication et à l'Abonné tandis que les données de la ligne perdante sont consignées dans une table de conflits. Les conflits sont résolus immédiatement après l'exécution du programme de résolution, à moins que vous ne choisissiez de les résoudre interactivement.  
  
### Types de programmes de résolution  
 Dans la réplication de fusion, la résolution des conflits a lieu au niveau de l'article. Pour les publications composées de plusieurs articles, différents programmes de résolution de conflits peuvent gérer différents articles, sinon un même programme de résolution de conflits peut gérer un article, plusieurs articles, ou tous les articles d'une publication.  
  
 Si vous envisagez d'utiliser le programme de résolution de conflits par défaut sur la base de priorités, vous n'êtes pas obligé de définir la propriété du programme de résolution d'un article. Si vous souhaitez utiliser un programme de résolution d'articles à la place du programme de résolution par défaut, vous devez définir la propriété du programme de résolution pour l'article qui va l'utiliser (en sélectionnant un programme de résolution disponible sur le serveur de publication). Toutes les informations spécifiques qui doivent être transmises au programme de résolution peuvent également être spécifiées dans la propriété du programme de résolution.  
  
 La réplication de fusion propose quatre types de programmes de résolution de conflits :  
  
-   Le programme de résolution des conflits par défaut basé sur les priorités  
  
     Le mécanisme de résolution par défaut se comporte différemment selon qu'un abonnement est de type client ou serveur. Vous attribuez des valeurs de priorités à des Abonnés individuels qui utilisent des abonnements serveur ; les modifications apportées au nœud ayant la priorité la plus élevée gagnent les conflits. Pour les abonnements client, c'est la première modification écrite sur le serveur de publication qui gagne le conflit.  
  
     Il n'est plus possible de modifier le type d'un abonnement une fois celui-ci créé.  
  
-   Un Gestionnaire de logique métier  
  
     L'infrastructure de gestion de logique métier permet d'écrire un assembly de code managé qui est appelé pendant le processus de synchronisation de fusion. Cet assembly inclut une logique de gestion capable de répondre aux conflits et à un certain nombre d'autres conditions pendant la synchronisation. Pour plus d’informations, consultez [exécution logique au cours de fusion synchronisation professionnels](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
-   Un programme de résolution personnalisé basé sur COM  
  
     La réplication de fusion fournit une API pour écrire des programmes de résolution en tant qu’objets COM dans les langues telles que [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]. Pour plus d’informations, consultez [programmes de résolution personnalisé basé sur COM](../../../relational-databases/replication/merge/com-based-custom-resolvers.md).  
  
-   Un programme de résolution basé sur COM fourni par [!INCLUDE[msCoName](../../../includes/msconame-md.md)]  
  
     [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inclut un certain nombre de programmes de résolution COM. Pour plus d’informations, consultez [Microsoft résolveurs COM](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
 Pour plus d’informations sur la façon de sélectionner le type de programme de résolution approprié, consultez [Choisir un résolveur](../../../relational-databases/replication/merge/choose-a-resolver.md).  
  
> [!NOTE]  
>  Certains programmes de résolution d'articles sont écrits pour gérer les conflits de certaines opérations bien précises. Un programme de résolution peut ainsi traiter les mises à jour, mais pas les insertions ni les suppressions. Le programme de résolution de conflits par défaut basé sur les priorités traite tous les conflits non traités par le programme de résolution d'articles.  
  
 Pour spécifier un type d'abonnement de fusion et une priorité pour la résolution des conflits, consultez  
  
-   [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md)  
  
-   Réplication [!INCLUDE[tsql](../../../includes/tsql-md.md)] programmation et la programmation de Replication Management Objects (RMO) : [créer un abonnement extrait](../../../relational-databases/replication/create-a-pull-subscription.md) et [créer un abonnement de Push](../../../relational-databases/replication/create-a-push-subscription.md)  
  
### Programme de résolution interactif  
 La réplication fournit une interface utilisateur du programme de résolution interactif, exploitable en association avec le programme de résolution de conflits par défaut basé sur les priorités ou avec un programme de résolution d'articles. Lors d'une synchronisation à la demande via le Gestionnaire de synchronisation [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, le programme de résolution interactif affiche les données conflictuelles durant l'exécution et vous permet de choisir le moyen de résoudre les conflits. Pour plus d’informations sur la façon d’activer la résolution interactive et lancez le programme de résolution interactif, consultez [résolution de conflit Interactive](../../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
## Affichage des conflits  
 Le moyen le plus direct d'afficher les conflits consiste à utiliser l'Outil de résolution des conflits de réplication, disponible à partir de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournit également les procédures stockées qui permettent l'interrogation des tables conflictuelles). L'Outil de résolution des conflits et le programme de résolution interactif sont des outils similaires, mais le second permet de résoudre des conflits au moment de la synchronisation tandis que le premier affiche les conflits après leur résolution. Si les métadonnées en conflit sont toujours disponibles dans les tables système (les métadonnées en conflit sont conservées par défaut pendant 14 jours), vous pouvez supplanter les résultats de la résolution des conflits dans l'Outil de résolution des conflits ; si, en revanche, une intervention directe est régulièrement demandée, pensez à utiliser le Programme de résolution interactif.  
  
> [!NOTE]  
>  Les conflits qui concernent des enregistrements logiques ne sont pas affichés dans l'Outil de résolution des conflits. Pour afficher des informations sur ces conflits, utilisez des procédures stockées de réplication. Pour plus d’informations, consultez [Afficher les informations de conflit pour les Publications de fusion & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/view conflict information for merge publications.md).  
  
 L'Outil de résolution des conflits affiche des informations issues de trois tables système :  
  
-   La réplication crée une table de conflits pour chaque table dans un article de fusion avec un nom sous la forme **MSmerge_conflict_ \< PublicationName>_ \< ArticleName>**.  
  
     Les tables de conflits possèdent la même structure que les tables sur lesquelles elles sont basées. Une ligne de l'une de ces tables se compose de la version perdante d'une ligne conflictuelle (la version gagnante de la ligne réside dans la table utilisateur réelle).  
  
-   Le **MSmerge_conflicts_info** table fournit des informations sur chaque conflit, y compris le type de conflit.  
  
-   Le **sysmergearticles** tableau identifie les tables utilisateur comportant le conflit de tables et fournit des informations sur les tables de conflits.  
  
 Par défaut, les informations sur les conflits sont stockées dans les emplacements suivants :  
  
-   Sur le serveur de publication et sur l'Abonné, si le niveau de compatibilité est égal ou supérieur à 90RTM.  
  
-   Sur le serveur de publication, si le niveau de compatibilité est inférieur à 80RTM.  
  
-   Sur le serveur de publication si les Abonnées exécutent [!INCLUDE[ssEW](../../../includes/ssew-md.md)]. Impossible de stocker les données de conflit sur [!INCLUDE[ssEW](../../../includes/ssew-md.md)] abonnés.  
  
 **Pour afficher les conflits**  
  
-   [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/view and resolve data conflicts for merge publications.md)  
  
-   Réplication [!INCLUDE[tsql](../../../includes/tsql-md.md)] Programming : [afficher des informations sur les conflits pour les Publications de fusion & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/view conflict information for merge publications.md)  
  
## Voir aussi  
 [Synchronisez les données](../../../relational-databases/replication/synchronize-data.md)  
  
  