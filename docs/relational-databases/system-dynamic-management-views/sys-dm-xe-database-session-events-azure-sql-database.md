---
title: Sys.dm_xe_database_session_events (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 9e985a19-f93f-4c56-b644-12c529298011
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 869ed1a58cde0c8350bfd05a97538a5e73931548
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758727"
---
# <a name="sysdmxedatabasesessionevents-azure-sql-database"></a>sys.dm_xe_database_session_events (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les événements de la session. Les événements sont des points d'exécution discrets. Des prédicats peuvent être appliqués aux événements pour les empêcher de se déclencher si ces événements ne contiennent pas les informations requises.  
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et les versions ultérieures.|  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Adresse mémoire de la session d'événements. N'accepte pas la valeur NULL.|  
|event_name|**nvarchar(60)**|Nom de l'événement auquel est liée une action. N'accepte pas la valeur NULL.|  
|event_package_guid|**uniqueidentifier**|GUID pour le package contenant l'événement. N'accepte pas la valeur NULL.|  
|event_predicate|**nvarchar(2048)**|Représentation XML de l'arborescence prédicat qui est appliquée à l'événement. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|From|Pour|Relation|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_events.event_session_address|sys.dm_xe_database_sessions.address|Plusieurs-à-un|  
|Sys.dm_xe_database_session_events.event_package_guid, sys.dm_xe_database_session_events.event_name|sys.dm_xe_objects.name, sys.dm_xe_objects.package_guid|Plusieurs-à-un|  
  
  
