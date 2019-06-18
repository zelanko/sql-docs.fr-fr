---
title: sys.dm_pdw_dms_external_work (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 47345015-f861-451e-97c4-6e1cb81d1922
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d02a1d50e9c7a5f906e78fa6753d594edced341f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62691049"
---
# <a name="sysdmpdwdmsexternalwork-transact-sql"></a>sys.dm_pdw_dms_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] vue système qui conserve des informations sur toutes les étapes de Service de déplacement des données (DMS) pour les opérations externes.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Requête qui est à l’aide de ce processus de travail DMS.<br /><br /> request_id, step_index et dms_step_index forment la clé pour cette vue.|Identique à request_id dans [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**Int**|Étape de requête qui appelle ce processus de travail DMS.<br /><br /> request_id, step_index et dms_step_index forment la clé pour cette vue.|Identique à step_index dans [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**Int**|Étape actuelle dans le plan DMS.<br /><br /> request_id, step_index et dms_step_index forment la clé pour cette vue.|Identique à dms___step_index dans [sys.dm_pdw_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md).|  
|pdw_node_id|**Int**|Nœud qui exécute le processus de travail DMS.|Identique à node_id dans [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|type|**nvarchar(60)**|Type d’opération externe que ce nœud est en cours d’exécution.<br /><br /> FICHIER fractionné est une opération sur un fichier Hadoop externe qui a été divisé en plusieurs concernent la plage plus petite.|« FRACTIONNEMENT DE FICHIER »|  
|work_id|**Int**|Le fichier fractionné le code.|Supérieur ou égal à 0.<br /><br /> Unique pour chaque nœud de calcul.|  
|input_name|**nvarchar(60)**|Nom de l’entrée en cours de lecture de la chaîne.|Pour un fichier Hadoop, ceci est le nom de fichier Hadoop.|  
|read_location|**bigint**|Décalage de l’emplacement de lecture.||  
|estimated_bytes_processed|**bigint**|Nombre d’octets traités par ce processus de travail.|Supérieur ou égal à 0.|  
|length|**bigint**|Nombre d’octets dans le fichier de fractionnement.<br /><br /> Pour Hadoop, il s’agit de la taille du bloc HDFS.|Défini par l’utilisateur. La valeur par défaut est 64 Mo.|  
|status|**nvarchar(32)**|État du processus de travail.|En attente, traitement, terminé, échec, abandonnée|  
|start_time|**datetime**|Heure de début de l’exécution de ce processus de travail.|Supérieur ou égal à l’heure de début de l’étape de requête qu'auquel appartient ce processus de travail. See [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Heure à laquelle l’exécution s’est terminée, a échoué ou a été annulée.|NULL pour les travailleurs en cours ou en file d’attente. Sinon, supérieur à start_time.|  
|total_elapsed_time|**Int**|Temps total passé dans l’exécution, en millisecondes.|Supérieur ou égal à 0.<br /><br /> Si total_elapsed_time dépasse la valeur maximale d’un entier, total_elapsed_time continueront à être la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée. »<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours environ.|  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section de métadonnées dans le [limites de capacité](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) rubrique.
  
## <a name="see-also"></a>Voir aussi  
 [System Views &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
