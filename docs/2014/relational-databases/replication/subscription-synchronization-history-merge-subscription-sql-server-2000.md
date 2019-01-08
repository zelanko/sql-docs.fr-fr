---
title: Abonnement, historique de synchronisation (abonnement de fusion, SQL Server 2000) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.downlevelsynchhistory.f1
ms.assetid: 0a0deab2-1c08-4371-9681-d9403e0236cc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 435b24f8f6d7c9255db3c7d72f78ffe474a85c6e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821983"
---
# <a name="subscription-synchronization-history-merge-subscription-sql-server-2000"></a>Abonnement, Historique de synchronisation (Abonnement de fusion, SQL Server 2000)
  L'onglet **Historique de synchronisation** affiche des informations détaillées sur l'Agent de fusion, notamment sur l'état, l'historique, les messages d'informations et n'importe quel message d'erreur.  
  
## <a name="options"></a>Options  
 Sélectionnez les sessions de l’Agent de fusion à afficher dans le menu **Afficher** , puis sélectionnez une session dans la grille **Sessions de l’Agent de fusion**. Des informations détaillées sur cette session s'affichent dans la grille étiquetée **Actions dans la session sélectionnée**. Si la session sélectionnée s'est terminée sur une erreur, la zone de texte étiquetée **Détails de l'erreur ou message de la session sélectionnée** s'affiche également.  
  
 **Affichage**  
 Sélectionnez les sessions de l'Agent de fusion à afficher. L'Agent de fusion s'exécute généralement en continu, ainsi une seule session risque d'être visible.  
  
 **État**  
 Statut de l'Agent de fusion. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Terminé  
  
-   Nouvel essai  
  
-   Exécution en cours  
  
 **Start Time**  
 Heure d'ouverture de la session.  
  
 **Heure de fin**  
 Heure de fin de la session. Si l'agent ne s'est pas arrêté, ce champ est vide.  
  
 **Duration**  
 Durée d'exécution de l'Agent de fusion dans cette session. Cette durée représente le temps écoulé si l'agent est en cours d'exécution et le temps total de la session si l'agent de la session s'est terminé.  
  
 **Message d'erreur**  
 Si la session s'est terminée par une erreur, ce champ contient le dernier message d'erreur consigné par l'Agent de fusion. Dans le cas contraire, ce champ est vide.  
  
 **Message d'action**  
 Tous les messages d'information et d'erreur consignés par l'Agent de fusion lors de la session sélectionnée.  
  
 **Heure de l'action**  
 Heure à laquelle l'action décrite dans la colonne **Message d'action** s'est déroulée.  
  
 **Détails de l'erreur ou message de la session sélectionnée**  
 S'affiche uniquement si la session sélectionnée affiche une valeur **Erreur** dans la colonne **État** . La zone de texte affiche des informations d'erreur détaillées, ainsi que la commande émise au moment de l'erreur. Elle comporte également des liens vers des informations supplémentaires à propos de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Afficher des informations et exécuter des tâches pour les agents associés à un abonnement &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [Surveillance de la réplication](monitoring-replication.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)  
  
  
