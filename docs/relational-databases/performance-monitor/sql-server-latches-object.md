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
ms.openlocfilehash: 36cc64688cb78febb3e023e2b11e6e3da204ad1b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "67939528"
---
# <a name="sql-server-latches-object"></a>SQL Server - Objet Latches
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'objet **SQLServer:Latches** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs qui permettent de surveiller les verrous des ressources internes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La surveillance des verrous internes, afin de déterminer l'activité de l'utilisateur et son exploitation des ressources, peut permettre d'identifier les goulots d'étranglement des performances.  
  
 Ce tableau décrit les compteurs **Verrous internes** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs des verrous internes de SQL Server|Description|  
|---------------------------------|-----------------|  
|**Temps d'attente moyen d'un verrou interne (ms)**|Temps d'attente moyen d'un verrou interne (en millisecondes) pour les requêtes en attente.|  
|**Base du temps d’attente moyen d’un verrou interne**|À usage interne uniquement.| 
|**Attentes de verrous internes/s**|Nombre de requêtes de verrous internes n'ayant pas pu être accordés immédiatement.|  
|**Nombre de SuperLatch**|Nombre de verrous internes qui sont actuellement des SuperLatch.|  
|**Rétrogradations SuperLatch/sec**|Nombre de SuperLatch ayant été rétrogradés au rang de verrous internes réguliers au cours de la dernière seconde.|  
|**Promotions SuperLatch/s**|Nombre de SuperLatch ayant été promus au rang de SuperLatch au cours de la dernière seconde.|  
|**Temps d'attente total des verrous internes (ms)**|Temps d'attente total (en millisecondes) pour les verrous lors de la dernière seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
