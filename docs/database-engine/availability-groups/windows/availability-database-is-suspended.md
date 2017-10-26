---
title: "La base de données de disponibilité est suspendue | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3f2040ca390a66809806e7e5123c24272c4470e2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="availability-database-is-suspended"></a>La base de données de disponibilité est suspendue
    
## <a name="introduction"></a>Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|État de suspension de la base de données de disponibilité|  
|**Problème**|La base de données de disponibilité est suspendue.|  
|**Catégorie**|**Avertissement**|  
|**Facette**|Base de données de disponibilité|  
  
## <a name="description"></a>Description  
 Cette stratégie vérifie l'état du déplacement des données de la base de données secondaire (également appelée « réplica de base de données secondaire »). La stratégie se trouve dans un état non sain lorsque le déplacement des données est suspendu. Autrement, l'état de la stratégie est sain.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [La base de données de disponibilité est suspendue](http://go.microsoft.com/fwlink/p/?LinkId=220860) sur TechNet Wiki.  
  
## <a name="possible-causes"></a>Causes possibles  
 La synchronisation des données sur cette base de données de disponibilité peut avoir été suspendue pour les motifs suivants :  
  
-   En raison d'une erreur, le système peut avoir suspendu la synchronisation des données.  
  
-   L'administrateur de base de données peut avoir suspendu la synchronisation des données à des fins de maintenance.  
  
## <a name="possible-solution"></a>Solution possible  
 Relancez la synchronisation des données. Si le problème persiste, vérifiez le groupe de disponibilité dans le journal des événements, puis diagnostiquez la raison de la suspension du déplacement des données par le système.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  

