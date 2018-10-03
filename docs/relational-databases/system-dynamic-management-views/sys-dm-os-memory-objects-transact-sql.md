---
title: Sys.dm_os_memory_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_memory_objects
- sys.dm_os_memory_objects
- sys.dm_os_memory_objects_TSQL
- dm_os_memory_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_objects dynamic management view
ms.assetid: 5688bcf8-5da9-4ff9-960b-742b671d7096
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fc006a940318ba84c3670ed9d10b96f728219668
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800647"
---
# <a name="sysdmosmemoryobjects-transact-sql"></a>sys.dm_os_memory_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne des objets mémoire qui sont actuellement alloués par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez utiliser **sys.dm_os_memory_objects** pour analyser l’utilisation de mémoire et identifient la mémoire possible fuites.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**memory_object_address**|**varbinary(8)**|Adresse de l'objet mémoire. N'accepte pas la valeur NULL.|  
|**parent_address**|**varbinary(8)**|Adresse de l'objet mémoire parent. Autorise la valeur NULL.|  
|**pages_allocated_count**|**Int**|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Nombre de pages allouées par cet objet. N'accepte pas la valeur NULL.|  
|**pages_in_bytes**|**bigint**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Quantité de mémoire, en octets, allouée par cette instance de l'objet mémoire. N'accepte pas la valeur NULL.|  
|**creation_options**|**Int**|À usage interne uniquement Autorise la valeur NULL.|  
|**bytes_used**|**bigint**|À usage interne uniquement Autorise la valeur NULL.|  
|**type**|**nvarchar(60)**|Type d'objet mémoire.<br /><br /> Indique le composant auquel cet objet mémoire appartient ou la fonction de l'objet mémoire. Autorise la valeur NULL.|  
|**nom**|**varchar(128)**|À usage interne uniquement Autorise la valeur Null.|  
|**memory_node_id**|**smallint**|ID d'un nœud de mémoire utilisé par cet objet mémoire. N'accepte pas la valeur NULL.|  
|**creation_time**|**datetime**|À usage interne uniquement Autorise la valeur NULL.|  
|**max_pages_allocated_count**|**Int**|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Nombre maximum de pages allouées par cet objet mémoire. N'accepte pas la valeur NULL.|  
|**page_size_in_bytes**|**Int**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Taille des pages, en octets, allouée par cet objet. N'accepte pas la valeur NULL.|  
|**max_pages_in_bytes**|**bigint**|Quantité de mémoire maximale utilisée par cet objet mémoire. N'accepte pas la valeur NULL.|  
|**page_allocator_address**|**varbinary(8)**|Adresse mémoire de l'allocateur de page. N'accepte pas la valeur NULL. Pour plus d’informations, consultez [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**creation_stack_address**|**varbinary(8)**|À usage interne uniquement Autorise la valeur NULL.|  
|**sequence_num**|**Int**|À usage interne uniquement Autorise la valeur NULL.|  
|**partition_type**|**Int**|Le type de partition :<br /><br /> 0 - objet de mémoire non configurables en partition<br /><br /> 1 - objet de mémoire configurables en partition, actuellement ne pas partitionnée<br /><br /> 2 - objet de mémoire configurables en partition, partitionné par nœud NUMA. Dans un environnement avec un seul nœud NUMA, cela équivaut à 1.<br /><br /> 3 - objet configurables en partition mémoire partitionné par UC.|  
|**contention_factor**|**real**|Valeur spécifiant la contention sur cet objet mémoire, avec 0, ce qui signifie qu’aucun conflit. La valeur est mise à jour chaque fois qu’un nombre spécifié d’allocations de mémoire ont été apportée à une contention réfléchissante pendant cette période. S’applique uniquement aux objets de mémoire thread-safe.|  
|**waiting_tasks_count**|**bigint**|Nombre d’attentes sur cet objet mémoire. Ce compteur est incrémenté chaque fois que la mémoire est allouée à partir de cet objet mémoire. L’incrément est le nombre de tâches en attente pour l’accès à cet objet mémoire. S’applique uniquement aux objets de mémoire thread-safe. Il s’agit d’un meilleur effort sans garantie d’exactitude.|  
|**exclusive_access_count**|**bigint**|Spécifie la fréquence à laquelle cet objet mémoire était accessible exclusivement. S’applique uniquement aux objets de mémoire thread-safe.  Il s’agit d’un meilleur effort sans garantie d’exactitude.|  
|**pdw_node_id**|**Int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
 **partition_type**, **contention_factor**, **waiting_tasks_count**, et **exclusive_access_count** ne sont pas encore implémentées dans [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
## <a name="permissions"></a>Permissions

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   

## <a name="remarks"></a>Notes  
 Les objets mémoire sont des segments. Ils fournissent des allocations qui ont une granularité plus fine que celles fournies par les régisseurs de mémoire. Les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent des objets mémoire au lieu de régisseurs de mémoire. Les objets mémoire utilisent l'interface d'allocation de page du régisseur de mémoire pour allouer les pages. Ils n'utilisent pas les interfaces de mémoire virtuelle ou partagée. Selon les modèles d'allocation, les composants peuvent créer différents types d'objets mémoire pour allouer des régions de taille arbitraire.  
  
 La taille de page type pour un objet mémoire est de 8 Ko. Toutefois, les objets mémoire incrémentiels peuvent avoir des tailles de page allant de 512 octets à 8 Ko.  
  
> [!NOTE]  
>  La taille de page n'est pas une allocation maximale. Il s'agit en fait de granularité d'allocation prise en charge par un allocateur de page et mise en œuvre par un régisseur de mémoire. Vous pouvez demander des allocations supérieures à 8 Ko d'objets mémoire.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne la quantité de mémoire allouée par chaque type d'objet mémoire.  
  
```  
SELECT SUM (pages_in_bytes) as 'Bytes Used', type   
FROM sys.dm_os_memory_objects  
GROUP BY type   
ORDER BY 'Bytes Used' DESC;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
  [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)  
  
  


