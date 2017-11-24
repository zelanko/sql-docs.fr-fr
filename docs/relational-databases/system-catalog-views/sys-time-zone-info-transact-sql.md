---
title: Sys.time_zone_info (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
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
helpviewer_keywords: sys.time_zone_info system table
ms.assetid: 3f51a9a4-75f8-4a11-9552-8bf6118b68da
caps.latest.revision: "7"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b4d893e468c2d9820506bb4be18de8c8fbb6dd28
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systimezoneinfo-transact-sql"></a>Sys.time_zone_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Retourne des informations sur les fuseaux horaires pris en charge. Tous les fuseaux horaires, installés sur l’ordinateur sont stockées dans la ruche de Registre suivante :  
`KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones`.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du fuseau horaire au format standard de Windows. Par exemple, **CEN. Australie** ou **Europe centrale**.|  
|**current_utc_offset**|**nvarchar(12)**|En cours de l’offset UTC. Par exemple, **+ 01:00** ou **-07:00**.|  
|**is_currently_dst**|**bit**|True si actuellement en observant l’heure d’été.|  
  
## <a name="see-also"></a>Voir aussi  
 [GETUTCDATE &#40; Transact-SQL &#41;](../../t-sql/functions/getutcdate-transact-sql.md)   
 [FUSEAU horaire &AMP;#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [Données de date et heure les fonctions et Types de &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [Affichages catalogue de Configuration du serveur &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)  
  
  
