---
title: Le réplica de disponibilité est déconnecté | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp2connected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 45c1441441181b5a904f4f2d9370e9c3b9328789
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265319"
---
# <a name="availability-replica-is-disconnected"></a>Le réplica de disponibilité est déconnecté
    
## <a name="introduction"></a>Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|État de la connexion du réplica de disponibilité|  
|**Problème**|Le réplica de disponibilité est déconnecté.|  
|**Catégorie**|**Critique**|  
|**Facette**|Réplica de disponibilité|  
  
## <a name="description"></a>Description  
 Cette stratégie vérifie l'état de la connexion entre les réplicas de disponibilité. La stratégie se trouve dans un état non sain lorsque l'état de la connexion du réplica de disponibilité est DISCONNECTED. Autrement, l'état de la stratégie est sain.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [Le réplica de disponibilité est déconnecté](http://go.microsoft.com/fwlink/p/?LinkId=220857) sur le Wiki TechNet.  
  
## <a name="possible-causes"></a>Causes possibles  
 Le réplica secondaire n'est pas connecté au réplica principal. L'état de la connexion est DISCONNECTED. Ce problème peut avoir les causes suivantes :  
  
-   Le port de connexion est peut-être en conflit avec une autre application.  
  
-   Le type ou l'algorithme de chiffrement est incompatible.  
  
-   Le point de terminaison de connexion a été supprimé ou n'a pas été démarré.  
  
-   Le transport est déconnecté.  
  
## <a name="possible-solutions"></a>Solutions possibles  
 Voici les solutions possibles à ce problème :  
  
-   Vérifiez la configuration du point de terminaison de mise en miroir de bases de données pour les instances du réplica principal et secondaire et mettez à jour la configuration incompatible.  
  
-   Vérifiez si le port est en conflit et, le cas échéant, modifiez le numéro de port.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
