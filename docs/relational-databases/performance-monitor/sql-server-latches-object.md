---
title: SQL Server, objet Latches | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cfbce84c62aa100c524a8656d910a6f64428c631
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158657"
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
  
## <a name="see-also"></a> Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
