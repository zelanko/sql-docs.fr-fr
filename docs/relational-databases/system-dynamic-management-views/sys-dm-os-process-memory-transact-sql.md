---
title: sys. dm_os_process_memory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_process_memory_TSQL
- dm_os_process_memory_TSQL
- dm_os_process_memory
- sys.dm_os_process_memory
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_process_memory dynamic management view
ms.assetid: e838130c-95d4-4605-9e3b-eb0ab71cd250
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fcbab4d5dc1bbc86fe9083e9c3407749040a0023
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265702"
---
# <a name="sysdm_os_process_memory-transact-sql"></a>sys.dm_os_process_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  La plupart des allocations de mémoire qui sont attribuées à l'espace du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont contrôlées par le biais d'interfaces qui permettent le suivi et la comptabilité de ces allocations. Toutefois, les allocations de mémoire peuvent être effectuées dans l'espace d'adressage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ignore les routines de gestion de la mémoire interne. Les valeurs sont obtenues par le biais d'appels au système d'exploitation de base. Elles ne sont pas manipulées par des méthodes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]internes à, sauf lorsqu’elles s’adaptent aux allocations de pages verrouillées ou volumineuses.  
  
 Toutes les valeurs retournées qui indiquent des tailles de mémoire sont affichées en kilo-octets (Ko). La **total_virtual_address_space_reserved_kb** de colonne est un doublon de **virtual_memory_in_bytes** à partir de **sys. dm_os_sys_info**.  
  
 Le tableau suivant fournit une illustration complète de l'espace d'adressage de processus.  
  
> [!NOTE]  
>  Pour appeler cette valeur [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] à [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]partir de ou, utilisez le nom **sys. dm_pdw_nodes_os_process_memory**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**physical_memory_in_use_kb**|**bigint**|Indique le travail de processus en Ko, tel que signalé par le système d'exploitation, ainsi que les allocations faisant l'objet d'un suivi effectuées à l'aide d'API de pages de grande taille. N'accepte pas la valeur NULL.|  
|**large_page_allocations_kb**|**bigint**|Spécifie la mémoire physique qui est allouée en utilisant des API de pages de grande taille. N'accepte pas la valeur NULL.|  
|**locked_page_allocations_kb**|**bigint**|Spécifie des pages mémoire verrouillées en mémoire. N'accepte pas la valeur NULL.|  
|**total_virtual_address_space_kb**|**bigint**|Indique la taille totale de la partie mode utilisateur de l'espace d'adressage virtuel. N'accepte pas la valeur NULL.|  
|**virtual_address_space_reserved_kb**|**bigint**|Indique la quantité totale d'espace d'adressage virtuel réservée par le processus. N'accepte pas la valeur NULL.|  
|**virtual_address_space_committed_kb**|**bigint**|Indique la quantité d'espace d'adressage virtuel réservée qui a été validée ou mappée aux pages physiques. N'accepte pas la valeur NULL.|  
|**virtual_address_space_available_kb**|**bigint**|Indique la quantité d'espace d'adressage virtuel qui est actuellement disponible. N'accepte pas la valeur NULL.<br /><br /> **Remarque :** Les régions libres qui sont plus petites que la granularité d’allocation peuvent exister. Ces régions ne sont pas disponibles pour les allocations.|  
|**page_fault_count**|**bigint**|Indique le nombre de défauts de page qui sont générés par le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N'accepte pas la valeur NULL.|  
|**memory_utilization_percentage**|**int**|Spécifie le pourcentage de mémoire validée qui se trouve dans la plage de travail. N'accepte pas la valeur NULL.|  
|**available_commit_limit_kb**|**bigint**|Indique la quantité de mémoire disponible pour être validée par le processus. N'accepte pas la valeur NULL.|  
|**process_physical_memory_low**|**bit**|Indique que le processus répond à une notification de mémoire physique insuffisante. N'accepte pas la valeur NULL.|  
|**process_virtual_memory_low**|**bit**|Indique qu'une condition de mémoire virtuelle insuffisante a été détectée. N'accepte pas la valeur NULL.|  
|**pdw_node_id**|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="permissions"></a>Autorisations  
 Sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite l'autorisation VIEW SERVER STATE sur le serveur.  
  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   
  
## <a name="see-also"></a>Voir aussi  
 [Vues et fonctions de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server vues de gestion dynamique liées au système d’exploitation &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


