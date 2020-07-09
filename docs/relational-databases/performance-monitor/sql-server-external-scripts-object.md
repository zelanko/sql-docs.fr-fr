---
title: SQL Server, objet External Scripts | Microsoft Docs
ms.custom: ''
ms.date: 03/21/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- External Scripts object
- SQLServer:External Scripts
ms.assetid: 8a75ccce-b174-4937-bc92-8e413b55afe1
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 3d1a481dfc14e3c84df78f2950a140f1bb14c059
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775872"
---
# <a name="sql-server-external-scripts-object"></a>SQL Server, objet External Scripts
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  L’objet **SQLServer : Scripts externes** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs pour surveiller les actions associées à l’exécution de scripts externes. Pour plus d’informations sur l’exécution de scripts externes, consultez [sp_execute_external_script &#40;Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
  
 Ce tableau décrit les compteurs **Scripts externes** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
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
  
  
