---
title: SQL Server, réplica de disponibilité | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- performance counters [SQL Server], AlwaysOn Availability Groups
- SQLServer:Availability Replica
- Availability Groups [SQL Server], performance counters
ms.assetid: e402f996-c1fb-484a-b804-45c49972f2e0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6269474edbde55f1ebf506bfbd5599f5c3287bc9
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52748811"
---
# <a name="sql-server-availability-replica"></a>SQL Server, réplica de disponibilité
  L’objet de performance **SQLServer:Availability Replica** contient des compteurs de performances qui recueillent des informations sur les réplicas de disponibilité des groupes de disponibilité AlwaysOn dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Tous les compteurs de performance du réplica de disponibilité s'appliquent au réplica principal et aux réplicas secondaires, et les compteurs d'envoi/réception reflètent le réplica local. Généralement, le réplica principal envoie la plupart des données, et les réplicas secondaires les reçoivent. Toutefois, les réplicas secondaires envoient des accusés de réception et d'autres informations d'arrière-plan sur le trafic aux réplicas principaux. Notez que sur un réplica de disponibilité donné, certains compteurs affichent la valeur zéro, suivant le rôle actuel, principal ou secondaire, du réplica local.  
  
|Nom du compteur|Description|  
|------------------|-----------------|  
|**Octets reçus du réplica par seconde**|Nombre d'octets reçus du réplica de disponibilité par seconde. Les mises à jour d'état et requête ping génèrent un trafic sur le réseau, même sur des bases de données sur lesquelles n'a lieu aucune mise à jour utilisateur.|  
|**Octets envoyés au réplica par seconde**|Nombre d'octets envoyés au réplica de disponibilité distant par seconde. Sur le réplica primaire, il s'agit du nombre d'octets envoyés au réplica secondaire. Sur le réplica secondaire, il s'agit du nombre d'octets envoyés au réplica primaire.|  
|**Octets envoyés au transport par seconde**|Nombre réel d'octets envoyés par seconde sur le réseau au réplica de disponibilité distant. Sur le réplica primaire, il s'agit du nombre d'octets envoyés au réplica secondaire. Sur le réplica secondaire, il s'agit du nombre d'octets envoyés au réplica primaire.|  
|**Temps de contrôle du flux (ms/s)**|Temps en millisecondes passé par les messages de flux du journal en attente de contrôle du flux d'envoi au cours de la dernière seconde.|  
|**Contrôle de flux par seconde**|Nombre de fois où le contrôle de flux a démarré au cours de la dernière seconde. **Temps de contrôle de flux (ms/s)** divisé par **Contrôle de flux/s** correspond à la durée moyenne par attente.|  
|**Réceptions du réplica par seconde**|Nombre de messages AlwaysOn reçus du réplica par seconde.|  
|**Messages renvoyés par seconde**|Nombre de messages AlwaysOn renvoyés au cours de la dernière seconde.|  
|**Envois au réplica par seconde**|Nombre de messages AlwaysOn envoyés à ce réplica de disponibilité par seconde.|  
|**Envois au transport par seconde**|Nombre réel de messages AlwaysOn envoyés par seconde sur le réseau au réplica de disponibilité distant. Sur le réplica primaire, il s'agit du nombre de messages envoyés au réplica secondaire. Sur le réplica secondaire, il s'agit du nombre de messages envoyés au réplica primaire.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, réplica de base de données](sql-server-database-replica.md)   
 [Groupes de disponibilité AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
