---
title: "Leçon 3 : Synchronisation de l’abonnement et de la publication de fusion | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
caps.latest.revision: "14"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5e0712662eb839270a8932e6059551b45af3f7a2
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Leçon 3 : Synchronisation de l'abonnement et de la publication de fusion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Dans cette leçon, vous allez démarrer l’Agent de fusion pour initialiser l’abonnement à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous allez également utiliser cette procédure pour effectuer la synchronisation avec le serveur de publication. Pour effectuer cette leçon, vous devez avoir terminé la leçon précédente, [Leçon 2 : Création d’un abonnement à la publication de fusion](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Pour démarrer la synchronisation et initialiser l'abonnement  
  
1.  Connectez-vous à l’Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur et le dossier **Réplication** .  
  
2.  Dans le dossier **Abonnements locaux** , cliquez avec le bouton droit sur l’abonnement de la base de données **SalesOrdersReplica** , puis cliquez sur **Afficher l’état de synchronisation**.  
  
3.  Cliquez sur **Démarrer** pour initialiser l’abonnement.  
  
## <a name="next-steps"></a>Next Steps  
Vous avez exécuté avec succès l'Agent de fusion dans le but de démarrer la synchronisation et d'initialiser l'abonnement. Vous pouvez aussi insérer, mettre à jour ou supprimer les données des tables **SalesOrderHeader** ou **SalesOrderDetail** sur le serveur de publication ou l’Abonné, répéter cette procédure quand la connexion réseau est disponible pour synchroniser les données entre le serveur de publication et l’Abonné, puis interroger les tables **SalesOrderHeader** ou **SalesOrderDetail** de l’autre serveur pour visualiser les modifications répliquées.  
  
Ainsi s'achève le didacticiel sur la réplication des données avec les clients mobiles. Pour obtenir un didacticiel similaire utilisant la réplication transactionnelle, consultez [Didacticiel : Réplication de données entre serveurs connectés en permanence](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a> Voir aussi  
[Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Synchronisez les données](../../relational-databases/replication/synchronize-data.md)  
[Synchroniser un abonnement par extraction (pull)](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  
