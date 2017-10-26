---
title: "Certains réplicas de disponibilité ne synchronisent pas de données | Microsoft Docs"
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
- sql13.swb.agdashboard.agp4synchronizing.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 28ef1fac4a5497b94dcc22c0509fb1e923667014
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="some-availability-replicas-are-not-synchronizing-data"></a>Certains réplicas de disponibilité ne synchronisent pas de données
    
## <a name="introduction"></a>Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|État de synchronisation des données des réplicas de disponibilité|  
|**Problème**|Certains réplicas de disponibilité ne synchronisent pas de données.|  
|**Catégorie**|**Avertissement**|  
|**Facette**|Groupe de disponibilité|  
  
## <a name="description"></a>Description  
 Cette stratégie détermine l'état de synchronisation des données de tous les réplicas de disponibilité du groupe de disponibilité et vérifie si la synchronisation d'un réplica de disponibilité n'est pas opérationnelle. La stratégie se trouve dans un état non sain si l'un des états de synchronisation des données du réplica de disponibilité est NOT SYNCHRONIZING.  
  
 Cette stratégie se trouve dans un état sain si aucun des états de synchronisation des données du réplica de disponibilité n'est NOT SYNCHRONIZING.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [Certains réplicas de disponibilité ne synchronisent pas de données](http://go.microsoft.com/fwlink/p/?LinkId=220852) sur TechNet Wiki.  
  
## <a name="possible-causes"></a>Causes possibles  
 Dans ce groupe de disponibilité, au moins un réplica secondaire affiche l'état de synchronisation NOT SYNCHRONIZING et n'accepte pas les données du réplica principal.  
  
## <a name="possible-solution"></a>Solution possible  
 Utilisez l'état de la stratégie du réplica de disponibilité pour rechercher le réplica de disponibilité dont l'état est NOT SYNCHRONIZING, puis résolvez le problème affectant le réplica de disponibilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  

