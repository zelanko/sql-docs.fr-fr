---
title: SQL Server, objet Latches | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 3cd5db61a2a64f02f0e34b8c2d8fec9dd0c1fa9f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62649588"
---
# <a name="sql-server-latches-object"></a>SQL Server - Objet Latches
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'objet **SQLServer:Latches** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs qui permettent de surveiller les verrous des ressources internes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La surveillance des verrous internes, afin de déterminer l'activité de l'utilisateur et son exploitation des ressources, peut permettre d'identifier les goulots d'étranglement des performances.  
  
 Ce tableau décrit les compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** .  
  
|Compteurs des verrous internes de SQL Server|Description|  
|---------------------------------|-----------------|  
|**Temps d'attente moyen d'un verrou interne (ms)**|Temps d'attente moyen d'un verrou interne (en millisecondes) pour les requêtes en attente.|  
|**Base du temps d’attente moyen d’un verrou interne**|À usage interne uniquement| 
|**Attentes de verrous internes/s**|Nombre de requêtes de verrous internes n'ayant pas pu être accordés immédiatement.|  
|**Nombre de SuperLatch**|Nombre de verrous internes qui sont actuellement des SuperLatch.|  
|**Rétrogradations SuperLatch/sec**|Nombre de SuperLatch ayant été rétrogradés au rang de verrous internes réguliers au cours de la dernière seconde.|  
|**Promotions SuperLatch/s**|Nombre de SuperLatch ayant été promus au rang de SuperLatch au cours de la dernière seconde.|  
|**Temps d'attente total des verrous internes (ms)**|Temps d'attente total (en millisecondes) pour les verrous lors de la dernière seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
