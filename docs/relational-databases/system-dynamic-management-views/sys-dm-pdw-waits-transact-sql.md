---
title: Sys.dm_pdw_waits (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5130e498-1c77-4ae3-a80b-9aae396494e9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a19e82707797c50f4180f7f5ef6090a9f52f6419
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716727"
---
# <a name="sysdmpdwwaits-transact-sql"></a>Sys.dm_pdw_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient les informations relatives à tous les attendre États rencontrées pendant l’exécution d’une demande ou des attentes de requête, y compris les verrous, files d’attente de transmission, et ainsi de suite.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Id numérique unique associé à l’état d’attente.<br /><br /> Clé pour cette vue.|Le point d’entrée unique pour toutes les attentes dans le système.|  
|session_id|**nvarchar(32)**|ID de la session sur laquelle l’état d’attente s’est produite.|Consultez session_id dans [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Type|**nvarchar(255)**|Type d’attente que représente cette entrée.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_type|**nvarchar(255)**|Type d’objet qui est affectée par l’attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_name|**nvarchar(386)**|Nom ou GUID de l’objet spécifié qui a été affectée par l’attente.||  
|request_id|**nvarchar(32)**|ID de la demande sur lequel l’état d’attente s’est produite.|Consultez request_id dans [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|request_time|**datetime**|Heure à laquelle l’état d’attente a été demandée.||  
|acquire_time|**datetime**|Heure à laquelle a été acquis le verrou ou une ressource.||  
|state|**nvarchar(50)**|État de l’état d’attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**Int**|Priorité de l’élément en attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
  
