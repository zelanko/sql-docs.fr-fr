---
title: Sys.dm_pdw_request_steps (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8543933aa102a6962846164b7267fad7df222cdd
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52393593"
---
# <a name="sysdmpdwrequeststeps-transact-sql"></a>Sys.dm_pdw_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les étapes qui composent une requête donnée ou une requête dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Elle répertorie une ligne par étape de la requête.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|request_id et step_index composent la clé pour cette vue.<br /><br /> Id numérique unique associé à la demande.|Consultez request_id dans [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**Int**|request_id et step_index composent la clé pour cette vue.<br /><br /> La position de cette étape dans la séquence d’étapes qui composent la demande.|0 pour (n-1) pour une demande avec n étapes.|  
|operation_type|**nvarchar(35)**|Type d’opération représentée par cette étape.|**Opérations de plan de requête DMS :** 'ReturnOperation', 'PartitionMoveOperation', 'MoveOperation', 'BroadcastMoveOperation', 'ShuffleMoveOperation', 'TrimMoveOperation', 'CopyOperation', 'DistributeReplicatedTableMoveOperation'<br /><br /> **Opérations de plan de requête SQL :** 'OnOperation', 'RemoteOperation'<br /><br /> **Autres opérations de plan de requête :** 'MetaDataCreateOperation', 'RandomIDOperation'<br /><br /> **Opérations externes pour les lectures :** 'HadoopShuffleOperation', 'HadoopRoundRobinOperation', 'HadoopBroadcastOperation'<br /><br /> **Opérations externes pour MapReduce :** 'HadoopJobOperation', 'HdfsDeleteOperation'<br /><br /> **Opérations externes pour les écritures :** 'ExternalExportDistributedOperation', 'ExternalExportReplicatedOperation', 'ExternalExportControlOperation'<br /><br /> Pour plus d’informations, consultez « Understanding Query Plans » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].|  
|distribution_type|**nvarchar(32)**|Type de distribution que subit cette étape.|'AllNodes', 'AllDistributions', 'AllComputeNodes', 'ComputeNode', 'Distribution', 'SubsetNodes', 'SubsetDistributions', 'Unspecified'|  
|élément location_type|**nvarchar(32)**|Où l’étape est en cours d’exécution.|« Calcul », « Contrôle », « DMS »|  
|status|**nvarchar(32)**|État de cette étape.|En attente, en cours d’exécution, terminé, échec, UndoFailed, PendingCancel, annulé, annulé, abandonnée|  
|error_id|**nvarchar(36)**|Id unique de l’erreur associée à cette étape, le cas échéant.|Consultez ID_erreur de [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). NULL si aucune erreur ne s’est produite.|  
|start_time|**datetime**|Heure de début d’exécution de l’étape.|Plus petit ou égal à l’heure actuelle et supérieur ou égal à end_compile_time de la requête à laquelle appartient cette étape. Pour plus d’informations sur les requêtes, consultez [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|end_time|**datetime**|Heure à laquelle cette étape exécutée avec succès, a été annulée ou a échoué.|Plus petit ou égal à l’heure actuelle et supérieur ou égal à start_time. Pour obtenir des instructions actuellement dans l’exécution de la valeur NULL ou en file d’attente.|  
|total_elapsed_time|**Int**|Durée totale de qu'exécution de l’étape de requête, en millisecondes.|Comprise entre 0 et la différence entre end_time et start_time. 0 pour les étapes en attente.<br /><br /> Si total_elapsed_time dépasse la valeur maximale d’un entier, total_elapsed_time continueront à être la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée. »<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours environ.|  
|row_count|**bigint**|Nombre total de lignes modifiées ou retourné par cette demande.|0 pour les étapes qui ne pas de modification ou de retourner des données. Sinon, d ' nombre de lignes affectées.|  
|commande|**nvarchar(4000)**|Contient le texte complet de la commande de cette étape.|Toute chaîne de requête valide pour une étape. NULL lorsque l’opération est du type MetaDataCreateOperation. Tronquée à 4 000 caractères.|  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section de valeurs de la vue système maximales dans la « Minimum et valeurs maximales » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
