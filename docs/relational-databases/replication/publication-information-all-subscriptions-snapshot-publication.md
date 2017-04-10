---
title: "Informations de publication, Tous les abonnements (Publication d&#39;instantan&#233;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1"
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Informations de publication, Tous les abonnements (Publication d&#39;instantan&#233;)
  Le **tous les abonnements** onglet affiche des informations sur tous les abonnements à la publication de l’instantané sélectionné.  
  
## Options  
 Pour plus d'informations et en savoir plus sur les tâches associées à un abonnement, cliquez avec le bouton droit de la souris sur la ligne de l'abonnement, puis cliquez sur une option dans le menu contextuel. Pour modifier la façon dont la grille affiche les données, cliquez avec le bouton droit sur la grille, puis cliquez sur l'une des options suivantes :  
  
-   **Trier**: cette option vous permet d'effectuer un tri sur ou plusieurs colonnes dans la boîte de dialogue **Trier les colonnes** .  
  
-   **Choisir les colonnes à afficher**: cette option vous permet de sélectionner les colonnes à afficher et l'ordre d'affichage dans la boîte de dialogue **Choisir les colonnes** .  
  
-   **Filtre**: cette option vous permet de filtrer les lignes dans la grille selon les valeurs de colonne dans la boîte de dialogue **Paramètres du filtre** .  
  
-   **Effacer le filtre**: cette option vous permet d'effacer tous les paramètres du filtre pour la grille.  
  
 Les paramètres du filtre sont spécifiques à chaque grille. La sélection et le tri des colonnes sont appliqués à toutes les grilles du même type, par exemple la grille de publications pour chaque serveur de publication.  
  
 **Afficher**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Sélectionnez les états d'abonnement à afficher pour le type d'abonnement sélectionné. Par exemple, vous pouvez afficher uniquement les abonnements associés à une erreur.  
  
 **État**  
 État de chaque abonnement, déterminé par l'état de l'Agent d'instantané ou l'Agent de distribution (la priorité d'état la plus haute est affichée).  
  
 Par défaut, la grille contenant les informations d’abonnement est triée par la **état** colonne. La liste suivante contient toutes les valeurs d'état possibles et l'ordre de tri des valeurs (par exemple, les erreurs sont toujours affichées dans la partie supérieure de la grille).  
  
-   Erreur  
  
-   Expire bientôt/Expiré ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement)  
  
-   Abonnement non initialisé ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement)  
  
-   Nouvelle tentative de la commande qui a échoué  
  
-   Synchronisation  
  
-   Sans synchronisation  
  
 L'ordre de tri détermine également la valeur affichée lorsqu'un abonnement a plusieurs états. Si, par exemple, un abonnement a une erreur et expire bientôt, la colonne **État** affiche **Erreur**.  
  
 Les valeurs d’état **expire bientôt/expiré** et **abonnement non initialisé** sont des avertissements. Lorsqu'un avertissement est affiché, la colonne **État** s'affiche également si un agent est en cours d'exécution. Par exemple, l’état peut être **en cours d’exécution, expire bientôt/expiré**.  
  
 La valeur d’état **expire bientôt/expiré** s’affiche uniquement si un seuil est défini. Pour plus d’informations sur la définition de seuils, voir [définition des seuils et des avertissements dans le moniteur de réplication](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Le nom de chaque abonnement, sous la forme : *NomAbonné : Nombasedonnéesabonnements*.  
  
 **Dernière synchronisation**  
 Heure de la dernière exécution de l'Agent de distribution. Si la synchronisation est en cours, **Opération en cours** s'affiche.  
  
## Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches pour un abonnement & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  