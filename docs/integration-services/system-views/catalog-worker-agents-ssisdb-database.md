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
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 198f730938d316a97948c51c893a5e651733ef64
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997784"
---
# <a name="catalogworkeragents-ssisdb-database"></a>catalog.worker_agents (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Affiche les informations de l’[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker.

|Nom de colonne|Type de données|Description|  
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
