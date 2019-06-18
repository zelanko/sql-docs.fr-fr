---
title: Abonnement, historique du serveur de publication vers le serveur de distribution (abonnement transactionnel) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.pubtodist.tran.f1
ms.assetid: d5a4c697-1342-49fd-8b7b-b059af32556a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 793420d352b25d969c5cd618861c9b355dea8491
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62752266"
---
# <a name="subscription-publisher-to-distributor-history-transactional-subscription"></a>Abonnement, Historique du serveur de publication vers le serveur de distribution (abonnement transactionnel)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'onglet **Historique du serveur de publication vers le serveur de distribution** affiche des informations détaillées sur l'Agent de lecture du journal, y compris l'état, l'historique, des messages d'information et d'éventuels messages d'erreur.  
  
## <a name="options"></a>Options  
 Dans le menu **Affichage** , sélectionnez les sessions de l'Agent de lecture du journal à afficher. Sélectionnez ensuite une session particulière dans la grille étiquetée **Sessions de l'Agent de lecture du journal**. Des informations détaillées sur cette session s'affichent dans la grille étiquetée **Actions dans la session sélectionnée**. Si la session sélectionnée s'est terminée sur une erreur, la zone de texte étiquetée **Détails de l'erreur ou message de la session sélectionnée** s'affiche également.  
  
 **Afficher**  
 Sélectionnez les sessions de l'Agent de lecture du journal à afficher. L'Agent de lecture du journal s'exécute généralement en permanence : il se peut donc qu'il n'y ait qu'une session à afficher.  
  
 **État**  
 État de l'Agent de lecture du journal. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Terminé  
  
-   Nouvel essai  
  
-   Exécution en cours  
  
 **Start Time**  
 Heure d'ouverture de la session.  
  
 **Heure de fin**  
 Heure de fin de la session. Si l'agent ne s'est pas arrêté, ce champ est vide.  
  
 **Duration**  
 Durée d'exécution de l'Agent de lecture du journal dans cette session. Cette durée représente le temps écoulé si l'agent est en cours d'exécution et le temps total de la session si l'agent de la session s'est terminé.  
  
 **Message d'erreur**  
 Si une session s'est terminée sur une erreur, ce champ affiche le dernier message d'erreur enregistré par l'Agent de lecture du journal. Dans le cas contraire, ce champ est vide.  
  
 **Message d'action**  
 Tous les messages d'information ou d'erreur que l'Agent de lecture du journal a enregistrés pendant la session sélectionnée.  
  
 **Heure de l'action**  
 Heure à laquelle l'action décrite dans la colonne **Message d'action** s'est déroulée.  
  
 **Détails de l'erreur ou message de la session sélectionnée**  
 S'affiche uniquement si la session sélectionnée affiche une valeur **Erreur** dans la colonne **État** . La zone de texte affiche des informations d'erreur détaillées, ainsi que la commande émise au moment de l'erreur. Elle comporte également des liens vers des informations supplémentaires à propos de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
