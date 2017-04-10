---
title: "Agent d&#39;instantan&#233; | Microsoft Docs"
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
  - "sql13.rep.monitor.snapshotagent.f1"
helpviewer_keywords: 
  - "boîte de dialogue Agent d'instantané"
ms.assetid: b715e621-2cd5-4a15-8f58-a341aa8ef5e4
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Agent d&#39;instantan&#233;
  La boîte de dialogue **Agent d'instantané** affiche des informations détaillées concernant l'Agent d'instantané, notamment son état, son historique, des messages d'information ainsi que tout message d'erreur s'y rapportant.  
  
## Options  
 Sélectionnez les sessions de l'Agent d'instantané à afficher à partir du menu **Affichage** , puis sélectionnez une session particulière dans la grille **Sessions de l'Agent d'instantané**. Des informations détaillées sur cette session s'affichent dans la grille étiquetée **Actions dans la session sélectionnée**. Si la session sélectionnée s'est terminée sur une erreur, la zone de texte étiquetée **Détails de l'erreur ou message de la session sélectionnée** s'affiche également.  
  
 **Affichage**  
 Permet de sélectionner les sessions de l'Agent d'instantané à afficher.  
  
 **État**  
 État de l'Agent d'instantané. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Erreur  
  
-   Nouvelle tentative de la commande qui a échoué  
  
-   Non exécuté  
  
-   Terminé  
  
 **Start Time**  
 Heure d'ouverture de la session.  
  
 **Heure de fin**  
 Heure de fin de la session. Si l'agent ne s'est pas arrêté, ce champ est vide.  
  
 **Duration**  
 Durée pendant laquelle l'Agent d'instantané s'est exécuté lors de la session en cours. Cette durée représente le temps écoulé si l'agent est en cours d'exécution et le temps total de la session si l'agent de la session s'est terminé.  
  
 **Message d'erreur**  
 Si une session s'est terminée sur une erreur, ce champ affiche alors le dernier message d'erreur consigné dans le journal par l'Agent d'instantané. Dans le cas contraire, ce champ est vide.  
  
 **Message d'action**  
 Correspond à tous les messages d'information et d'erreur que l'Agent d'instantané a consignés dans le journal lors de la session sélectionnée.  
  
 **Heure de l'action**  
 L’heure à laquelle l’action décrite dans le **Message d’Action** de colonne a été effectuée.  
  
 **Détails de l'erreur ou message de la session sélectionnée**  
 S’affiche uniquement si la session sélectionnée affiche une valeur **erreur** dans les **état** colonne. La zone de texte affiche des informations d'erreur détaillées, ainsi que la commande émise au moment de l'erreur. Elle comporte également des liens vers des informations supplémentaires à propos de l'erreur.  
  
## Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  