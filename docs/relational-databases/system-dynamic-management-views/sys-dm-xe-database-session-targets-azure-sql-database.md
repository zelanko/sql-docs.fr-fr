---
title: sys.dm_xe_database_session_targets
titleSuffix: Azure SQL Database
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 7f353e2a-f8fc-4366-97e4-aa1c49eadaf4
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: ac4b9b01b85b6c8b4832a591ba18654ac58e9125
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826683"
---
# <a name="sysdm_xe_database_session_targets-azure-sql-database"></a>sys.dm_xe_database_session_targets (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Renvoie des informations sur les cibles d’une session d’événements.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et à toutes les futures versions.|  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|Adresse mémoire de la session d'événements. A une relation plusieurs-à-un avec sys. dm_xe_database_sessions. Address. N'accepte pas la valeur NULL.|  
|target_name|**nvarchar(60)**|Nom de la cible au sein d'une session. N'accepte pas la valeur NULL.|  
|target_package_guid|**uniqueidentifier**|GUID du package qui contient la cible. N'accepte pas la valeur NULL.|  
|execution_count|**bigint**|Nombre d'exécutions de la cible pour la session. N'accepte pas la valeur NULL.|  
|execution_duration_ms|**bigint**|Temps d'exécution total de la cible, en millisecondes. N'accepte pas la valeur NULL.|  
|target_data|**nvarchar(max)**|Données gérées par la cible, par exemple les informations sur l'agrégation d'événements. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|À partir|À|Relation|  
|----------|--------|------------------|  
|sys. dm_xe_database_session_targets. event_session_address|sys. dm_xe_database_sessions. Address|Plusieurs-à-un|  
  
  
