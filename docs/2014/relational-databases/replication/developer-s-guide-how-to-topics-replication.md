---
title: 'Guide du développeur : rubriques de guide pratique (réplication) | Microsoft Docs'
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- replication
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c6c15ae6-da52-4638-93d3-61c7242e8a0b
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1329e7b4da266ea6024ed8bbc760b5eed636a30a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141795"
---
# <a name="developer39s-guide-how-to-topics-replication"></a>Guide du développeur : rubriques de guide pratique (réplication)
  Cette rubrique contient des liens vers des informations indiquant comment effectuer par programmation des tâches liées à la réplication.  
  
## <a name="securing-a-replication-topology"></a>Sécurisation d'une topologie de réplication  
  
-   [Afficher et modifier les paramètres de sécurité de la réplication](security/view-and-modify-replication-security-settings.md)  
  
-   [Gérer des connexions dans la liste d’accès à la publication](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="configuring-modifying-and-disabling-publishing-and-distribution-replication"></a>Configuration, modification et désactivation de la publication et de la distribution (réplication)  
  
-   [Configurer la publication et la distribution](configure-publishing-and-distribution.md)  
  
-   [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)  
  
-   [Désactiver la publication et la distribution](disable-publishing-and-distribution.md)  
  
## <a name="creating-modifying-and-deleting-publications-and-articles"></a>Création, modification et suppression de publications et d'articles  
  
-   [Create a Publication](publish/create-a-publication.md)  
  
-   [Define an Article](publish/define-an-article.md)  
  
-   [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)  
  
-   [Afficher et modifier les propriétés d’un article](publish/view-and-modify-article-properties.md)  
  
-   [Supprimer une publication](publish/delete-a-publication.md)  
  
-   [Supprimer un article](publish/delete-an-article.md)  
  
-   [Créer une publication à partir d’une base de données Oracle](publish/create-a-publication-from-an-oracle-database.md)  
  
-   [Définir la période d’expiration des abonnements](publish/set-the-expiration-period-for-subscriptions.md)  
  
-   [Spécifier des options de schéma](publish/specify-schema-options.md)  
  
-   [Répliquer les modifications de schéma](publish/replicate-schema-changes.md)  
  
-   [Gérer des colonnes d’identité](publish/manage-identity-columns.md)  
  
-   [Définir le niveau de compatibilité pour les publications de fusion](publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a>Options d'instantané  
  
-   [Configurer les propriétés d’instantané &#40;programmation Transact-SQL de la réplication&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [Remettre un instantané via FTP](publish/deliver-a-snapshot-through-ftp.md)  
  
### <a name="filtering-data"></a>Filtrage des données  
  
-   [Définir et modifier un filtre de colonne](publish/define-and-modify-a-column-filter.md)  
  
-   [Définir et modifier un filtre de lignes statiques](publish/define-and-modify-a-static-row-filter.md)  
  
-   [Définir et modifier un filtre de lignes paramétrable pour un article de fusion](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [Optimiser les filtres de lignes paramétrables](merge/parameterized-filters-parameterized-row-filters.md)  
  
-   [Définir et modifier un filtre de jointure entre des articles de fusion](publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a>Options de la réplication transactionnelle  
  
-   [Définir la méthode de propagation des modifications de données des articles transactionnels](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)  
  
-   [Activer les abonnements de mise à jour pour les publications transactionnelles](publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a>Options de la réplication de fusion  
  
-   [Définir une relation d’enregistrement logique entre des articles de table de fusion](publish/define-a-logical-record-relationship-between-merge-table-articles.md)  
  
-   [Spécifier l’ordre de traitement d’articles de table de fusion &#40;programmation Transact-SQL de la réplication&#41;](publish/specify-the-processing-order-of-merge-table-articles.md)  
  
-   [Spécifier qu’un article de table de fusion est en téléchargement seul](publish/specify-that-a-merge-table-article-is-download-only.md)  
  
-   [Indiquer que les suppressions ne doivent pas être suivies pour les articles de fusion &#40;programmation Transact-SQL de la réplication&#41;](publish/specify-that-deletes-should-not-be-tracked-for-merge-articles.md)  
  
-   [Spécifier le niveau de suivi et de résolution des conflits pour des articles de fusion](publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md)  
  
-   [Spécifier un programme de résolution d’articles de fusion](publish/specify-a-merge-article-resolver.md)  
  
-   [Spécifier la résolution interactive des conflits pour les articles de fusion](publish/specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="creating-modifying-and-deleting-subscriptions"></a>Création, modification et suppression d'abonnements  
  
-   [Créer un abonnement par extraction](create-a-pull-subscription.md)  
  
-   [Afficher et modifier les propriétés d’un abonnement par extraction](view-and-modify-pull-subscription-properties.md)  
  
-   [Supprimer un abonnement par extraction (pull)](delete-a-pull-subscription.md)  
  
-   [Créer un abonnement par émission de données](create-a-push-subscription.md)  
  
-   [Afficher et modifier les propriétés d’un abonnement par émission de données](view-and-modify-push-subscription-properties.md)  
  
-   [Supprimer un abonnement par émission de données](delete-a-push-subscription.md)  
  
-   [Spécifier des planifications de synchronisation](specify-synchronization-schedules.md)  
  
-   [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](create-updatable-subscription-transactional-publication-transact-sql.md)  
  
-   [Créer un abonnement pour un abonné non-SQL Server](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronizing-subscriptions"></a>Synchronisation d'abonnements  
  
-   [Créer et appliquer l'instantané initial](create-and-apply-the-initial-snapshot.md)  
  
-   [Créer un instantané d’une publication de fusion avec des filtres paramétrés](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Initialiser un abonnement transactionnel à partir d’une sauvegarde &#40;programmation Transact-SQL de la réplication&#41;](initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [Initialiser manuellement un abonnement](initialize-a-subscription-manually.md)  
  
-   [Synchroniser un abonnement par extraction (pull)](synchronize-a-pull-subscription.md)  
  
-   [Synchroniser un abonnement par émission (push)](synchronize-a-push-subscription.md)  
  
-   [Réinitialiser un abonnement](reinitialize-a-subscription.md)  
  
-   [Exécuter des scripts pendant la synchronisation &#40;programmation Transact-SQL de la réplication&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Implémenter un gestionnaire de logique métier pour un article de fusion](implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Déboguer un gestionnaire de logique métier &#40;programmation de la réplication&#41;](debug-a-business-logic-handler-replication-programming.md)  
  
-   [Contrôler le comportement des déclencheurs et des contraintes pendant la synchronisation &#40;programmation Transact-SQL de la réplication&#41;](control-behavior-of-triggers-and-constraints-in-synchronization.md)  
  
-   [Implémenter un outil personnalisé de résolution des conflits pour un article de fusion](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administering-a-replication-topology"></a>Administration d'une topologie de réplication  
  
-   [Utiliser des profils d’agent de réplication](agents/replication-agent-profiles.md)  
  
-   [Valider des données sur l’abonné](validate-data-at-the-subscriber.md)  
  
-   [Gérer les partitions d’une publication de fusion avec des filtres paramétrables](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Charger en masse des données dans les tables d’une publication de fusion &#40;programmation Transact-SQL de la réplication&#41;](bulk-load-data-into-tables-in-a-merge-publication.md)  
  
-   [Nettoyer les métadonnées de fusion &#40;programmation Transact-SQL de la réplication&#41;](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)  
  
-   [Exécuter une mise à jour factice pour un article de fusion &#40;programmation Transact-SQL de la réplication&#41;](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)  
  
-   [Afficher les commandes répliquées et autres informations dans la base de données de distribution &#40;programmation Transact-SQL de la réplication&#41;](monitor/view-replicated-commands-and-information-in-distribution-database.md)  
  
-   [Activer les sauvegardes coordonnées pour la réplication transactionnelle &#40;programmation Transact-SQL de la réplication&#41;](administration/enable-coordinated-backups-for-transactional-replication.md)  
  
-   [Administrer une topologie d’égal à égal &#40;programmation Transact-SQL de la réplication&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)  
  
-   [Suspendre une topologie de réplication &#40;programmation Transact-SQL de la réplication&#41;](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)  
  
-   [Configurer le travail d’un jeu de transactions pour un serveur de publication Oracle &#40;programmation Transact-SQL de la réplication&#41;](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)  
  
-   [Mettre à niveau les scripts de réplication &#40;programmation Transact-SQL de la réplication&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitoring-a-replication-topology"></a>Analyse d'une topologie de réplication  
  
-   [Autoriser des non-administrateurs à utiliser le moniteur de réplication](monitor/allow-non-administrators-to-use-replication-monitor.md)  
  
-   [Surveiller la réplication par programmation](monitor/monitoring-replication-overview.md)  
  
-   [Afficher les commandes répliquées et autres informations dans la base de données de distribution &#40;programmation Transact-SQL de la réplication&#41;](monitor/view-replicated-commands-and-information-in-distribution-database.md)  
  
-   [Afficher les informations relatives aux conflits pour les publications de fusion &#40;programmation Transact-SQL de la réplication&#41;](view-conflict-information-for-merge-publications.md)  
  
-   [Mesurer la latence et valider les connexions pour la réplication transactionnelle](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  