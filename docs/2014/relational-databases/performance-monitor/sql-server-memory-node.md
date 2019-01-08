---
title: SQL Server, nœud de mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 32a2296fdb68e640ce8ebfc8dd9cdb351666b337
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52803581"
---
# <a name="sql-server-memory-node"></a>SQL Server, nœud de mémoire
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
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, objet Gestionnaire de tampons](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
