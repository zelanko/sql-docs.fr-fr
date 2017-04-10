---
title: "Propri&#233;t&#233;s de la publication, Options d&#39;abonnement | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.subscriptionoptions.f1"
ms.assetid: 31abd605-b273-419d-86df-d0ecf539a507
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Propri&#233;t&#233;s de la publication, Options d&#39;abonnement
  Le **Options d’abonnement** page de le **Propriétés de la Publication** boîte de dialogue permet d’afficher et définir des propriétés de niveau associées aux abonnements de publication. Les propriétés sont regroupées selon les catégories suivantes :  
  
-   Propriétés qui s'appliquent à toutes les publications.  
  
-   Propriétés qui s'appliquent aux publications d'instantané et transactionnelles (y compris celles qui permettent de mettre à jour les abonnements).  
  
-   Propriétés qui s'appliquent aux publications de fusion.  
  
> [!NOTE]  
>  Certaines propriétés sont en lecture seule ; vous trouverez de plus amples explications à cet égard dans les descriptions de propriété de la présente rubrique. Certaines modifications de propriété nécessitent un nouvel instantané pour la publication, et d'autres nécessitent également la réinitialisation de tous les abonnements. Pour plus d’informations, consultez [Publication de modification et les propriétés de l’Article](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
## Options pour toutes les publications  
  
### Création et synchronisation  
 **Autoriser les abonnements anonymes**  
 Détermine s'il est nécessaire d'autoriser les extractions d'abonnements anonymes. Les abonnements anonymes sont pris en charge pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEWEd2005](../../includes/ssewed2005-md.md)], [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssMobileEd2005](../../includes/ssmobileed2005-md.md)], et [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour Windows CE. Pour utiliser cette option pour les publications transactionnelles, l’option d’instantané et **instantané toujours disponible** doit être définie sur **True**.  
  
 **Base de données d'abonnement pouvant être attachée**  
 Détermine si les abonnements peuvent être créés en attachant une copie d’une base de données d’abonnement (nécessite que l’option **instantané toujours disponible** a la valeur **True** pour la capture instantanée et les publications transactionnelles).  
  
> [!IMPORTANT]  
>  Les abonnements attachables ne seront pas disponibles dans une version ultérieure. Cette fonctionnalité est déconseillée.  
  
 **Autoriser les abonnements extraits**  
 Détermine s'il est nécessaire d'autoriser les abonnés à créer des extractions d'abonnements sur cette publication. Pour plus d’informations, consultez la page [s’abonner aux Publications](../../relational-databases/replication/subscribe-to-publications.md).  
  
### Réplication de schéma  
 **Réplique les modifications de schéma**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Détermine s'il est nécessaire de répliquer les modifications de schéma (telles que l'ajout d'une colonne à une table ou la modification du type de données d'une colonne) sur les objets publiés. Pour plus d’informations, consultez [apporter des modifications de schéma sur les bases de données de Publication](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
## Options applicables aux publications d'instantané et transactionnelles  
  
### Création et synchronisation  
 **Agent de distribution indépendant**  
 Détermine s'il est nécessaire d'utiliser un agent indépendant des autres publications de cette base de données. Cette option est en lecture seule ; Il est défini sur **True** par défaut pour les publications créées avec l’Assistant Nouvelle Publication et ne peut pas être modifiées après la création de la publication. Pour plus d’informations, consultez [Administration de l’Agent de réplication](../../relational-databases/replication/agents/replication-agent-administration.md).  
  
 **Instantané toujours disponible**  
 Détermine si les fichiers d’instantanés sont créés chaque fois que l’Agent de capture instantanée s’exécute (nécessite **Agent de Distribution indépendant**). Cette option est en lecture seule ; Il est défini sur **True** Si vous sélectionnez **créer une capture instantanée immédiatement et garder cette dernière disponible pour l’initialisation des abonnements** sur la **Agent de capture instantanée** page de l’Assistant Nouvelle Publication (la valeur par défaut). Pour plus d’informations, consultez [créer et appliquer l’instantané](../../relational-databases/replication/create-and-apply-the-snapshot.md).  
  
 **Autoriser l'initialisation à partir de fichiers de sauvegarde**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Détermine s'il est nécessaire d'autoriser l'utilisation de fichiers de sauvegarde pour initialiser les abonnements. Pour plus d’informations, consultez [initialiser un abonnement transactionnel sans instantané](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 **Autoriser les abonnés non-SQL Server**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Détermine si la publication prend en charge les abonnés non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si cette option **True** définit d’autres propriétés de publication pour prendre en charge non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés. Cette option est en lecture seule si des abonnements existent ; elle ne peut pas être définie sur **True** Si **Autoriser les abonnements de mise à jour immédiate**, **Autoriser les abonnements mis à jour en attente**, ou **autorisent les abonnements d’égal à égal** est définie sur **True**. Pour plus d’informations, consultez la page [les abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
### Transformation des données  
 **Autoriser les transformations de données**  
 Détermine s'il est nécessaire d'utiliser DTS (Data Transformation Services) pour transformer les données avant de les distribuer à un abonné. Cette option est en lecture seule. Vous pouvez uniquement activer les transformations de données si vous créez une publication à l'aide des procédures stockées.  
  
> [!IMPORTANT]  
>  Les abonnements transformables ne seront pas disponibles dans une version ultérieure. Cette fonctionnalité est déconseillée.  
  
### Réplication d'égal à égal  
 **Autoriser les abonnements d'égal à égal**  
 S'applique uniquement à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures. Détermine si la publication prend en charge la réplication d'égal à égal. Si cette option **True** définit d’autres propriétés de publication pour prendre en charge la réplication d’égal à égal. Cette option est en lecture seule si des abonnements existent. Cette option ne peut pas être définie sur **True** Si **Autoriser les abonnements de mise à jour immédiate** ou **Autoriser les abonnements mis à jour en attente**, ou **Autoriser des abonnés non SQL Server** a la valeur **True**. Pour plus d’informations, consultez [égal à la réplication transactionnelle](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 **Autoriser la détection de conflit d'égal à égal**  
 S'applique uniquement à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures. Spécifie si la détection de conflit est activée pour cette publication. Pour utiliser la détection de conflit, tous les nœuds doivent exécuter [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure, et la détection doit être activée pour tous les nœuds. Pour utiliser la détection de conflit, vous devez également spécifier une valeur pour **id d’appelant homologue**. Pour plus d’informations, consultez [la détection de conflit lors de la réplication d’égal à égal](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md).  
  
 **ID d'appelant de l'homologue**  
 S'applique uniquement à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures. Spécifie un ID pour un nœud dans une topologie d'égal à égal. Cet ID est utilisé pour la détection de conflit si **permettre la détection de conflit d’égal à égal** est définie sur **True**. Spécifiez un ID positif différent de zéro qui n'a jamais été utilisé dans la topologie. Pour une liste d’ID qui ont déjà été utilisés, interrogez la [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) (table système).  
  
### Abonnements pouvant être mis à jour  
 **Autoriser les abonnements mis à jour immédiatement**  
 Détermine si les modifications de données de l'abonné peuvent être immédiatement répliquées sur le serveur de publication. Cette option est en lecture seule. Vous pouvez uniquement activer la mise à jour d'abonnement lors de la création d'une publication. Pour plus d’informations, consultez la page [à des abonnements pour la réplication transactionnelle](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 **Autoriser les abonnements mis à jour en attente**  
 Détermine si les modifications de données de l'abonné peuvent être mises en file d'attente et répliquées ultérieurement sur le serveur de publication. Cette option est en lecture seule. Vous pouvez uniquement activer la mise à jour d'abonnement lors de la création d'une publication. Pour plus d’informations, consultez la page [à des abonnements pour la réplication transactionnelle](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 **Signaler les conflits de manière centrale**  
 Détermine s’il faut signaler les modifications de données conflictuelles que sur le serveur de publication ou l’éditeur et l’abonné (nécessite l’option **Autoriser les abonnements mis à jour en attente**). Cette option est en lecture seule ; Il est défini sur **True** par défaut pour les publications créées avec l’Assistant Nouvelle Publication et ne peut pas être modifiées après la création de la publication. Valeur **True** signifie que les conflits sont signalés uniquement sur le serveur de publication. Vous pouvez uniquement voir les conflits lors de leur signalement.  
  
 **Stratégie de résolution de conflit**  
 Spécifie l’action à entreprendre lorsqu’une modification d’abonné entre en conflit avec une modification du serveur de publication (nécessite l’option **Autoriser les abonnements mis à jour en attente**). Pour plus d’informations, consultez [détection de conflit de mise à jour en file d’attente et la résolution](../../relational-databases/replication/transactional/queued-updating-conflict-detection-and-resolution.md).  
  
 **Type de file d'attente**  
 Détermine s’il faut utiliser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file d’attente ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (MSMQ) pour les modifications en attente sur l’abonné jusqu'à ce qu’elles peuvent être appliquées au serveur de publication (nécessite l’option **Autoriser les abonnements mis à jour en attente**). Cette option concerne uniquement [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ; les versions ultérieures utilisent toujours les tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la mise en file d'attente.  
  
## Options des publications de fusion  
  
### Rapport de conflit  
 **Signaler les conflits de manière centrale**  
 Détermine s'il est nécessaire de signaler les conflits de modifications de données uniquement sur le serveur de publication ou à la fois sur le serveur de publication et à l'abonné. Cette option est en lecture seule ; Il est défini sur **True** par défaut pour les publications créées avec l’Assistant Nouvelle Publication et ne peut pas être modifiées après la création de la publication. Valeur **True** signifie que les conflits sont signalés uniquement sur le serveur de publication. Vous pouvez uniquement voir les conflits lors de leur signalement. Pour plus d’informations, consultez la section « Affichage des conflits » de [avancée de détection de conflit la réplication de fusion et résolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
### Filtrage  
 **Autoriser les filtres paramétrés**  
 Dépend du fait qu'une publication utilise ou non des filtres paramétrés. Cette option est toujours en lecture seule. Pour plus d'informations, voir [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Valider les abonnés**  
 Détermine les fonctions à utiliser lors de la confirmation qu'un abonné dispose de la partition de données correcte. Séparez les valeurs multiples par des virgules. Pour plus d’informations, consultez [valider les informations de Partition pour un abonné de fusion](../../relational-databases/replication/validate-partition-information-for-a-merge-subscriber.md).  
  
 **Précalculer les partitions**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Détermine s'il est nécessaire d'optimiser la synchronisation en calculant à l'avance l'appartenance des lignes de données aux partitions. Ce paramètre par défaut est **True** Si la publication satisfait les critères pour les partitions précalculées. Pour plus d’informations, consultez [optimiser les performances de filtre paramétré avec des Partitions précalculées](../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
 **Optimiser la synchronisation**  
 Détermine s'il est nécessaire d'optimiser le traitement de la fusion en stockant des métadonnées supplémentaires pour chaque abonné. Cette optimisation a été remplacée par les partitions précalculées. le **optimiser la synchronisation** option est uniquement pertinente si **Précalculer les partitions** est définie sur **False**. Pour plus d'informations, voir [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
### Processus de fusion  
 **Limiter les processus simultanés**  
 Détermine s'il est nécessaire de limiter le nombre d'Agents de fusion pouvant s'exécuter simultanément. Cette option est généralement utilisée lorsqu'une publication compte un grand nombre d'abonnements par émission de données pouvant être synchronisés en même temps.  
  
 **Nombre maximal de processus simultanés**  
 Le nombre maximal d’Agents de fusion pouvant s’exécuter simultanément (nécessite **limiter les processus simultanés**). Si le nombre d'agents en cours de synchronisation dépasse la limite maximale, ils sont placés en file d'attente jusqu'à ce que leur nombre soit inférieur au maximum.  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  