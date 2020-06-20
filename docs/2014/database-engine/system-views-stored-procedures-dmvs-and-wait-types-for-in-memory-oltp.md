---
title: Vues système, procédures stockées, DMV et types d’attente pour l’OLTP en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: efaa59e3-dbfa-407f-b1aa-cb0c6602ea17
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f15e1e55f0646f2cd42fe5a7154a606684961af
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928430"
---
# <a name="system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp"></a>Vues système, procédures stockées, DMV et types d’attente pour l’OLTP en mémoire
  Cette rubrique fournit de brèves descriptions et des liens vers de nombreux objets de base de données qui prennent en charge OLTP en mémoire.  
  
### <a name="system-views"></a>Vues système  
  
|Affichage système|Description|Fonctionnalité OLTP en mémoire|  
|-----------------|-----------------|-----------------------------|  
|[sys.data_spaces &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-data-spaces-transact-sql)|Vérifiez si un groupe de fichiers contient des données optimisées en mémoire.|Les colonnes suivantes affichent des valeurs supplémentaires : **type** et **type_desc**.|  
|[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)|Vérifiez si un index est une table optimisée en mémoire.|Les colonnes suivantes affichent des valeurs supplémentaires : **type** et **type_desc**.|  
|[sys.parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql)|Vérifiez si un paramètre n'accepte pas la valeur null (pour une exécution plus efficace des procédures stockées compilées en mode natif).|**IS_NULLABLE** colonne.|  
|[sys. all_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql)|Vérifiez si une procédure stockée est compilée en mode natif.|**uses_native_compilation** colonne.|  
|[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)|Vérifiez si une procédure stockée est compilée en mode natif.|**uses_native_compilation** colonne.|  
|[sys. table_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-table-types-transact-sql)|Vérifiez si une table est optimisée en mémoire.|**is_memory_optimized** colonne.|  
|[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|Vérifiez si une table est optimisée en mémoire et vérifiez le paramètre de durabilité d’une table.|les colonnes **durabilité**, **durability_desc**et **is_memory_optimized** .|  
|[sys.hash_indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-hash-indexes-transact-sql)|Affichez les index de hachage d'une table optimisée en mémoire.|OLTP en mémoire spécifique.|  
  
### <a name="metadata-functions"></a>Fonctions de métadonnées  
  
|Fonction de métadonnées|Description|Fonctionnalité OLTP en mémoire|  
|-----------------------|-----------------|-----------------------------|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)|Vérifiez si les objets de base de données sont optimisés en mémoire.|Propriétés **ExecIsWithNativeCompilation** et **TableIsMemoryOptimized** .<br /><br /> La propriété **IsSchemaBound** prend en charge le type d’objet Procedure (retourne 0 pour les procédures au lieu de null).|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)|Vérifiez si un serveur prend en charge OLTP en mémoire.|Propriété **IsXTPSupported** .|  
  
### <a name="system-stored-procedures"></a>Procédures stockées système  
  
|Procédure stockée|Description|  
|----------------------|-----------------|  
|[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql)|Liez une base de données OLTP en mémoire à un pool de ressources.|  
|[sys. sp_xtp_checkpoint_force_garbage_collection &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-checkpoint-force-garbage-collection-transact-sql)|Initialisez le garbage collection sur une base de données OLTP en mémoire.|  
|[sys. sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql)|Activez la collection de statistiques pour les procédures stockées compilées en mode natif.|  
|[sys. sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql)|Activez la collection de statistiques par requête pour les procédures stockées compilées en mode natif.|  
|[sys. sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)|Fusionnez les fichiers de données et les fichiers delta.|  
|[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)|Supprimez la liaison entre une base de données et un pool de ressources.|  
  
## <a name="dynamic-management-views-dmvs"></a>Vues de gestion dynamique  
 Il existe plusieurs vues de gestion dynamique des tables optimisées en mémoire.  
  
 Pour plus d’informations, consultez [vues de gestion dynamique des tables à mémoire optimisée &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql).  
  
## <a name="wait-types"></a>Type d’attente  
 Il existe plusieurs types d'attente qui prennent en charge OLTP en mémoire.  
  
 Pour plus d’informations, consultez les types d’attente qui ont le préfixe **WAIT_XTP**et **XTPPROC** dans la rubrique [sys. dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql) .  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;de l’optimisation en mémoire de l’OLTP en mémoire&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [Prise en charge d'OLTP en mémoire par Transact-SQL](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
