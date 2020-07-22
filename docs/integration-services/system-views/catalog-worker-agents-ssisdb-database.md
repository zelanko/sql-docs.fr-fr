---
title: catalog.worker_agents (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0bd0d827-e2f1-44fe-aa90-6bf922d68d16
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f8c494e135764ddca11985f3036068c848f818b
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912425"
---
# <a name="catalogworker_agents-ssisdb-database"></a>catalog.worker_agents (base de données SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Affiche les informations de l’[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker.

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|WorkerAgentId|**uniqueidentifier**|ID d’agent de Worker de Scale Out Worker.|
|IsEnabled|**bit**|Indique si le Scale Out Worker est activé.|
|DisplayName|**nvarchar (256)**|Nom complet de Scale Out Worker.|
|Description|**nvarchar (256)**|Description de Scale Out Worker.|
|MachineName|**nvarchar (256)**|Nom de machine pour Scale Out Worker.|
|Balises|**nvarchar(max)**|Balises de Scale Out Worker.|
|UserAccount|**nvarchar (256)**|Compte d’utilisateur exécutant le service Scale Out Worker.|
|LastOnlineTime|**datetimeoffset(7)**|Dernière fois que le Scale Out Worker était en ligne.|

## <a name="remarks"></a>Notes
Cette vue affiche une ligne par connexion du Scale Out Worker au Scale Out Master utilisant le catalogue SSISDB.

## <a name="permissions"></a>Autorisations
Cette vue requiert l'une des autorisations suivantes :

- Appartenance au rôle de base de données **ssis_admin**

- Appartenance au rôle de base de données **ssis_cluster_executor**

- Appartenance au rôle serveur **sysadmin**
