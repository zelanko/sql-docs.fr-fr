---
title: "Certains réplicas synchrones ne sont pas synchronisés | Microsoft Docs"
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
- sql13.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0bbc03ffe902737ed22380b0d64d4d71ea6d1b4e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="some-synchronous-replicas-are-not-synchronized"></a>Certains réplicas synchrones ne sont pas synchronisés
    
## <a name="introduction"></a>Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|État de synchronisation des données de réplicas synchrones|  
|**Problème**|Certains réplicas synchrones ne sont pas synchronisés.|  
|**Catégorie**|**Avertissement**|  
|**Facette**|Groupe de disponibilité|  
  
## <a name="description"></a>Description  
 Cette stratégie détermine l'état de synchronisation des données de tous les réplicas de disponibilité et recherche les réplicas de disponibilité qui ne sont pas dans l'état de synchronisation escompté. La stratégie se trouve dans un état non sain lorsqu'aucun réplica asynchrone n'est dans un état SYNCHRONIZING et qu'un réplica synchrone n'est dans un état SYNCHRONIZED. Sinon, l'état de la stratégie est sain.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [Certains réplicas synchrones ne sont pas synchronisés](http://go.microsoft.com/fwlink/p/?LinkId=220853) sur Wiki TechNet.  
  
## <a name="possible-causes"></a>Causes possibles  
 Dans ce groupe de disponibilité, au moins un réplica synchrone n'est pas synchronisé actuellement. L'état de synchronisation du réplica peut être SYNCHRONIZING ou NOT SYNCHRONIZING.  
  
## <a name="possible-solution"></a>Solution possible  
 Utilisez l'état de la stratégie de réplica de disponibilité pour rechercher le réplica de disponibilité dont l'état de synchronisation est incorrect, puis résolvez le problème qui affecte le réplica de disponibilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  

