---
title: "Objet SQL Server&#160;: Statistiques des objets de transmission de Service Broker | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Broker Transmission Object (objet)"
  - "SQL Server : Statistiques des objets de transmission de Service Broker"
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
caps.latest.revision: 14
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 14
---
# Objet SQL Server&#160;: Statistiques des objets de transmission de Service Broker
  L’objet de performance SQL Server : Statistiques des objets de transmission de Service Broker communique des informations sur le nombre de fois que des dialogues [!INCLUDE[ssSB](../../includes/sssb-md.md)] demandent des objets de transmission et sur la fréquence à laquelle des objets de transmission sont écrits dans **tempdb**.  
  
 Les objets de transmission enregistrent l'état de transmissions de message pour un dialogue [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Ils sont stockés en mémoire. Pour libérer de la mémoire, [!INCLUDE[ssSB](../../includes/sssb-md.md)] écrit périodiquement des lots d’objets de transmission inactifs dans des tables de travail **tempdb**.  
  
 Le tableau ci-dessous répertorie les compteurs que cet objet contient.  
  
|Compteurs de Statistiques des objets de transmission de Service Broker|Description|  
|----------------------------------------------|-----------------|  
|**Nombre moyen Longueur moy. des écritures par lot**|Nombre moyen d'objets de transmission enregistrés dans un lot.|  
|**Nombre moyen Durée moy. d'écriture d'un lot (ms)**|Nombre moyen de millisecondes requises pour enregistrer un lot d'objets de transmission.|  
|**Nombre moyen Durée d’écriture de la base d’un lot**|À usage interne uniquement|
|**Nombre moyen Durée moy. entre chaque lot (ms)**|Nombre moyen de millisecondes entre des écritures de lots d'objets de transmission.|  
|**Nombre moyen Base de durée entre chaque lot**|À usage interne uniquement| 
|**Objets de transmission obtenus/s**|Nombre de fois par seconde que les dialogues ont demandé des objets de transmission.|  
|**Nombre d'objets de transmission marqués comme modifiés/s**|Nombre de fois par seconde que les objets de transmission ont été marqués comme modifiés. Les objets de transmission sont marqués comme modifiés par la première modification qui entraîne une différence entre la copie en mémoire et la copie stockée dans **tempdb**. Les objets de transmission sont modifiés lorsque [!INCLUDE[ssSB](../../includes/sssb-md.md)] doit enregistrer une modification dans l'état des transmissions de message pour le dialogue.|  
|**Objets de transmission écrits/s**|Nombre de fois par seconde où un lot d’objets de transmission a été écrit dans les tables de travail **tempdb** . De grands nombres d'écritures peuvent indiquer que la mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est accentuée.|  
  
## Voir aussi  
 [SQL Server - Objet Access Methods](../../relational-databases/performance-monitor/sql-server-access-methods-object.md)   
 [Objet SQLServer:Memory Manager](../../relational-databases/performance-monitor/sql-server-memory-manager-object.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  