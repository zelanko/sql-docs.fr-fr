---
title: Sys.dm_pdw_errors (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 944eac31-5691-432b-b9f5-f1e11c05191f
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 796e3e1d888c765bd54b817cb6547adbba21f2c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735097"
---
# <a name="sysdmpdwerrors-transact-sql"></a>Sys.dm_pdw_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les erreurs rencontrées pendant l’exécution d’une requête ou d’une requête.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|error_id|**nvarchar(36)**|Clé pour cette vue.<br /><br /> Id numérique unique associé à l’erreur.|Le point d’entrée unique pour toutes les erreurs de requête dans le système.|  
|source|**nvarchar(64)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|Type|**nvarchar(4000)**|Type d'erreur qui s'est produit.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|create_time|**datetime**|Heure à laquelle l’erreur s’est produite.|Inférieur ou égal à l’heure actuelle.|  
|pwd_node_id|**Int**|Identificateur du nœud spécifique impliqué, le cas échéant. Pour plus d’informations sur les ID de nœud, consultez [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).||  
|session_id|**nvarchar(32)**|Identificateur de la session impliquée, le cas échéant. Pour plus d’informations sur les ID de session, consultez [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|request_id|**nvarchar(32)**|Identificateur de la demande impliquée, le cas échéant. Pour plus d’informations sur les ID de demande, consultez [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).||  
|spid|**Int**|SPID de la session de SQL Server impliquée, le cas échéant.||  
|thread_id|**Int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|détails|**nvarchar(4000)**|Contient la description complète de l’erreur.||  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section de valeurs de la vue système maximales dans le [valeurs minimales et maximales (SQL Server PDW)](http://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9) rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
