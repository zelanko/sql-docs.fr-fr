---
title: SQL Server, objet External Scripts | Microsoft Docs
ms.custom: ''
ms.date: 03/21/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- External Scripts object
- SQLServer:External Scripts
ms.assetid: 8a75ccce-b174-4937-bc92-8e413b55afe1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e6eb921d6ebee88ce14ad30b0d2071941ec5f007
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47665547"
---
# <a name="sql-server-external-scripts-object"></a>SQL Server, objet External Scripts
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="see-also"></a> Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)   
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
