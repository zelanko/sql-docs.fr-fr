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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250578"
---
# <a name="sql-server-memory-node"></a>SQL Server, nœud de mémoire
  L’objet **nœud de mémoire** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft fournit des compteurs pour surveiller l’utilisation de la mémoire du serveur sur les nœuds NUMA.  
  
## <a name="memory-node-counters"></a>Compteurs de nœuds de mémoire  
 Ce tableau décrit les compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Nœud de mémoire** .  
  
|Compteurs du Gestionnaire de mémoire de SQL Server|Description|  
|----------------------------------------|-----------------|  
|**Mémoire du nœud de base de données (Ko)**|Spécifie la quantité de mémoire que le serveur utilise actuellement sur ce nœud pour les pages de bases de données.|  
|**Mémoire disponible du nœud (Ko)**|Spécifie la quantité de mémoire que le serveur n'utilise pas sur ce nœud.|  
|**Mémoire du nœud étranger (Ko)**|Spécifie la quantité de mémoire non-NUMA locale sur ce nœud.|  
|**Nœud mémoire volée (Ko)**|Spécifie la quantité de mémoire utilisée par le serveur sur ce nœud à d'autres fins que les pages de bases de données.|  
|**Mémoire du nœud cible**|Spécifie la quantité de mémoire idéale pour ce nœud.|  
|**Mémoire totale du nœud**|Indique la quantité totale de mémoire validée par le serveur sur ce nœud.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, objet Gestionnaire de tampons](sql-server-buffer-manager-object.md)   
 [sys. dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
