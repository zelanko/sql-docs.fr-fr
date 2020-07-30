---
title: sys. time_zone_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.time_zone_info
- sys.time_zone_info_TSQL
- time_zone_info
- time_zone_info_TSQL
helpviewer_keywords:
- sys.time_zone_info system table
ms.assetid: 3f51a9a4-75f8-4a11-9552-8bf6118b68da
author: CarlRabeler
ms.author: carlrab
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bc96f144e7b23b54faae5a58bf6f17975daa305c
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395214"
---
# <a name="systime_zone_info-transact-sql"></a>sys.time_zone_info (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Retourne des informations sur les fuseaux horaires pris en charge. Tous les fuseaux horaires installés sur l’ordinateur sont stockés dans la ruche de Registre suivante :  
`KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones`.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom du fuseau horaire dans le format standard Windows. Par exemple, l' **heure standard CEN. Australia** ou l’heure d’hiver de l' **Europe centrale**.|  
|**current_utc_offset**|**nvarchar (12)**|Décalage actuel en heure UTC. Par exemple, **+ 01:00** ou **-07:00**.|  
|**is_currently_dst**|**bit**|True si vous observez actuellement l’heure d’été.|  
  
## <a name="see-also"></a>Voir aussi  
 [GETUTCDATE &#40;Transact-SQL&#41;](../../t-sql/functions/getutcdate-transact-sql.md)   
 [DANS le fuseau horaire &#40;&#41;Transact-SQL](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [Fonctions et types de données de date et d’heure &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [Affichages catalogue de configurations à l’ensemble du serveur &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)  
