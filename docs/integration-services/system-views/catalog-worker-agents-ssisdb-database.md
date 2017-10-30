---
title: "Catalog.worker_agents (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd0d827-e2f1-44fe-aa90-6bf922d68d16
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: d56af0ab150255c53746898a638a32112938755c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/08/2017

---
# <a name="catalogworkeragents-ssisdb-database"></a>Catalog.worker_agents (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Affiche les informations pour le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] montée en puissance des processus de travail.

|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|WorkerAgentId|**uniqueidentifier**|L’agent de travailleur ID de montée en puissance des processus de travail.|
|IsEnabled|**bit**|Indique si le montée en puissance des processus de travail est activée.|
|DisplayName|**nvarchar (256)**|Le nom complet de montée en puissance des processus de travail.|
| Description|**nvarchar (256)**|Description de la montée en puissance des processus de travail.|
|MachineName|**nvarchar (256)**|Le nom d’ordinateur pour l’échelle des processus de travail.|
|Balises|**nvarchar(max)**|Les balises de montée en puissance des processus de travail.|
|UserAccount|**nvarchar (256)**|Le compte d’utilisateur exécutant le service de mise à l’échelle des processus de travail.|
|LastOnlineTime|**DateTimeOffset(7)**|La dernière fois à la montée en puissance des processus de travail est en ligne.|

## <a name="remarks"></a>Notes
Cette vue affiche une ligne pour chaque montée en puissance des processus de travail la connexion à l’échelle des Master travaillant avec le catalogue SSISDB.

## <a name="permissions"></a>Permissions
Cette vue requiert l'une des autorisations suivantes :

- L’appartenance à la **ssis_admin** rôle de base de données

- L’appartenance à la **ssis_cluster_executor** rôle de base de données

- L’appartenance à la **sysadmin** rôle de serveur

