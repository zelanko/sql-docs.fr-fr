---
title: Sys.time_zone_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Data Warehouse
- SQL Server (starting with 2016)
f1_keywords:
- sys.time_zone_info
- sys.time_zone_info_TSQL
- time_zone_info
- time_zone_info_TSQL
helpviewer_keywords:
- sys.time_zone_info system table
ms.assetid: 3f51a9a4-75f8-4a11-9552-8bf6118b68da
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b642e3c84cd6d9d08f02f143d1bc3356a80c13ba
ms.sourcegitcommit: 95093f8b4f3d02f8d55d415f03a241102a641cb3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39654324"
---
# <a name="systimezoneinfo-transact-sql"></a>sys.time_zone_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-asdw-xxx-md.md)]

  Retourne des informations sur les fuseaux horaires pris en charge. Tous les fuseaux horaires installés sur l’ordinateur sont stockés dans la ruche de Registre suivante :  
`KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones` .  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du fuseau horaire au format standard de Windows. Par exemple, **CEN. Heure d’hiver Australie** ou **Europe centrale**.|  
|**current_utc_offset**|**nvarchar(12)**|En cours de l’offset UTC. Par exemple, **+ 01:00** ou **-07:00**.|  
|**is_currently_dst**|**bit**|True si actuellement en observant l’heure d’été.|  
  
## <a name="see-also"></a>Voir aussi  
 [GETUTCDATE &#40;Transact-SQL&#41;](../../t-sql/functions/getutcdate-transact-sql.md)   
 [AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [Types de données et fonctions de date et d’heure &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [Affichages catalogue de Configuration de l’échelle du serveur &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)  
