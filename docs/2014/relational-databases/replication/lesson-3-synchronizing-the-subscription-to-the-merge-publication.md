---
title: 'Leçon 3 : Synchronisation de l’abonnement et de la publication de fusion | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 63d8f82d207a985bac34b5c9a9be3273bb84ef7d
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000389"
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
 [Synchroniser un abonnement par extraction](synchronize-a-pull-subscription.md)  
  
  
