---
title: SQL Server, objet External Scripts | Microsoft Docs
ms.custom: 
ms.date: 03/21/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- External Scripts object
- SQLServer:External Scripts
ms.assetid: 8a75ccce-b174-4937-bc92-8e413b55afe1
caps.latest.revision: "7"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e5510df60aeff35597da1954fd97c9fc0eb8e86
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-external-scripts-object"></a>SQL Server, objet External Scripts
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  L’objet **SQLServer:External Scripts** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs pour surveiller les actions associées à l’exécution de scripts externes. Pour plus d’informations sur l’exécution de scripts externes, consultez [sp_execute_external_script &#40;Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
  
 Le tableau suivant décrit les compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Scripts externes** .  
  
|Compteurs Scripts externes SQL Server|Description|  
|------------------------------------------|-----------------|  
|**Erreurs d’exécution**|Nombre d’erreurs lors de l’exécution de scripts externes.|  
|**Connexions par auth. implicite**|Nombre de connexions de processus satellites authentifiés à l’aide de l’authentification implicite.|  
|**Exécutions parallèles**|Nombre de scripts externes exécutés avec @parallel = 1.|  
|**Exécutions de contexte de calcul SQL**|Nombre de scripts externes exécutés à l’aide du contexte de calcul SQL.|  
|**Exécutions avec diffusion en continu**|Nombre de scripts externes exécutés avec le paramètre @r_rowsPerRead.|  
|**Durée totale d’exécution (ms)**|Temps total d’exécution des scripts externes.|  
|**Nombre total d’exécutions**|Nombre de scripts externes exécutés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)   
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
