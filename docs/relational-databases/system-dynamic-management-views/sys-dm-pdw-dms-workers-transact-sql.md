---
title: sys.dm_pdw_dms_workers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0a284d18-3c46-4ffa-bcc9-689e660ee8b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 96fd36d1710a166285fecba092735c7d2495271e
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658243"
---
# <a name="sysdmpdwdmsworkers-transact-sql"></a>sys.dm_pdw_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur tous les traitements étapes effectuées DMS.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Que ce processus de travail DMS fait partie d’une requête.<br /><br /> request_id, step_index et dms_step_index forment la clé pour cette vue.|Consultez request_id dans [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**Int**|Étape de que ce processus de travail DMS est la partie de la requête.<br /><br /> request_id, step_index et dms_step_index forment la clé pour cette vue.|Consultez step_index dans [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**Int**|Étape dans le plan DMS que ce processus de travail est en cours d’exécution.<br /><br /> request_id, step_index et dms_step_index forment la clé pour cette vue.||  
|pdw_node_id|**Int**|Nœud qui le processus de travail est en cours d’exécution.|Consultez node_id dans [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**Int**|Distribution du travail s’exécute, le cas échéant.|Consultez l’argument distribution_id dans [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md).|  
|Type|**nvarchar(32)**|Type de thread de travail DMS que représente cette entrée.|'DIRECT_CONVERTER', 'DIRECT_READER', 'FILE_READER', 'HASH_CONVERTER', 'HASH_READER', 'ROUNDROBIN_CONVERTER', 'EXPORT_READER', 'EXTERNAL_READER', 'EXTERNAL_WRITER', 'PARALLEL_COPY_READER', « REJECT_WRITER », « WRITER »|  
|status|**nvarchar(32)**|État du processus de travail DMS.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**bigint**|Débit de lecture ou d’écriture de la dernière seconde.|Supérieur ou égal à 0. NULL si la requête a été annulée ou a échoué avant d’exécuter le processus de travail.|  
|bytes_processed|**bigint**|Nombre total d’octets traité par ce processus de travail.|Supérieur ou égal à 0. NULL si la requête a été annulée ou a échoué avant d’exécuter le processus de travail.|  
|rows_processed|**bigint**|Nombre de lignes lues ou écrites pour ce processus de travail.|Supérieur ou égal à 0. NULL si la requête a été annulée ou a échoué avant d’exécuter le processus de travail.|  
|start_time|**datetime**|Heure de début de l’exécution de ce processus de travail.|Supérieur ou égal à l’heure de début de l’étape de requête qu'auquel appartient ce processus de travail. See [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Heure à laquelle l’exécution s’est terminée, a échoué ou a été annulée.|NULL pour les travailleurs en cours ou en file d’attente. Sinon, supérieur à start_time.|  
|total_elapsed_time|**Int**|Temps total passé dans l’exécution, en millisecondes.|Supérieur ou égal à 0.<br /><br /> Temps total écoulé depuis le système de démarrer ou redémarrer. Si total_elapsed_time dépasse la valeur maximale d’un entier (24,8 jours en millisecondes), cela entraînera l’échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours environ.|  
|cpu_time|**bigint**|Temps de processeur consommé par ce processus de travail, en millisecondes.|Supérieur ou égal à 0.|  
|query_time|**Int**|Période de temps avant que SQL démarre en renvoyant des lignes au thread, en millisecondes.|Supérieur ou égal à 0.|  
|buffers_available|**Int**|Nombre de mémoires tampons non utilisées.| NULL si la requête a été annulée ou a échoué avant d’exécuter le processus de travail.|  
|sql_spid|**Int**|Id de session sur l’instance de SQL Server effectuant le travail pour ce processus de travail DMS.||  
|dms_cpid|**Int**|ID de processus du thread réel en cours d’exécution.||  
|error_id|**nvarchar(36)**|Identificateur unique de l’erreur qui s’est produite pendant l’exécution de ce processus de travail, le cas échéant.|Consultez ID_erreur dans [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|source_info|**nvarchar(4000)**|Pour un lecteur, la spécification des tables sources et des colonnes.||  
|destination_info|**nvarchar(4000)**|Pour un writer, spécification des tables de destination.||  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section de métadonnées dans le [limites de capacité](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) rubrique...  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
