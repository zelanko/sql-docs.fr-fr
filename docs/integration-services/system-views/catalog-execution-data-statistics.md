---
title: Catalog.execution_data_statistics | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 6f51407e-0e4e-4b44-af33-db14c9d40ded
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: fa1d87489ff6d0a10d95bf160ded3d038ca39d81
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="catalogexecutiondatastatistics"></a>catalog.execution_data_statistics
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Cette vue affiche une ligne chaque fois qu'un composant de flux de données envoie des données à un composant en aval, pour une exécution de package donnée. Les informations de cette vue peuvent être utilisées pour calculer le débit des données pour un composant.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|data_stats_id|**bigint**|Identificateur (ID) unique des données.|  
|execution_id|**bigint**|ID unique de l'instance d'exécution.|  
|package_name|**nvarchar (260)**|Nom du premier package démarré pendant l'exécution.|  
|task_name|**nvarchar(4000)**|Nom de la tâche de flux de données.|  
|dataflow_path_id_string|**nvarchar(4000)**|Chaîne d'identification du chemin d'accès de flux de données.|  
|dataflow_path_name|**nvarchar(4000)**|Nom du chemin d'accès de flux de données.|  
|source_component_name|**nvarchar(4000)**|Nom du composant de flux de données ayant envoyé les données.|  
|destination_component_name|**nvarchar(4000)**|Nom du composant de flux de données ayant reçu les données.|  
|rows_sent|**bigint**|Nombre de lignes envoyées à partir du composant source.|  
|created_time|**datatimeoffset(7)**|Heure à laquelle les valeurs ont été obtenues.|  
|execution_path|**nvarchar(max)**|Chemin d'accès d'exécution du composant.|  
  
## <a name="remarks"></a>Notes  
  
-   Lorsqu'il existe plusieurs sorties du composant, une ligne est ajoutée pour chacune d'elles.  
  
-   Par défaut, lors du démarrage d'une exécution, les informations sur le nombre de lignes envoyées ne sont pas enregistrées.  
  
-   Pour afficher ces données pour une exécution de package donnée, définissez le niveau de journalisation sur **Verbose**. Pour plus d’informations, consultez [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).  
  
## <a name="permissions"></a>Autorisations  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'instance d'exécution  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
