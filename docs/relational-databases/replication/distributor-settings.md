---
description: Paramètres du serveur de distribution
title: Paramètres du serveur de distribution | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.DistributorSettings.f1
helpviewer_keywords:
- Distributor Settings dialog box
ms.assetid: 8276a521-bdd1-4783-bdb6-7ab43499c0ca
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: a85d9f7753ef1ba44d9879ca9d884fc56a5b852d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97483090"
---
# <a name="distributor-settings"></a>Paramètres du serveur de distribution
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
   La boîte de dialogue **Paramètres du serveur de distribution** permet de changer les paramètres des serveurs de distribution ajoutés dans le volet de gauche du Moniteur de réplication.  
  
## <a name="options"></a>Options  
 **Se connecter automatiquement au démarrage du Moniteur de réplication**  
 Sélectionnez cette option pour permettre au Moniteur de réplication de se connecter au serveur de distribution  et d'extraire les informations d'état.  
  
 **Connection**  
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
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
