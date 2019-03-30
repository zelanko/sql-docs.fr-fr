---
title: sys.dm_pdw_sql_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 44e19609-902c-46cf-acdf-19ea75011365
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 24bcf44fe2e1e0d35610dba9fb40d64ac2c819bb
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658003"
---
# <a name="sysdmpdwsqlrequests-transact-sql"></a>sys.dm_pdw_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les distributions de requête de SQL Server dans le cadre d’une étape SQL dans la requête.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Identificateur unique de la requête à laquelle appartient cette distribution de la requête SQL.<br /><br /> argument distribution_id request_id et step_index forment la clé pour cette vue.|Consultez request_id dans [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**Int**|Index de cette distribution fait partie de l’étape de requête.<br /><br /> argument distribution_id request_id et step_index forment la clé pour cette vue.|Consultez step_index dans [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|pdw_node_id|**Int**|Identificateur unique du nœud sur lequel cette distribution de la requête est exécutée.|Consultez node_id dans [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**Int**|Identificateur unique de la distribution sur lequel cette distribution de la requête est exécutée.<br /><br /> argument distribution_id request_id et step_index forment la clé pour cette vue.|Consultez l’argument distribution_id dans [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md). La valeur -1 pour les requêtes qui s’exécutent dans l’étendue du nœud, pas l’étendue de la distribution.|  
|status|**nvarchar(32)**|État actuel de la distribution de la requête.|En attente, en cours d’exécution, ayant échoué, annulé, terminée, annulée, CancelSubmitted|  
|error_id|**nvarchar(36)**|Identificateur unique de l’erreur associée à cette distribution de requête, le cas échéant.|Consultez ID_erreur dans [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). La valeur NULL si aucune erreur ne s’est produite.|  
|start_time|**datetime**|Heure de début de l’exécution de requête distribution.|Plus petit ou égal à l’heure actuelle et supérieure ou égale à start_time de l’étape de requête appartient cette distribution de la requête|  
|end_time|**datetime**|Heure à laquelle cette distribution de la requête exécutée avec succès, a été annulée ou a échoué.|Supérieur ou égal à l’heure de début, ou NULL si la distribution de la requête est en cours ou en file d’attente.|  
|total_elapsed_time|**Int**|Représente l’heure de que la distribution de la requête a été en cours d’exécution, en millisecondes.|Supérieur ou égal à 0. Égaux au delta de start_time et end_time pour terminé, échec ou annulé les distributions de requête.<br /><br /> Si total_elapsed_time dépasse la valeur maximale d’un entier, total_elapsed_time continueront à être la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée. »<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours environ.|  
|row_count|**bigint**|Nombre de lignes modifiées ou lues par cette distribution de la requête.|-1 pour les opérations de modifier ou de retourner des données, telles que CREATE TABLE et DROP TABLE.|  
|spid|**Int**|Id de session sur l’instance de SQL Server exécute la distribution de la requête.||  
|commande|**nvarchar(4000)**|Texte complet de commande pour cette distribution de la requête.|Toute chaîne de requête ou de requête valide.|  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section de métadonnées dans le [limites de capacité](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
