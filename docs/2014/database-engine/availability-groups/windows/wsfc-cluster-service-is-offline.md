---
title: Le service de cluster WSFC est hors connexion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp1WSFCquorum.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: d502548d-ece6-4a42-9ded-2157d33e3d21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2fd89cf306116a0554366984f864c6f0f6020a20
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126009"
---
# <a name="wsfc-cluster-service-is-offline"></a>Le service de cluster WSFC est hors connexion
    
## <a name="introduction"></a>Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|État du cluster WSFC|  
|**Problème**|Le service de cluster WSFC est hors connexion.|  
|**Catégorie**|**Critique**|  
|**Facette**|Instance de SQL Server|  
  
## <a name="description"></a>Description  
 Cette stratégie vérifie l'état du cluster de basculement Windows Server (WSFC). La stratégie se trouve dans un état non sain et une alerte est déclenchée lorsque le cluster WSFC est hors connexion ou que son état est Quorum forcé. Tous les groupes de disponibilité hébergés dans ce cluster sont hors connexion ou une action de récupération d'urgence est requise.  
  
 L'état de la stratégie est sain lorsque l'état du cluster est Quorum normal.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [Le service de cluster WSFC est hors connexion](http://go.microsoft.com/fwlink/p/?LinkId=220849) sur TechNet Wiki.  
  
## <a name="possible-causes"></a>Causes possibles  
 Ce problème peut être dû à un problème de service de cluster ou à la perte du quorum dans le cluster.  
  
## <a name="possible-solution"></a>Solution possible  
 Utilisez l'outil Administrateur de cluster pour exécuter le quorum forcé ou le flux de travail de récupération d'urgence. Si vous ne pouvez pas résoudre le problème en exécutant le quorum forcé ou la récupération d'urgence, contactez votre administrateur de cluster pour résoudre ce problème. Pour plus d’informations, consultez [Forcer un cluster WSFC à démarrer sans quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
