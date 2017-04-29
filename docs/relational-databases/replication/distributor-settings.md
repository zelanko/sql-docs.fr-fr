---
title: "Paramètres du serveur de distribution | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.monitor.DistributorSettings.f1
helpviewer_keywords:
- Distributor Settings dialog box
ms.assetid: 8276a521-bdd1-4783-bdb6-7ab43499c0ca
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f86500a4461bc2da64c7f3a3d8906bb919b28628
ms.lasthandoff: 04/11/2017

---
# <a name="distributor-settings"></a>Paramètres du serveur de distribution
  La boîte de dialogue **Paramètres du serveur de distribution** permet de changer les paramètres des serveurs de distribution ajoutés dans le volet de gauche du Moniteur de réplication.  
  
## <a name="options"></a>Options  
 **Se connecter automatiquement au démarrage du Moniteur de réplication**  
 Sélectionnez cette option pour permettre au Moniteur de réplication de se connecter au serveur de distribution  et d'extraire les informations d'état.  
  
 **Connexion**  
 Cliquez pour ouvrir la boîte de dialogue **Se connecter au serveur** . Cela vous permet d'afficher et de modifier les propriétés de connexion et les informations d'identification que le Moniteur de réplication utilisent pour se connecter au serveur de distribution.  
  
 **Actualiser automatiquement le statut de ce serveur de distribution et de ses publications**  
 Sélectionnez cette option pour laisser le Moniteur de réplication actualiser automatiquement l'état pour le serveur de distribution. Si cette option est sélectionnée, le Moniteur de réplication interroge le serveur de distribution pour obtenir les informations d'état en fonction de la fréquence d'interrogation définie par l'option **Fréquence d'actualisation** . Pour plus d'informations sur l'actualisation du Moniteur de réplication, consultez [Caching, Refresh, and Replication Monitor Performance](../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Fréquence d'actualisation**  
 Entrez une valeur (en secondes) pour définir la fréquence à laquelle le Moniteur de réplication interroge le serveur de distribution pour obtenir les informations d'état. Des valeurs faibles provoquent des interrogations plus fréquentes. Cela peut affecter les performances du serveur de distribution si vous surveillez plusieurs serveurs de publication. Il est recommandé de tester le système pour déterminer la valeur appropriée. L'option **Fréquence d'actualisation** est également utilisée si vous sélectionnez **Actualisation automatique** dans une fenêtre de détail du Moniteur de réplication.  
  
 **Afficher tous les serveurs de publication de ce serveur de distribution dans le groupe suivant**  
 Sélectionnez un groupe de serveurs de publication dans la liste. Le serveur de publication se trouve dans ce groupe dans le volet de gauche. Les groupes permettent d'organiser les serveurs de publication et n'ont aucun impact sur le fonctionnement de la réplication.  
  
 **Nouveau groupe**  
 Cliquez pour créer un nouveau groupe de serveurs de publication. Un groupe de serveurs de publication permet d'organiser aisément les serveurs de publication dans le Moniteur de réplication. Les groupes n'affectent pas la réplication des données ni la relation entre les serveurs dans une topologie de réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Moniteur de réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
