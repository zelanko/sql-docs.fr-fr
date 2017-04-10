---
title: "Informations de publication, Avertissements (Publication d&#39;instantan&#233;, SQL Server 2005 et version ult&#233;rieure) | Microsoft Docs"
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
  - "sql13.rep.monitor.publicationinfo.warningsandagents.snapshot.f1"
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Informations de publication, Avertissements (Publication d&#39;instantan&#233;, SQL Server 2005 et version ult&#233;rieure)
  L'onglet **Avertissements** est disponible pour les serveurs de distribution qui exécutent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures. L'onglet **Avertissements** vous permet d'effectuer les tâches suivantes selon la publication sélectionnée :  
  
-   activer les avertissements ;  
  
-   définir des seuils associés aux avertissements ;  
  
-   définir des alertes associées aux avertissements ;  
  
## Avertissements, seuils et alertes  
 Le moniteur de réplication affiche par défaut des avertissements quant aux abonnements non initialisés : l'état **Abonnement non initialisé** s'affiche en tant qu'avertissement dans la colonne **État** des pages incluant des informations propres aux abonnements. Pour les publications de instantanés, vous pouvez également indiquer que l'expiration d'abonnement imminente génère un avertissement en définissant l'option **Avertir si un abonnement expire avant le seuil défini**. Si le seuil spécifié est atteint ou dépassé, l’état de l’abonnement s’affiche en tant que **expire bientôt/expiré** (sauf si un problème avec une priorité plus élevée doit être affichée).  
  
 L'atteinte d'un seuil déclenche un avertissement dans le Moniteur de réplication, mais également une alerte. Les alertes sont définies en cliquant sur **Configurer des alertes** et en fournissant les informations nécessaires dans la boîte de dialogue **Configurer les alertes de réplication** .  
  
## Options  
 **Activé**  
 Permet d'activer un avertissement et de définir un seuil.  
  
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
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  