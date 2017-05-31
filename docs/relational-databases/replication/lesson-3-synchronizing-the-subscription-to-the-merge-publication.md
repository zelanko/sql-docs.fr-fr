---
title: "Leçon 3 : Synchronisation de l’abonnement et de la publication de fusion | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2f80d0e6e39bea34899501368e7c7dfb693be1c6
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Leçon 3 : Synchronisation de l'abonnement et de la publication de fusion
Dans cette leçon, vous allez démarrer l'Agent de fusion pour initialiser l'abonnement à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous allez également utiliser cette procédure pour effectuer la synchronisation avec le serveur de publication. Pour effectuer cette leçon, vous devez avoir terminé la leçon précédente, [Leçon 2 : Création d’un abonnement à la publication de fusion](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Pour démarrer la synchronisation et initialiser l'abonnement  
  
1.  Connectez-vous à l’Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur et le dossier **Réplication** .  
  
2.  Dans le dossier **Abonnements locaux** , cliquez avec le bouton droit sur l’abonnement de la base de données **SalesOrdersReplica** , puis cliquez sur **Afficher l’état de synchronisation**.  
  
3.  Cliquez sur **Démarrer** pour initialiser l’abonnement.  
  
## <a name="next-steps"></a>Étapes suivantes  
Vous avez exécuté avec succès l'Agent de fusion dans le but de démarrer la synchronisation et d'initialiser l'abonnement. Vous pouvez aussi insérer, mettre à jour ou supprimer les données des tables **SalesOrderHeader** ou **SalesOrderDetail** sur le serveur de publication ou l’Abonné, répéter cette procédure quand la connexion réseau est disponible pour synchroniser les données entre le serveur de publication et l’Abonné, puis interroger les tables **SalesOrderHeader** ou **SalesOrderDetail** de l’autre serveur pour visualiser les modifications répliquées.  
  
Ainsi s'achève le didacticiel sur la réplication des données avec les clients mobiles. Pour obtenir un didacticiel similaire utilisant la réplication transactionnelle, consultez [Didacticiel : Réplication de données entre serveurs connectés en permanence](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a>Voir aussi  
[Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Synchronisez les données](../../relational-databases/replication/synchronize-data.md)  
[Synchroniser un abonnement par extraction (pull)](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  

