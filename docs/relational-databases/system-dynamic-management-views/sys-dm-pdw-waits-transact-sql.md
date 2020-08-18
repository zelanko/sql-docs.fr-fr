---
description: sys. dm_pdw_waits (Transact-SQL)
title: sys. dm_pdw_waits (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5130e498-1c77-4ae3-a80b-9aae396494e9
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1214a5e7f4d6d64d739440f0ecebf35d39a81dd8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88397835"
---
# <a name="sysdm_pdw_waits-transact-sql"></a>sys. dm_pdw_waits (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Contient des informations sur tous les États d’attente rencontrés lors de l’exécution d’une requête ou d’une requête, y compris les verrous, les attentes sur les files d’attente de transmission, etc.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|ID numérique unique associé à l’état d’attente.<br /><br /> Clé pour cette vue.|Unique dans toutes les attentes du système.|  
|session_id|**nvarchar(32)**|ID de la session sur laquelle l’état d’attente s’est produit.|Consultez session_id dans [sys. dm_pdw_exec_sessions &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|type|**nvarchar(255)**|Type d’attente représenté par cette entrée.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_type|**nvarchar(255)**|Type d’objet affecté par l’attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_name|**nvarchar(386**|Nom ou GUID de l’objet spécifié qui a été affecté par l’attente.||  
|request_id|**nvarchar(32)**|ID de la demande sur laquelle l’état d’attente s’est produit.|Consultez request_id dans [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|request_time|**datetime**|Heure à laquelle l’état d’attente a été demandé.||  
|acquire_time|**datetime**|Heure à laquelle le verrou ou la ressource a été acquis (e).||  
|state|**nvarchar(50)**|État de l’état d’attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Priorité de l’élément en attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys. dm_pdw_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
  
