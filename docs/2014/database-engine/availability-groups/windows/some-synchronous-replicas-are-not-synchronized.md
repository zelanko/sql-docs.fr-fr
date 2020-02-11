---
title: Certains réplicas synchrones ne sont pas synchronisés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2423a011e75d346d196ebe5ebac2597ac30914a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62788258"
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
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [Certains réplicas synchrones ne sont pas synchronisés](https://go.microsoft.com/fwlink/p/?LinkId=220853) sur Wiki TechNet.  
  
## <a name="possible-causes"></a>Causes possibles  
 Dans ce groupe de disponibilité, au moins un réplica synchrone n'est pas synchronisé actuellement. L'état de synchronisation du réplica peut être SYNCHRONIZING ou NOT SYNCHRONIZING.  
  
## <a name="possible-solution"></a>Solution possible  
 Utilisez l'état de la stratégie de réplica de disponibilité pour rechercher le réplica de disponibilité dont l'état de synchronisation est incorrect, puis résolvez le problème qui affecte le réplica de disponibilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Utilisez le tableau de bord AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
