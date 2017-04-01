---
title: "Objet SQL Server, ExecStatistics | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQLServer:ExecStatistics"
  - "ExecStatistics (objet)"
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Objet SQL Server, ExecStatistics
  L'objet **SQLServer:ExecStatistics** de Microsoft SQL Server intègre des compteurs chargés de surveiller les diverses exécutions.  
  
 Ce tableau décrit les compteurs **Exec Statistics** de SQL Server.  
  
|Compteurs ExecStatistics de SQL Server|Description|  
|-----------------------------------------|-----------------|  
|**Requête distribuée**|Statistiques relatives à l'exécution de requêtes distribuées|  
|**Appels DTC**|Statistiques relatives à l'exécution d'appels DTC|  
|**Procédures étendues**|Statistiques relatives à l'exécution de procédures étendues|  
|**Appels OLEDB**|Statistiques relatives à l''exécution d'appels OLEDB|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Élément|Description|  
|----------|-----------------|  
|**Temps d'exécution moyen (ms)**|Temps d'exécution moyen pour le type d'exécution sélectionné|  
|**Temps d'exécution cumulé (ms) par seconde**|Temps d'exécution global par seconde pour le type d'exécution sélectionné|  
|**Exécutions en cours**|Nombre d'exécutions en cours pour le type d'exécution sélectionné|  
|**Exécutions démarrées par seconde**|Nombre d'exécutions démarrées par seconde pour le type d'exécution sélectionné|  
  
## Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  