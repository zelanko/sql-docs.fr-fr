---
title: sys. dm_os_memory_cache_clock_hands (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_clock_hands_TSQL
- dm_os_memory_cache_clock_hands
- dm_os_memory_cache_clock_hands_TSQL
- sys.dm_os_memory_cache_clock_hands
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_clock_hands dynamic management view
ms.assetid: 0660eddc-691c-425f-9d43-71151d644de7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 783f985810b44673c6a6566caa6e89ff655670e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265790"
---
# <a name="sysdm_os_memory_cache_clock_hands-transact-sql"></a>sys.dm_os_memory_cache_clock_hands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le statut de chaque aiguille d'une horloge de cache spécifique.  
  
> [!NOTE]  
>  Pour appeler cette valeur [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] à [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]partir de ou, utilisez le nom **sys. dm_pdw_nodes_os_memory_cache_clock_hands**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary (8)**|Adresse du cache associé à l'horloge. N'accepte pas la valeur NULL.|  
|**nomme**|**nvarchar (256)**|Nom du cache. N'accepte pas la valeur NULL.|  
|**entrer**|**nvarchar (60)**|Type de cache. Il peut exister plusieurs caches du même type. N'accepte pas la valeur NULL.|  
|**clock_hand**|**nvarchar (60)**|Type d'aiguille. Il s’agit de l’un des éléments suivants :<br /><br /> Externe<br /><br /> Interne<br /><br /> N'accepte pas la valeur NULL.|  
|**clock_status**|**nvarchar (60)**|Statut de l'horloge. Il s’agit de l’un des éléments suivants :<br /><br /> Suspended<br /><br /> Exécution en cours<br /><br /> N'accepte pas la valeur NULL.|  
|**rounds_count**|**bigint**|Nombre de balayages effectués sur le cache pour supprimer des entrées. N'accepte pas la valeur NULL.|  
|**removed_all_rounds_count**|**bigint**|Nombre d'entrées supprimées par tous les balayages. N'accepte pas la valeur NULL.|  
|**updated_last_round_count**|**bigint**|Nombre d'entrées mises à jour lors du dernier balayage. N'accepte pas la valeur NULL.|  
|**removed_last_round_count**|**bigint**|Nombre d'entrées supprimées lors du dernier balayage. N'accepte pas la valeur NULL.|  
|**last_tick_time**|**bigint**|Heure, en millisecondes, du dernier mouvement de l'aiguille de l'horloge. N'accepte pas la valeur NULL.|  
|**round_start_time**|**bigint**|Heure, en millisecondes, du balayage précédent. N'accepte pas la valeur NULL.|  
|**last_round_start_time**|**bigint**|Durée totale, en millisecondes, du précédent cycle d'horloge. N'accepte pas la valeur NULL.|  
|**pdw_node_id**|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="permissions"></a>Autorisations  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   
  
## <a name="remarks"></a>Notes  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stocke des informations en mémoire dans une structure appelée un cache mémoire. Les informations stockées dans le cache peuvent être des données, des entrées d'index, des plans de procédures compilées et divers autres types d'informations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour éviter d'avoir à recréer ces informations, celles-ci sont conservées aussi longtemps que possible dans le cache mémoire et sont généralement supprimées du cache lorsqu'elles sont trop anciennes pour être utiles ou lorsqu'il est nécessaire de libérer l'espace mémoire pour stocker de nouvelles informations. Le processus de suppression des anciennes informations s'appelle un balayage mémoire. Le balayage mémoire est une activité fréquente, mais pas continue. Un algorithme d'horloge contrôle le balayage du cache mémoire. Chaque horloge peut contrôler plusieurs balayages mémoire, qui sont appelés des aiguilles. L'aiguille de l'horloge du cache mémoire correspond à l'emplacement actuel de l'une des aiguilles d'un balayage mémoire.  

## <a name="see-also"></a>Voir aussi  
 [SQL Server vues de gestion dynamique liées au système d’exploitation &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
 [sys. dm_os_memory_cache_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)
  

