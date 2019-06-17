---
title: Informations de publication, avertissements (Publication transactionnelle, SQL Server 2005 et versions ultérieur) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.tran.f1
ms.assetid: 4d4baf1d-d0a1-4d09-bec7-137811f43f09
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e2ab1c4be29b87e1051daa702ce40905a95e34ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63022008"
---
# <a name="publication-information-warnings-transactional-publication-sql-server-2005-and-later"></a>Informations de publication, Avertissements (Publication transactionnelle, SQL Server 2005 et version ultérieure)
  L'onglet **Avertissements** est disponible pour les serveurs de distribution qui exécutent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures. L'onglet **Avertissements** vous permet d'effectuer les tâches suivantes selon la publication sélectionnée :  
  
-   activer l'affichage des avertissements dans le Moniteur de réplication ;  
  
-   définir des seuils associés aux avertissements ;  
  
-   définir des alertes associées aux avertissements ;  
  
## <a name="warnings-thresholds-and-alerts"></a>Avertissements, seuils et alertes  
 Le moniteur de réplication affiche par défaut des avertissements relatifs aux abonnements non initialisés : l’état **Abonnement non initialisé** s’affiche en tant qu’avertissement dans la colonne **État** des pages incluant des informations propres aux abonnements. Pour les publications transactionnelles, vous pouvez indiquer si ces conditions additionnelles génèrent des avertissements :  
  
-   Expiration d'abonnement imminente.  
  
     Cet événement correspond à l'option **Avertir si un abonnement expire avant le seuil défini**. Si le seuil précisé est atteint ou dépassé, l'état de l'abonnement se change alors en **Expire bientôt/Expiré** (à moins qu'un problème dont la priorité est supérieure doit être affiché avant l'état de l'abonnement).  
  
-   Dépassement de la latence spécifiée. Délai qui s'écoule entre la validation d'une transaction sur le serveur de publication et la validation de la transaction correspondante au niveau de l'Abonné.  
  
     Ceci correspond à l'option **Avertir si la latence dépasse le seuil**. Si le seuil défini est atteint, l'état d'abonnement est affiché sous la forme **Critique pour les performances** (à moins qu'une erreur ayant une priorité plus élevée ne doive être affichée). Le seuil est également utilisé pour fournir une valeur de performance qui est affichée dans la colonne **Performances** des pages qui contiennent des informations d'abonnement. Les valeurs possibles sont les suivantes :  
  
    -   Excellent  
  
    -   Bonne  
  
    -   Correcte  
  
    -   Médiocre  
  
    -   Critique  
  
 Activer un avertissement entraîne également la définition d'un seuil. Si, par exemple, vous activez l'avertissement **Avertir si la latence dépasse le seuil**, sélectionnez le délai entre la validation de la transaction sur le serveur de publication et la validation de la transaction au niveau de l'Abonné.  
  
 L'atteinte d'un seuil déclenche un avertissement dans le Moniteur de réplication, mais également une alerte. Les alertes sont définies en cliquant sur **Configurer des alertes** et en fournissant les informations nécessaires dans la boîte de dialogue **Configurer les alertes de réplication** .  
  
## <a name="options"></a>Options  
 **Activé**  
 Permet d'activer un avertissement et de définir un seuil.  
  
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
  
 **Enregistrer les modifications**  
 Permet d'enregistrer toute modification apportée aux avertissements et aux seuils.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Analyser les performances avec le moniteur de réplication](monitor/monitor-performance-with-replication-monitor.md)   
 [Surveillance de la réplication](monitoring-replication.md)   
 [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
