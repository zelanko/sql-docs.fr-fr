---
title: Certains réplicas de disponibilité sont déconnectés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8ebc6b8e8d06418c289726fd3ff2a1e56830f464
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155939"
---
# <a name="some-availability-replicas-are-disconnected"></a>Certains réplicas de disponibilité sont déconnectés
    
## <a name="introduction"></a>Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|État de la connexion des réplicas de disponibilité|  
|**Problème**|Certains réplicas de disponibilité sont déconnectés.|  
|**Catégorie**|**Avertissement**|  
|**Facette**|Groupe de disponibilité|  
  
## <a name="description"></a>Description  
 Cette stratégie détermine l'état de la connexion de tous les réplicas de disponibilité et recherche les réplicas de disponibilité dont l'état est DISCONNECTED. La stratégie se trouve dans un état non sain lorsque l'état d'un réplica de disponibilité est DISCONNECTED. Autrement, l'état de la stratégie est sain.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [Certains réplicas de disponibilité sont déconnectés](http://go.microsoft.com/fwlink/p/?LinkId=220855) sur TechNet Wiki.  
  
## <a name="possible-causes"></a>Causes possibles  
 Dans ce groupe de disponibilité, au moins un réplica secondaire n'est pas connecté au réplica principal. L'état de la connexion est DISCONNECTED.  
  
## <a name="possible-solution"></a>Solution possible  
 Utilisez l'état de la stratégie de réplica de disponibilité pour rechercher le réplica de disponibilité dont l'état est DISCONNECTED, puis résolvez le problème qui affecte le réplica de disponibilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
