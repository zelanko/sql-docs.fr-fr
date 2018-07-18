---
title: 'Leçon 3 : Synchronisation de l’abonnement et de la publication de fusion | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 587d8514ede68f731ccacfef8861b95bbcfa1406
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37199019"
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Leçon 3 : Synchronisation de l'abonnement et de la publication de fusion
  Dans cette leçon, vous allez démarrer l'Agent de fusion pour initialiser l'abonnement à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous allez également utiliser cette procédure pour effectuer la synchronisation avec le serveur de publication. Pour effectuer cette leçon, vous devez avoir terminé la leçon précédente, [Leçon 2 : Création d’un abonnement à la publication de fusion](lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Pour démarrer la synchronisation et initialiser l'abonnement  
  
1.  Connectez-vous à l’Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur et le dossier **Réplication** .  
  
2.  Dans le dossier **Abonnements locaux** , cliquez avec le bouton droit sur l’abonnement de la base de données **SalesOrdersReplica** , puis cliquez sur **Afficher l’état de synchronisation**.  
  
3.  Cliquez sur **Démarrer** pour initialiser l’abonnement.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez exécuté avec succès l'Agent de fusion dans le but de démarrer la synchronisation et d'initialiser l'abonnement. Vous pouvez aussi insérer, mettre à jour ou supprimer les données des tables **SalesOrderHeader** ou **SalesOrderDetail** sur le serveur de publication ou l’Abonné, répéter cette procédure quand la connexion réseau est disponible pour synchroniser les données entre le serveur de publication et l’Abonné, puis interroger les tables **SalesOrderHeader** ou **SalesOrderDetail** de l’autre serveur pour visualiser les modifications répliquées.  
  
 Ainsi s'achève le didacticiel sur la réplication des données avec les clients mobiles. Pour obtenir un didacticiel similaire utilisant la réplication transactionnelle, consultez [Didacticiel : Réplication de données entre serveurs connectés en permanence](tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md)   
 [Synchroniser les données](synchronize-data.md)   
 [Synchroniser un abonnement par extraction (pull)](synchronize-a-pull-subscription.md)  
  
  
