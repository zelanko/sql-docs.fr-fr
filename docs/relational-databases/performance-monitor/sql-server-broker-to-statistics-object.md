---
title: SQL Server, objet Broker TO Statistics | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
caps.latest.revision: "14"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 356fc4a2b894cbcb226678b4aa320c4590002dbb
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-broker-to-statistics-object"></a>SQL Server, objet Broker TO Statistics
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] L’objet de performance SQLServer:Broker TO Statistics communique des informations sur le nombre de fois que des boîtes de dialogue [!INCLUDE[ssSB](../../includes/sssb-md.md)] demandent des objets de transmission, et sur la fréquence à laquelle des objets de transmission sont écrits dans **tempdb**.  
  
 Les objets de transmission enregistrent l'état de transmissions de message pour un dialogue [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Ils sont stockés en mémoire. Pour libérer de la mémoire, [!INCLUDE[ssSB](../../includes/sssb-md.md)] écrit périodiquement des lots d’objets de transmission inactifs dans des tables de travail **tempdb**.  
  
 Le tableau ci-dessous répertorie les compteurs que cet objet contient.  
  
|Compteurs de Statistiques des objets de transmission de Service Broker|Description|  
|----------------------------------------------|-----------------|  
|**Longueur moy. des écritures par lot**|Nombre moyen d'objets de transmission enregistrés dans un lot.|  
|**Durée moy. d’écriture d’un lot (ms)**|Nombre moyen de millisecondes requises pour enregistrer un lot d'objets de transmission.|  
|**Durée moy. d’écriture de la base d’un lot**|À usage interne uniquement|
|**Durée moy. entre chaque lot (ms)**|Nombre moyen de millisecondes entre des écritures de lots d'objets de transmission.|  
|**Durée moy. entre la base de chaque lot**|À usage interne uniquement| 
|**Objets de transmission obtenus/s**|Nombre de fois par seconde que les dialogues ont demandé des objets de transmission.|  
|**Nombre d'objets de transmission marqués comme modifiés/s**|Nombre de fois par seconde que les objets de transmission ont été marqués comme modifiés. Les objets de transmission sont marqués comme modifiés par la première modification qui entraîne une différence entre la copie en mémoire et la copie stockée dans **tempdb**. Les objets de transmission sont modifiés lorsque [!INCLUDE[ssSB](../../includes/sssb-md.md)] doit enregistrer une modification dans l'état des transmissions de message pour le dialogue.|  
|**Objets de transmission écrits/s**|Nombre de fois par seconde où un lot d’objets de transmission a été écrit dans les tables de travail **tempdb** . De grands nombres d'écritures peuvent indiquer que la mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est accentuée.|  
  
## <a name="see-also"></a> Voir aussi  
 [SQL Server - Objet Access Methods](../../relational-databases/performance-monitor/sql-server-access-methods-object.md)   
 [Objet SQLServer:Memory Manager](../../relational-databases/performance-monitor/sql-server-memory-manager-object.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
