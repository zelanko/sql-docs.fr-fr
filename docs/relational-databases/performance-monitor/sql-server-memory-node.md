---
title: SQL Server, nœud de mémoire | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: ed5f54ae9e24574589f880f864645a634d78e177
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380004"
---
# <a name="sql-server-memory-node"></a>SQL Server, nœud de mémoire
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'objet **Nœud de mémoire** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs permettant de surveiller l'utilisation globale de la mémoire sur des nœuds NUMA.  
  
## <a name="memory-node-counters"></a>Compteurs de nœuds de mémoire  
 Ce tableau décrit les compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Nœud de mémoire** .  
  
|Compteurs du Gestionnaire de mémoire de SQL Server|Description|  
|----------------------------------------|-----------------|  
|**Mémoire de nœud de base de données (Ko)**|Spécifie la quantité de mémoire que le serveur utilise actuellement sur ce nœud pour les pages de bases de données.|  
|**Mémoire disponible du nœud (Ko)**|Spécifie la quantité de mémoire que le serveur n'utilise pas sur ce nœud.|  
|**Mémoire distante du nœud (Ko)**|Spécifie la quantité de mémoire non-NUMA locale sur ce nœud.|  
|**Mémoire détournée du nœud (Ko)**|Spécifie la quantité de mémoire utilisée par le serveur sur ce nœud à d'autres fins que les pages de bases de données.|  
|**Mémoire cible du nœud**|Spécifie la quantité de mémoire idéale pour ce nœud.|  
|**Mémoire totale du nœud**|Indique la quantité totale de mémoire validée par le serveur sur ce nœud.|  
  
## <a name="see-also"></a> Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, objet Gestionnaire de tampons](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  
