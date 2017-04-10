---
title: "Informations de publication, Avertissements (Publication de fusion, SQL Server&#160;2005 et version ult&#233;rieure) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.warningsandagents.merge.f1"
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Informations de publication, Avertissements (Publication de fusion, SQL Server&#160;2005 et version ult&#233;rieure)
  L'onglet **Avertissements** est disponible pour les serveurs de distribution qui exécutent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures. L'onglet **Avertissements** vous permet d'effectuer les tâches suivantes selon la publication sélectionnée :  
  
-   activer les avertissements ;  
  
-   définir des seuils associés aux avertissements ;  
  
-   définir des alertes associées aux avertissements ;  
  
## Avertissements, seuils et alertes  
 Le moniteur de réplication affiche par défaut des avertissements quant aux abonnements non initialisés : l'état **Abonnement non initialisé** s'affiche en tant qu'avertissement dans la colonne **État** des pages incluant des informations propres aux abonnements. Dans le cas de publications de fusion, vous pouvez indiquer si les conditions complémentaires suivantes constituent un motif pour lancer un avertissement :  
  
-   Expiration d'abonnement imminente.  
  
     Cela correspond à l’option **Avertir si un abonnement expire avant le seuil**. Si le seuil spécifié est atteint ou dépassé, l’état de l’abonnement s’affiche en tant que **expire bientôt/expiré** (sauf si un problème avec une priorité plus élevée doit être affichée).  
  
-   Dépassement du temps de synchronisation spécifié.  
  
     Cela correspond aux options **Avertir si la durée de la fusion pour les connexions d’accès à distance dépasse le seuil** et **Avertir si une longueur de fusion pour les connexions LAN dépasse le seuil**. Ces deux seuils peuvent être définis, mais seulement un des deux n'est utilisé lors d'une synchronisation donnée. L'Agent de fusion applique en effet le seuil approprié selon le type de connexion.  
  
     Si le seuil spécifié est atteint ou dépassé, l’état de l’abonnement s’affiche en tant que **Fusion longue** (sauf si un problème avec une priorité plus élevée doit être affichée).  
  
-   Impossibilité de traiter le nombre de lignes spécifié dans un intervalle de temps donné.  
  
     Cela correspond aux options **Avertir si les lignes fusionnées par seconde pour les connexions à distance sont inférieures au seuil** et **Avertir si une longueur de fusion pour les connexions LAN dépasse le seuil**. Ces deux seuils peuvent être définis, mais seulement un des deux n'est utilisé lors d'une synchronisation donnée. L'Agent de fusion applique en effet le seuil approprié selon le type de connexion.  
  
     Si le seuil spécifié est atteint ou dépassé, l’état de l’abonnement s’affiche en tant que **critique pour les performances** (sauf si un problème avec une priorité plus élevée doit être affichée).  
  
 Activer un avertissement entraîne également la définition d'un seuil. Par exemple, si vous activez l’avertissement **Avertir si une longueur de fusion pour les connexions LAN dépasse le seuil**, définissez la longueur maximale autorisée de temps pour une synchronisation de fusion.  
  
 L'atteinte d'un seuil déclenche un avertissement dans le Moniteur de réplication, mais également une alerte. Les alertes sont définies en cliquant sur **Configurer des alertes** et en fournissant les informations nécessaires dans la boîte de dialogue **Configurer les alertes de réplication** .  
  
## Options  
 **Activé**  
 Permet d'activer un avertissement et de définir un seuil.  
  
 **Alerte**  
 Sélectionnez pour activer le paramètre d'alerte pour un avertissement de réplication donné.  
  
 **Avertissement**  
 Description de l'avertissement associé à un seuil.  
  
 **Seuil**  
 Permet de spécifier une valeur pour le seuil.  
  
 **Configurer des alertes**  
 Sélectionnez une ligne dans le **avertissements** grille, puis cliquez sur **configurer les alertes** pour lancer le **configurer des alertes de réplication** boîte de dialogue. Cette boîte de dialogue permet de définir une alerte associée au seuil et à l'avertissement sélectionnés.  
  
 **Ignorer les modifications**  
 Permet d'annuler les modifications apportées aux avertissements et aux seuils.  
  
> [!NOTE]  
>  En cliquant sur **Ignorer les modifications** n’affecte pas les alertes définies dans le **configurer des alertes de réplication** boîte de dialogue.  
  
 **Enregistrer les modifications**  
 Permet d'enregistrer toute modification apportée aux avertissements et aux seuils.  
  
## Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches pour une Publication & #40 ; Moniteur de réplication & #41 ;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Analyser les performances avec le Moniteur de réplication](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Set Thresholds and Warnings in Replication Monitor](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  