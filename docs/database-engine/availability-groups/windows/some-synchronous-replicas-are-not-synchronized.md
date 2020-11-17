---
title: Certains réplicas synchrones ne sont pas synchronisés
description: Décrit quelques causes possibles et méthodes de résolution quand un réplica synchrone n’est pas synchronisé avec un groupe de disponibilité Always On.
ms.custom: seo-lt-2019
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: cawrites
ms.author: chadam
ms.openlocfilehash: a8e5fc7b3aa708acc3542082ece0d980c938eb34
ms.sourcegitcommit: 54cd97a33f417432aa26b948b3fc4b71a5e9162b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94583836"
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a>Certains réplicas synchrones ne sont pas synchronisés
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
    
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
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [Certains réplicas synchrones ne sont pas synchronisés](https://go.microsoft.com/fwlink/p/?LinkId=220853) sur Wiki TechNet.  
  
## <a name="possible-causes"></a>Causes possibles  
 Dans ce groupe de disponibilité, au moins un réplica synchrone n'est pas synchronisé actuellement. L'état de synchronisation du réplica peut être SYNCHRONIZING ou NOT SYNCHRONIZING.  
  
## <a name="possible-solution"></a>Solution possible  
 Utilisez l'état de la stratégie de réplica de disponibilité pour rechercher le réplica de disponibilité dont l'état de synchronisation est incorrect, puis résolvez le problème qui affecte le réplica de disponibilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
