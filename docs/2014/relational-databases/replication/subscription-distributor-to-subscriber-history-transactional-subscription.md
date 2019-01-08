---
title: Abonnement, historique du serveur de distribution vers l’abonné (abonnement transactionnel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.disttosub.f1
ms.assetid: 1aad5b82-592e-4907-92f7-b90794175be5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4daea476dd9d533d8a16365a5260905f9fb22d29
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52804301"
---
# <a name="subscription-distributor-to-subscriber-history-transactional-subscription"></a>Abonnement, Historique du serveur de distribution vers l'Abonné (Abonnement transactionnel)
  L'onglet **Historique du serveur de distribution vers l'Abonné** affiche des informations détaillées sur l'Agent de distribution, y compris l'état, l'historique, des messages d'information et d'éventuels messages d'erreur.  
  
## <a name="options"></a>Options  
 Dans le menu **Affichage** , sélectionnez les sessions de l'Agent de distribution à afficher. Sélectionnez ensuite une session particulière dans la grille étiquetée **Sessions de l'Agent de distribution**. Des informations détaillées sur cette session s'affichent dans la grille étiquetée **Actions dans la session sélectionnée**. Si la session sélectionnée s'est terminée sur une erreur, la zone de texte étiquetée **Détails de l'erreur ou message de la session sélectionnée** s'affiche également.  
  
 **Affichage**  
 Sélectionnez les sessions de l'Agent de distribution à afficher. Comme l'agent de distribution s'exécute généralement en continu, il se peut qu'il n'y ait qu'une seule session à afficher.  
  
 **État**  
 État de l'Agent de distribution La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Terminé  
  
-   Nouvel essai  
  
-   Exécution en cours  
  
 **Start Time**  
 Heure d'ouverture de la session.  
  
 **Heure de fin**  
 Heure de fin de la session. Si l'agent ne s'est pas arrêté, ce champ est vide.  
  
 **Duration**  
 Durée d'exécution de l'Agent de distribution dans cette session. Cette durée représente le temps écoulé si l'agent est en cours d'exécution et le temps total de la session si l'agent de la session s'est terminé.  
  
 **Message d'erreur**  
 Si une session s'est terminée sur une erreur, ce champ affiche le dernier message d'erreur enregistré par l'Agent de distribution. Dans le cas contraire, ce champ est vide.  
  
 **Message d'action**  
 Tous les messages d'information ou d'erreur que l'Agent de distribution a enregistrés pendant la session sélectionnée.  
  
 **Heure de l'action**  
 Heure à laquelle l'action décrite dans la colonne **Message d'action** s'est déroulée.  
  
 **Détails de l'erreur ou message de la session sélectionnée**  
 S'affiche uniquement si la session sélectionnée affiche une valeur **Erreur** dans la colonne **État** . La zone de texte affiche des informations d'erreur détaillées, ainsi que la commande émise au moment de l'erreur. Elle comporte également des liens vers des informations supplémentaires à propos de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Afficher des informations et exécuter des tâches pour les agents associés à un abonnement &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [Surveillance de la réplication](monitoring-replication.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)  
  
  
