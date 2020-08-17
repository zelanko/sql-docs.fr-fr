---
description: sys.dm_xe_database_session_events (Azure SQL Database)
title: sys.dm_xe_database_session_events
titleSuffix: Azure SQL Database
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 9e985a19-f93f-4c56-b644-12c529298011
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-lt-2019
ms.openlocfilehash: 06de1e7657008f924e80427b3e9bfa04eae225a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88323055"
---
# <a name="sysdm_xe_database_session_events-azure-sql-database"></a>sys.dm_xe_database_session_events (Azure SQL Database)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Retourne des informations sur les événements de la session. Les événements sont des points d'exécution discrets. Des prédicats peuvent être appliqués aux événements pour les empêcher de se déclencher si ces événements ne contiennent pas les informations requises.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et à toutes les versions ultérieures.|  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|Adresse mémoire de la session d'événements. N'accepte pas la valeur NULL.|  
|event_name|**nvarchar(60)**|Nom de l'événement auquel est liée une action. N'accepte pas la valeur NULL.|  
|event_package_guid|**uniqueidentifier**|GUID pour le package contenant l'événement. N'accepte pas la valeur NULL.|  
|event_predicate|**nvarchar(2048)**|Représentation XML de l'arborescence prédicat qui est appliquée à l'événement. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|Du|À|Relation|  
|----------|--------|------------------|  
|sys. dm_xe_database_session_events. event_session_address|sys. dm_xe_database_sessions. Address|Plusieurs-à-un|  
|sys. dm_xe_database_session_events. event_package_guid, sys. dm_xe_database_session_events. event_name|sys.dm_xe_objects.name, sys.dm_xe_objects.package_guid|Plusieurs-à-un|  
  
  
