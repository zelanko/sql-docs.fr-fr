---
title: "L’état de synchronisation des données de la base de données de disponibilité n’est pas sain | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords: Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: eacc935d1a470b797e5006738319207c17354c3e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a>L'état de synchronisation des données de la base de données de disponibilité n'est pas sain
    
## <a name="introduction"></a>Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|État de synchronisation des données de la base de données de disponibilité|  
|**Problème**|L'état de synchronisation des données de la base de données de disponibilité n'est pas sain.|  
|**Catégorie**|**Avertissement**|  
|**Facette**|Base de données de disponibilité|  
  
## <a name="description"></a>Description  
 Cette stratégie regroupe l'état de synchronisation des données de toutes les bases de données de disponibilité (également appelées « réplicas de base de données ») dans le réplica de disponibilité. La stratégie se trouve dans un état non sain lorsqu'un réplica de base de données ne se trouve pas dans l'état de synchronisation des données attendu. Autrement, l'état de la stratégie est sain.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], vous trouverez des informations sur les causes et les solutions possibles dans la page [L’état de synchronisation des données d’une base de données de disponibilité n’est pas sain](http://go.microsoft.com/fwlink/p/?LinkId=220858) sur le wiki TechNet.  
  
## <a name="possible-causes"></a>Causes possibles  
 L'état de synchronisation des données de cette base de données de disponibilité n'est pas sain. Sur un réplica de disponibilité en validation asynchrone, chaque base de données de disponibilité doit avoir l'état SYNCHRONIZING. Sur un réplica à validation synchrone, chaque base de données de disponibilité doit être dans l'état SYNCHRONIZED.  
  
## <a name="possible-solution"></a>Solution possible  
 Utilisez la stratégie de réplica de base de données pour rechercher le réplica de base de données affichant un état de synchronisation des données non sain, puis résolvez le problème qui affecte le réplica de base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](~/database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  


