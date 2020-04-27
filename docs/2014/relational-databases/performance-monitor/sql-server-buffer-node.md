---
title: SQL Server:Buffer Node | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Buffer Node
- Buffer Node object
ms.assetid: fd3f9f0f-7c38-4cfd-a0c5-ee93dd52d9a5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7e99c6e4f28ecef032ff3b793393e5465740156d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63250740"
---
# <a name="sql-serverbuffer-node"></a>SQL Server:Buffer Node
  L'objet **Nœud de tampon** fournit des compteurs qui complètent les compteurs de l'objet **Gestionnaire de tampons** . Il vous permet de contrôler la distribution des pages du pool de mémoires tampons [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour chaque nœud NUMA (Non-Uniform Memory Access). Il existe une instance de l'objet **Nœud de tampon** pour chaque nœud NUMA employé. Dans une architecture non-NUMA, une seule instance de l’objet **Nœud de tampon** est présente.  
  
## <a name="buffer-node-performance-objects"></a>Objets de performances du Nœud de tampon  
 Ce tableau décrit les objets de performance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Nœud de tampon**de**.  
  
|Compteurs de l'objet Nœud de tampon de SQL Server|Description|  
|-------------------------------------|-----------------|  
|**Pages de base de données**|Indique le nombre de pages dans le pool de mémoires tampons de ce nœud avec le contenu de la base de données.|  
|**Espérance de vie d'une page**|Indique le nombre minimal de secondes pendant lesquelles une page est conservée dans le pool de mémoires tampons sur ce nœud sans références.|  
|**Recherches de pages de nœud local/s**|Indique le nombre de demandes de recherches à partir de ce nœud qui ont été satisfaites par ce nœud.|  
|**Recherches de pages de nœud distant/s**|Indique le nombre de demandes de recherches à partir de ce nœud qui ont été satisfaites par d'autres nœuds.|  
  
 Si vous exécutez SQL Server sur du matériel non-NUMA, les compteurs des objets **Nœud de tampon** et **Gestionnaire de tampons** doivent correspondre.  
  
 Sur du matériel NUMA, les sommes des compteurs respectifs de tous les objets **Nœud de tampon** doivent correspondre aux sommes de leurs objets **Gestionnaire de tampons**équivalents.  
  
> [!NOTE]  
>  Il est possible que les valeurs et les sommes des compteurs ne correspondent pas exactement en raison de la nature dynamique des compteurs et de la précision d'échantillonnage.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server, objet Gestionnaire de tampons](sql-server-buffer-manager-object.md)   
 [Mémoire du serveur (option de configuration de serveur)](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
