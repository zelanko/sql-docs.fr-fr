---
title: Objet SQL Server, ExecStatistics | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 44dc1c8df0385b61ce6b378caa15e3b63af23ab7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-execstatistics-object"></a>Objet SQL Server, ExecStatistics
  L'objet **SQLServer:ExecStatistics** de Microsoft SQL Server intègre des compteurs chargés de surveiller les diverses exécutions.  
  
 Ce tableau décrit les compteurs **Exec Statistics** de SQL Server.  
  
|Compteurs ExecStatistics de SQL Server|Description|  
|-----------------------------------------|-----------------|  
|**Requête distribuée**|Statistiques relatives à l'exécution de requêtes distribuées|  
|**Appels DTC**|Statistiques relatives à l'exécution d'appels DTC|  
|**Procédures étendues**|Statistiques relatives à l'exécution de procédures étendues|  
|**Appels OLEDB**|Statistiques relatives à l''exécution d'appels OLEDB|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Élément|Description|  
|----------|-----------------|  
|**Temps d'exécution moyen (ms)**|Temps d'exécution moyen pour le type d'exécution sélectionné|  
|**Temps d'exécution cumulé (ms) par seconde**|Temps d'exécution global par seconde pour le type d'exécution sélectionné|  
|**Exécutions en cours**|Nombre d'exécutions en cours pour le type d'exécution sélectionné|  
|**Exécutions démarrées par seconde**|Nombre d'exécutions démarrées par seconde pour le type d'exécution sélectionné|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
