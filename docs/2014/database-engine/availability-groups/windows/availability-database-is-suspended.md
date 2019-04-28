---
title: La base de données de disponibilité est suspendue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21d788db62fe39b86eb801c028450c16cf845845
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815764"
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
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [La base de données de disponibilité est suspendue](https://go.microsoft.com/fwlink/p/?LinkId=220860) sur TechNet Wiki.  
  
## <a name="possible-causes"></a>Causes possibles  
 La synchronisation des données sur cette base de données de disponibilité peut avoir été suspendue pour les motifs suivants :  
  
-   En raison d'une erreur, le système peut avoir suspendu la synchronisation des données.  
  
-   L'administrateur de base de données peut avoir suspendu la synchronisation des données à des fins de maintenance.  
  
## <a name="possible-solution"></a>Solution possible  
 Relancez la synchronisation des données. Si le problème persiste, vérifiez le groupe de disponibilité dans le journal des événements, puis diagnostiquez la raison de la suspension du déplacement des données par le système.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
