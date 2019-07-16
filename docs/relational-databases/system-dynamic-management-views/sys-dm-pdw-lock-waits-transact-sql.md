---
title: Sys.dm_pdw_lock_waits (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8ef966f8-d14e-40d3-9626-3508ada9b8fb
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 29a82daa2857177200bd76b738f92d65f6b26668
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899379"
---
# <a name="sysdmpdwlockwaits-transact-sql"></a>Sys.dm_pdw_lock_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur les demandes en attente de verrous.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Position de la demande dans la liste d’attente.|ordinal à partir de 0. Cela n’est pas unique sur toutes les entrées de l’attente.|  
|session_id|**nvarchar(32)**|ID de la session dans laquelle l’état d’attente s’est produite.|Consultez session_id dans [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|type|**nvarchar(255)**|Type d’attente que représente cette entrée.|Valeurs possibles :<br /><br /> Partagés<br /><br /> SharedUpdate<br /><br /> ExclusiveUpdate<br /><br /> Exclusive|  
|object_type|**nvarchar(255)**|Type d’objet qui est affectée par l’attente.|Valeurs possibles :<br /><br /> OBJECT<br /><br /> DATABASE<br /><br /> SYSTEM<br /><br /> SCHEMA<br /><br /> APPLICATION|  
|object_name|**nvarchar(386)**|Nom ou GUID de l’objet spécifié qui a été affectée par l’attente.|Tables et les vues sont affichées avec des noms en trois parties.<br /><br /> Index et les statistiques sont affichées avec des noms en quatre parties.<br /><br /> Les noms, les principaux et les bases de données sont des noms de chaîne.|  
|request_id|**nvarchar(32)**|ID de la demande sur lequel l’état d’attente s’est produite.|ID de la demande.<br /><br /> Il s’agit d’un GUID pour les demandes de charge.|  
|request_time|**datetime**|Heure à laquelle le verrou ou la ressource a été demandée.||  
|acquire_time|**datetime**|Heure à laquelle a été acquis le verrou ou une ressource.||  
|state|**nvarchar(50)**|État de l’état d’attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Priorité de l’élément en attente.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
