---
title: Base de données des captures instantanées avec les groupes de disponibilité AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 7432da1c-ce2f-4cd9-af41-54c97744166b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cba02aa87e800391ffba3c791c1ee4341462c3f8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62814655"
---
# <a name="database-snapshots-with-alwayson-availability-groups-sql-server"></a>Instantanés de base de données avec des groupes de disponibilité AlwaysOn (SQL Server)
  Vous pouvez créer un instantané de base de données sur une base de données primaire ou secondaire dans un groupe de disponibilité. Le rôle de réplica doit être PRIMARY ou SECONDARY, et non dans l'état RESOLVING.  
  
 Nous vous recommandons que l'état de synchronisation de base de données soit SYNCHRONIZING ou SYNCHRONIZED lorsque vous créez un instantané de base de données. Toutefois, les instantanés de base de données peuvent être créés lorsque l'état de synchronisation de base de données est NOT SYNCHRONIZING.  
  
 Un instantané de base de données sur un réplica secondaire doit continuer de fonctionner si le réplica est déconnecté (état DISCONNECTED) du réplica principal.  
  
 Certaines conditions [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] provoquent le redémarrage de la base de données source et de ses instantanés de base de données, entraînant la déconnexion temporaire des utilisateurs. Ces conditions sont les suivantes :  
  
-   Le réplica principal modifie des rôles, ce qui peut se produire lorsque le réplica principal actuel est mis hors connexion et qu'il revient en ligne sur la même instance de serveur ou en cas de basculement du groupe de disponibilité.  
  
-   La base de données entre dans le rôle secondaire.  
  
 Si le réplica de disponibilité qui héberge les instantanés de base de données fait l'objet d'un basculement, les instantanés de base de données restent sur l'instance de serveur où ils ont été créés. Les utilisateurs peuvent continuer à utiliser les instantanés après le basculement. Si les performances constituent un problème dans votre environnement, nous vous recommandons de créer des instantanés de base de données uniquement sur les bases de données secondaires qui sont hébergées par un réplica secondaire configuré en mode de basculement manuel.  S'il vous arrive de basculer manuellement le groupe de disponibilité vers ce réplica secondaire, vous pouvez créer un nouvel ensemble d'instantanés de base de données sur un autre réplica secondaire, rediriger les clients vers les nouveaux instantanés de base de données, puis supprimer tous les instantanés de base de données des bases de données désormais primaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Instantanés de base de données &#40;SQL Server&#41;](../../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
