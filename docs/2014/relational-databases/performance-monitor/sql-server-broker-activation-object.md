---
title: SQL Server, Broker Activation (objet) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 59c66bc237b496fd913658f168b7b1c0089fdc00
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63250694"
---
# <a name="sql-server-broker-activation-object"></a>SQL Server, Broker Activation (objet)
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
 [sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql)   
 [sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
