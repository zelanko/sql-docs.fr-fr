---
title: Le groupe de disponibilité n’est pas prêt pour le basculement automatique | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp3autofailover.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fcbff0c10d6e58e12474ce3c514a38e74c7119f9
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937130"
---
# <a name="availability-group-is-not-ready-for-automatic-failover"></a>Le groupe de disponibilité n'est pas prêt pour le basculement automatique
    
## <a name="introduction"></a>Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|Disponibilité du groupe de disponibilité pour le basculement automatique|  
|**Problème**|Le groupe de disponibilité n'est pas prêt pour le basculement automatique.|  
|**Catégorie**|**Critical**|  
|**Articulaire**|Groupe de disponibilité|  
  
## <a name="description"></a>Description  
 Cette stratégie vérifie que le groupe de disponibilité a au moins un réplica secondaire prêt pour le basculement. La stratégie se trouve dans un état non sain et une alerte est déclenchée lorsque le mode de basculement du réplica principal est automatique, mais qu'aucun des réplicas secondaires dans le groupe de disponibilité n'est prêt pour le basculement.  
  
 La stratégie se trouve dans un état sain lorsqu'au moins un réplica secondaire est prêt pour le basculement automatique.  
  
> [!NOTE]  
>   Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [Le groupe de disponibilité n'est pas prêt pour le basculement automatique](https://go.microsoft.com/fwlink/p/?LinkId=220851) sur TechNet Wiki.  
  
## <a name="possible-causes"></a>Causes possibles  
 Le groupe de disponibilité n'est pas prêt pour le basculement automatique. Le réplica principal est configuré pour le basculement automatique ; toutefois, le réplica secondaire n'est pas prêt pour le basculement automatique. Le réplica secondaire configuré pour le basculement automatique est peut-être indisponible ou son état de synchronisation des données n'est pas SYNCHRONIZED pour le moment.  
  
## <a name="possible-solutions"></a>Solutions possibles  
 Voici les solutions possibles à ce problème :  
  
-   Vérifiez qu'au moins un réplica secondaire est configuré pour le basculement automatique. Si aucun réplica secondaire n'est configuré pour le basculement automatique, mettez à jour la configuration d'un réplica secondaire de sorte qu'il soit la cible de basculement automatique avec validation synchrone.  
  
-   Utilisez la stratégie pour vérifier que les données sont dans un état de synchronisation et que la cible de basculement automatique est à l'état SYNCHRONIZED, puis pour résoudre le problème qui affecte le réplica de disponibilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
