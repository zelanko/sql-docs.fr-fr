---
title: Avertissements (Informations de publication de fusion)
description: Décrit l’onglet « Avertissements » de la page d’informations sur la publication de réplication de fusion dans SQL Server Management Studio sur SQL Server 2005 et versions ultérieures.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publicationinfo.warningsandagents.merge.f1
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 41e709bcbc533c3cf7ff294dd2b07a6c638a0c52
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "75321333"
---
# <a name="publication-information-warnings-merge-publication-sql-server-2005-and-later"></a>Informations de publication, Avertissements (Publication de fusion, SQL Server 2005 et version ultérieure)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'onglet **Avertissements** est disponible pour les serveurs de distribution qui exécutent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures. L'onglet **Avertissements** vous permet d'effectuer les tâches suivantes selon la publication sélectionnée :  
  
-   activer les avertissements ;  
  
-   définir des seuils associés aux avertissements ;  
  
-   définir des alertes associées aux avertissements ;  
  
## <a name="warnings-thresholds-and-alerts"></a>Avertissements, seuils et alertes  
 Le moniteur de réplication affiche par défaut des avertissements relatifs aux abonnements non initialisés : l’état **Abonnement non initialisé** s’affiche en tant qu’avertissement dans la colonne **État** des pages incluant des informations propres aux abonnements. Dans le cas de publications de fusion, vous pouvez indiquer si les conditions complémentaires suivantes constituent un motif pour lancer un avertissement :  
  
-   Expiration d'abonnement imminente.  
  
     Cet événement correspond à l'option **Avertir si un abonnement expire avant le seuil défini**. Si le seuil précisé est atteint ou dépassé, l'état de l'abonnement se change alors en **Expire bientôt/Expiré** (à moins qu'un problème dont la priorité est supérieure doit être affiché avant l'état de l'abonnement).  
  
-   Dépassement du temps de synchronisation spécifié.  
  
     Ce problème correspond aux options **Avertir si la durée de la fusion pour les connexions d'accès à distance dépasse le seuil** et **Avertir si la durée de la fusion pour les connexions LAN dépasse le seuil**. Ces deux seuils peuvent être définis, mais seulement un des deux n'est utilisé lors d'une synchronisation donnée. L'Agent de fusion applique en effet le seuil approprié selon le type de connexion.  
  
     Si le seuil précisé est atteint ou dépassé, l'état de l'abonnement se change alors en **Fusion longue** (à moins qu'un problème dont la priorité est supérieure doit être affiché avant l'état de l'abonnement).  
  
-   Impossibilité de traiter le nombre de lignes spécifié dans un intervalle de temps donné.  
  
     Cela correspond aux options **Avertir si les lignes fusionnées par seconde pour les connexions d'accès à distance sont inférieures au seuil** et **Avertir si la durée de la fusion pour les connexions LAN dépasse le seuil**. Ces deux seuils peuvent être définis, mais seulement un des deux n'est utilisé lors d'une synchronisation donnée. L'Agent de fusion applique en effet le seuil approprié selon le type de connexion.  
  
     Si le seuil défini est atteint, l'état d'abonnement est affiché sous la forme **Critique pour les performances** (à moins qu'une erreur ayant une priorité plus élevée ne doive être affichée).  
  
 Activer un avertissement entraîne également la définition d'un seuil. Par exemple, si vous activez l'avertissement **Avertir si la durée de la fusion pour les connexions LAN dépasse le seuil**, définissez le temps maximal autorisé à l'opération de synchronisation de fusion.  
  
 L'atteinte d'un seuil déclenche un avertissement dans le Moniteur de réplication, mais également une alerte. Les alertes sont définies en cliquant sur **Configurer des alertes** et en fournissant les informations nécessaires dans la boîte de dialogue **Configurer les alertes de réplication** .  
  
## <a name="options"></a>Options  
 **Activé**  
 Permet d'activer un avertissement et de définir un seuil.  
  
 **Alert**  
 Sélectionnez pour activer le paramètre d'alerte pour un avertissement de réplication donné.  
  
 **Avertissement**  
 Description de l'avertissement associé à un seuil.  
  
 **Seuil**  
 Permet de spécifier une valeur pour le seuil.  
  
 **Configurer des alertes**  
 Sélectionnez une ligne dans la grille **Avertissements** , puis cliquez sur **Configurer des alertes** pour ouvrir la boîte de dialogue **Configurer des alertes de réplication** . Cette boîte de dialogue permet de définir une alerte associée au seuil et à l'avertissement sélectionnés.  
  
 **Ignorer les modifications**  
 Permet d'annuler les modifications apportées aux avertissements et aux seuils.  
  
> [!NOTE]  
>  Cliquer sur **Ignorer les modifications** n'affecte en rien les alertes définies dans la boîte de dialogue **Configurer les alertes de réplication** .  
  
 **Save Changes**  
 Permet d'enregistrer toute modification apportée aux avertissements et aux seuils.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Analyser les performances avec le moniteur de réplication](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Set Thresholds and Warnings in Replication Monitor](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
