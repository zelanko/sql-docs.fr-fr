---
title: Réplication SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], about
- replication [SQL Server]
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: be03754ea8eeb61d838357667da6e37e1be6bc31
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62626148"
---
# <a name="sql-server-replication"></a>Réplication SQL Server
  La réplication repose sur un ensemble de technologies qui permettent de copier et de distribuer des données et des objets de base de données d'une base de données vers une autre, puis de synchroniser ces bases de données afin de préserver leur cohérence. Avec la réplication, vous pouvez distribuer des données en différents emplacements et à des utilisateurs distants ou mobiles sur des réseaux locaux et étendus, des connexions d'accès à distance, des connexions sans fil, et Internet.  
  
 La réplication transactionnelle est généralement utilisée dans des scénarios serveur à serveur qui nécessitent un débit élevé, notamment pour l'amélioration de l'extensibilité et de la disponibilité, l'entrepôt de données et la création de rapports, l'intégration de données depuis plusieurs sites, l'intégration de données hétérogènes et le déchargement du traitement par lots. La réplication de fusion est conçue essentiellement pour les applications mobiles ou les applications de serveur distribuées contenant des conflits de données possibles. Les scénarios courants incluent l'échange de données avec des utilisateurs mobiles, les applications de point de vente aux consommateurs (POS, Consumer Point of Sale) et l'intégration des données à partir de plusieurs sites. La réplication d'instantané est utilisée pour fournir le jeu des données initiales pour la réplication transactionnelle et de fusion ; elle peut s'utiliser également lorsque des actualisations complètes des données sont nécessaires. Avec ces trois types de réplication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit un système souple et puissant de synchronisation des données dans votre entreprise. La réplication dans SQLCE 3.5 et SQLCE 4.0 est prise en charge sur [!INCLUDE[win8srv](../../includes/win8srv-md.md)] et [!INCLUDE[win8](../../includes/win8-md.md)].  
  
 Comme alternative à la réplication,les bases de données peuvent être synchronisées à l'aide de Microsoft Sync Framework. Sync Framework inclut les composants et une API intuitive et flexible qui facilitent la synchronisation entre des bases de données SQL Server, SQL Server Express, SQL Server Compact, et SQL Azure. Sync Framework inclut également les classes qui peuvent être adaptées pour synchroniser une base de données SQL Server et toute autre base de données compatible avec ADO.NET. Pour la documentation détaillée des composants de synchronisation de base de données Sync Framework, consultez [Synchronisation des bases de données](https://go.microsoft.com/fwlink/?LinkId=209079). Pour une vue d'ensemble de Sync Framework, consultez le [Centre de développement Microsoft Sync Framework](https://go.microsoft.com/fwlink/?LinkId=209078). Pour une comparaison entre Sync Framework et la réplication de fusion, consultez [Synchronisation de présentation de bases de données](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)  
  

## <a name="whats-new"></a>Nouveautés 
- SQL Server 2017 ne propose pas de nouvelles fonctionnalités importantes pour la réplication SQL Server. 
- SQL Server 2016 ne propose pas de nouvelles fonctionnalités importantes pour la réplication SQL Server. 

Pour obtenir des informations sur la compatibilité descendante, consultez [Compatibilité descendante de la réplication](replication-backward-compatibility.md). 


 ## <a name="replication-security"></a>Sécurité de la réplication
  
-   [Afficher et modifier les paramètres de sécurité de la réplication](security/view-and-modify-replication-security-settings.md)  
-   [Gérer des connexions dans la liste d'accès à la publication](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="publishing-and-distribution"></a>Publication et distribution  
  
-   [Configurer la publication et la distribution](configure-publishing-and-distribution.md)   
-   [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)   
-   [Désactiver la publication et la distribution](disable-publishing-and-distribution.md)  
  
## <a name="publications-and-articles"></a>Publications et articles 
  
-   [Créer une publication](publish/create-a-publication.md)    
-   [Définir un article](publish/define-an-article.md)   
-   [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)   
-   [Afficher et modifier les propriétés d’un article](publish/view-and-modify-article-properties.md)    
-   [Supprimer une publication](publish/delete-a-publication.md)   
-   [Supprimer un article](publish/delete-an-article.md)    
-   [Créer une publication à partir d’une base de données Oracle](publish/create-a-publication-from-an-oracle-database.md)   
-   [Définir la période d’expiration des abonnements](publish/set-the-expiration-period-for-subscriptions.md)  
-   [Spécifier les options de schéma](publish/specify-schema-options.md)  
-   [Répliquer les modifications de schéma](publish/replicate-schema-changes.md)    
-   [Gérer les colonnes d’identité](publish/manage-identity-columns.md)   
-   [Définir le niveau de compatibilité pour les publications de fusion](publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a>Options d'instantané  
  
-   [Configurer les propriétés d’instantané](publish/configure-snapshot-properties-replication-transact-sql-programming.md)    
-   [Remettre un instantané via FTP](publish/deliver-a-snapshot-through-ftp.md) 
  
### <a name="filter-data"></a>Filtrer les données  
  
-   [Définir et modifier un filtre de colonne](publish/define-and-modify-a-column-filter.md)    
-   [Définir et modifier un filtre de lignes statiques](publish/define-and-modify-a-static-row-filter.md)    
-   [Définir et modifier un filtre de lignes paramétrable pour un article de fusion](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)    
-   [Optimiser les filtres de lignes paramétrables](publish/optimize-parameterized-row-filters.md)    
-   [Définir et modifier un filtre de jointure entre des articles de fusion](publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a>Options de la réplication transactionnelle  
  
-   [Définir la méthode de propagation des modifications de données des articles transactionnels](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)    
-   [Activer les abonnements de mise à jour pour les publications transactionnelles](publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a>Options de la réplication de fusion  
  
-   [Définir une relation d’enregistrement logique entre des articles de table de fusion](publish/define-a-logical-record-relationship-between-merge-table-articles.md)    
-   [Spécifier les propriétés de réplication de fusion](publish/specify-merge-replication-properties.md)    
-   [Spécifier un programme de résolution d’articles de fusion](publish/specify-a-merge-article-resolver.md)    

  
## <a name="manage-subscriptions"></a>Gérer les abonnements  
  
-   [Créer un abonnement par extraction de données (pull)](create-a-pull-subscription.md)    
-   [Afficher et modifier les propriétés d’un abonnement par extraction](view-and-modify-pull-subscription-properties.md)    
-   [Supprimer un abonnement par extraction](delete-a-pull-subscription.md)    
-   [Créer un abonnement par émission de données](create-a-push-subscription.md)   
-   [Afficher et modifier les propriétés d'un abonnement par émission (push)](view-and-modify-push-subscription-properties.md)   
-   [Supprimer un abonnement par émission (push)](delete-a-push-subscription.md)   
-   [Spécifier des planifications de synchronisation](specify-synchronization-schedules.md)    
-   [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](publish/create-an-updatable-subscription-to-a-transactional-publication.md)  
-   [Créer un abonnement pour un Abonné non-SQL Server](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronize-subscriptions"></a>Synchroniser des abonnements  
  
-   [Créer et appliquer l'instantané initial](create-and-apply-the-initial-snapshot.md)   
-   [Créer un instantané d’une publication de fusion avec des filtres paramétrés](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)    
-   [Initialiser un abonnement transactionnel à partir d’une sauvegarde](initialize-a-transactional-subscription-from-a-backup.md)    
-   [Initialiser manuellement un abonnement](initialize-a-subscription-manually.md)    
-   [Synchroniser un abonnement par extraction](synchronize-a-pull-subscription.md)    
-   [Synchroniser un abonnement par émission de données](synchronize-a-push-subscription.md)   
-   [Réinitialiser un abonnement](reinitialize-a-subscription.md)    
-   [Exécuter des scripts pendant la synchronisation](execute-scripts-during-synchronization-replication-transact-sql-programming.md)    
-   [Implémenter un gestionnaire de logique métier pour un article de fusion](implement-a-business-logic-handler-for-a-merge-article.md)  
-   [Déboguer un gestionnaire de logique métier &#40;programmation de la réplication&#41;](debug-a-business-logic-handler-replication-programming.md)    
-   [Contrôler le comportement des déclencheurs et des contraintes pendant la synchronisation](control-behavior-of-triggers-and-constraints-in-synchronization.md)    
-   [Implémenter un outil personnalisé de résolution des conflits pour un article de fusion](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administeration"></a>Administration 
  
-   [Utiliser des profils d’agent de réplication](agents/work-with-replication-agent-profiles.md)   
-   [Valider des données sur l’abonné](validate-data-at-the-subscriber.md)    
-   [Gérer les partitions d'une publication de fusion avec des filtres paramétrables](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)    
-   [Charger en masse des données dans les tables d’une publication de fusion](bulk-load-data-into-tables-in-a-merge-publication.md)    
-   [Nettoyer les métadonnées de fusion](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)    
-   [Effectuer une mise à jour factice pour un article de fusion](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)    
-   [Afficher les commandes répliquées et d’autres informations dans la base de données de distribution](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [Activer les sauvegardes coordonnées pour la réplication transactionnelle](administration/enable-coordinated-backups-for-transactional-replication.md)   
-   [Administrer une topologie d’égal à égal](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)    
-   [Suspendre une topologie de réplication](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)    
-   [Configurer le travail d’un jeu de transactions pour un serveur de publication Oracle](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
-   [Mettre à niveau les scripts de réplication](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitor"></a>Superviser
  
-   [Autoriser des non-administrateurs à utiliser le Moniteur de réplication](monitor/allow-non-administrators-to-use-replication-monitor.md)    
-   [Surveiller la réplication par programmation](monitor/programmatically-monitor-replication.md)    
-   [Afficher les commandes répliquées et d’autres informations dans la base de données de distribution](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [Afficher les informations relatives aux conflits pour les publications de fusion](view-conflict-information-for-merge-publications.md) 
-   [Mesurer la latence et valider les connexions pour la réplication transactionnelle](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  