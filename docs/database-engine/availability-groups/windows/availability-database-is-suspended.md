---
title: Une base de données de disponibilité est suspendue dans un groupe de disponibilité
description: Identifiez les raisons possibles pour lesquelles une base de données de disponibilité est suspendue dans un groupe de disponibilité Always On.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a7a0a6d1fa10576eab5e515031e8233af95c2d76
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67934911"
---
# <a name="availability-database-is-suspended-for-an-availability-group"></a>Une base de données de disponibilité est suspendue dans un groupe de disponibilité
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
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
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [La base de données de disponibilité est suspendue](https://go.microsoft.com/fwlink/p/?LinkId=220860) sur TechNet Wiki.  
  
## <a name="possible-causes"></a>Causes possibles  
 La synchronisation des données sur cette base de données de disponibilité peut avoir été suspendue pour les motifs suivants :  
  
-   En raison d'une erreur, le système peut avoir suspendu la synchronisation des données.  
  
-   L'administrateur de base de données peut avoir suspendu la synchronisation des données à des fins de maintenance.  
  
## <a name="possible-solution"></a>Solution possible  
 Relancez la synchronisation des données. Si le problème persiste, vérifiez le groupe de disponibilité dans le journal des événements, puis diagnostiquez la raison de la suspension du déplacement des données par le système.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
