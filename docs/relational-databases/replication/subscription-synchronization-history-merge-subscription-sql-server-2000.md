---
title: "Abonnement, Historique de synchronisation (Abonnement de fusion, SQL Server&#160;2000) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.subscription.downlevelsynchhistory.f1"
ms.assetid: 0a0deab2-1c08-4371-9681-d9403e0236cc
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Abonnement, Historique de synchronisation (Abonnement de fusion, SQL Server&#160;2000)
  Le **historique de synchronisation** onglet affiche des informations détaillées sur l’Agent de fusion, notamment l’état, l’historique, les messages d’information et des messages d’erreur.  
  
## Options  
 Sélectionnez les sessions de l'Agent de fusion à afficher dans le menu **Afficher** , puis sélectionnez une session dans la grille **Sessions de l'Agent de fusion**. Des informations détaillées sur cette session s'affichent dans la grille étiquetée **Actions dans la session sélectionnée**. Si la session sélectionnée s'est terminée sur une erreur, la zone de texte étiquetée **Détails de l'erreur ou message de la session sélectionnée** s'affiche également.  
  
 **Affichage**  
 Sélectionnez les sessions de l'Agent de fusion à afficher. L'Agent de fusion s'exécute généralement en continu, ainsi une seule session risque d'être visible.  
  
 **État**  
 Statut de l'Agent de fusion. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Erreur  
  
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
 L’heure à laquelle l’action décrite dans le **Message d’Action** de colonne a été effectuée.  
  
 **Détails de l'erreur ou message de la session sélectionnée**  
 Affiche uniquement si la session sélectionnée affiche une valeur **erreur** dans les **état** colonne. La zone de texte affiche des informations d'erreur détaillées, ainsi que la commande émise au moment de l'erreur. Elle comporte également des liens vers des informations supplémentaires à propos de l'erreur.  
  
## Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  