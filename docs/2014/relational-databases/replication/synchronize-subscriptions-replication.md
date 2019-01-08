---
title: Synchroniser des abonnements (réplication) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], subscriptions
- subscriptions [SQL Server replication], synchronizing
- replication [SQL Server], synchronization
ms.assetid: cbe13120-8dd9-4309-88dd-07a801c68f5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d82ef2a50da415504c2a7c461e652beb7547d501
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52772011"
---
# <a name="synchronize-subscriptions-replication"></a>Synchroniser des abonnements (réplication)
  Les abonnements sont synchronisés par les agents de réplication. L'Agent de distribution synchronise les abonnements à des publications transactionnelles et d'instantané, tandis que l'Agent de fusion synchronise les abonnements à des publications de fusion. Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], les procédures stockées de réplication et les Replication Management Objects pour synchroniser des abonnements et contrôler le comportement de synchronisation. Les rubriques répertoriées ci-dessous expliquent comment synchroniser des abonnements et spécifier les options de synchronisation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Créer et appliquer l'instantané initial](create-and-apply-the-initial-snapshot.md)  
  
-   [Créer un instantané d’une publication de fusion avec des filtres paramétrés](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Activer l’initialisation avec une sauvegarde pour les publications transactionnelles &#40;SQL Server Management Studio&#41;](enable-initialization-with-backup-for-transactional-publications.md)  
  
-   [Initialiser un abonnement transactionnel à partir d’une sauvegarde &#40;programmation Transact-SQL de la réplication&#41;](initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [Initialiser manuellement un abonnement](initialize-a-subscription-manually.md)  
  
-   [Synchroniser un abonnement par extraction (pull)](synchronize-a-pull-subscription.md)  
  
-   [Synchroniser un abonnement par émission (push)](synchronize-a-push-subscription.md)  
  
-   [Réinitialiser un abonnement](reinitialize-a-subscription.md)  
  
-   [Exécuter des scripts avant et après l’application d’un instantané &#40;SQL Server Management Studio&#41;](execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [Exécuter des scripts pendant la synchronisation &#40;programmation Transact-SQL de la réplication&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Afficher et résoudre les conflits de données pour les publications de fusion &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [Afficher les conflits de données pour les publications transactionnelles &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
-   [Synchroniser un abonnement à l’aide du Gestionnaire de synchronisation Windows &#40;Gestionnaire de synchronisation Windows&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md)  
  
-   [Implémenter un gestionnaire de logique métier pour un article de fusion](implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Déboguer un gestionnaire de logique métier &#40;programmation de la réplication&#41;](debug-a-business-logic-handler-replication-programming.md)  
  
-   [Contrôler le comportement des déclencheurs et des contraintes pendant la synchronisation &#40;programmation Transact-SQL de la réplication&#41;](control-behavior-of-triggers-and-constraints-in-synchronization.md)  
  
-   [Implémenter un outil personnalisé de résolution des conflits pour un article de fusion](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Synchroniser les données](synchronize-data.md)  
  
  
