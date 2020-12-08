---
title: SQL Server, Broker Activation (objet) | Microsoft Docs
description: Découvrez l’objet de performance SQLServer:BrokerActivation, qui contient des compteurs de performances fournissant des informations sur l’activation des procédures stockées.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 8c257bee159905042ddece42102ef0a55a3512f1
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505857"
---
# <a name="sql-server-broker-activation-object"></a>SQL Server: Broker Activation (objet)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  L'objet de performance **SQLServer:BrokerActivation** contient des compteurs de performances qui fournissent des informations sur l'activation des procédures stockées. Le tableau ci-dessous répertorie les compteurs inclus dans cet objet.  
  
|Compteurs de SQL Server Broker Activation|Description|  
|-------------------------------------------|-----------------|  
|**Appels de procédures stockées/s**|Ce compteur indique le nombre total de procédures stockées d'activation appelées par seconde par tous les moniteurs de file d'attente de l'instance.|  
|**Limite de tâches atteinte**|Ce compteur indique le nombre total de fois qu'un démarrage d'une nouvelle tâche par un moniteur de file d'attente a avorté du fait que le nombre maximal de tâches pour cette file est déjà en cours d'exécution.|  
|**Limite de tâches atteinte/s**|Ce compteur indique le nombre de fois par seconde qu'un démarrage d'une nouvelle tâche par un moniteur de file d'attente a avorté du fait que le nombre maximal de tâches pour cette file est déjà en cours d'exécution.|  
|**Tâches abandonnées/s**|Ce compteur signale le nombre de tâches de procédures stockées d'activation s'étant soldées par une erreur ou ayant été abandonnées par un moniteur de file d'attente du fait de la non-réception de messages.|  
|**Tâches en cours d'exécution**|Ce compteur fait état du nombre de procédures stockées d'activation en cours d'exécution.|  
|**Tâches démarrées/s**|Ce compteur indique le nombre de procédures stockées d'activation appelées par seconde par tous les moniteurs de file d'attente de l'instance.|  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql.md)   
 [sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
