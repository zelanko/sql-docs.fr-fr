---
title: sys.dm_os_performance_counters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_performance_counters
- sys.dm_os_performance_counters_TSQL
- dm_os_performance_counters_TSQL
- sys.dm_os_performance_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_performance_counters dynamic management view
ms.assetid: a1c3e892-cd48-40d4-b6be-2a9246e8fbff
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dcfe7869767bc9178f9241c3ffa82d166685d7ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62939687"
---
# <a name="sysdmosperformancecounters-transact-sql"></a>sys.dm_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie une ligne par compteur de performance maintenu par le serveur. Pour plus d’informations sur chaque compteur de performance, consultez [utiliser des objets SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).  
  
> [!NOTE]  
>  À appeler à partir [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_performance_counters**.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|Catégorie à laquelle ce compteur appartient.|  
|**counter_name**|**nchar(128)**|Nom du compteur. Pour obtenir plus d’informations sur un compteur, il s’agit du nom de la rubrique à sélectionner à partir de la liste des compteurs dans [utiliser des objets SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md). |  
|**instance_name**|**nchar(128)**|Nom d'une instance particulière du compteur. Contient souvent le nom de la base de données.|  
|**cntr_value**|**bigint**|Valeur actuelle du compteur.<br /><br /> **Remarque :** Pour les compteurs par seconde, cette valeur est cumulative. La valeur de la fréquence doit se calculer en échantillonnant la valeur à des intervalles de temps discrets. La différence entre deux valeurs prélevées successives est égale à la fréquence de l'intervalle de temps utilisé.|  
|**cntr_type**|**Int**|Type de compteur défini par l'architecture de performances Windows. Consultez [Types de compteurs de performances WMI](https://docs.microsoft.com/windows/desktop/WmiSdk/wmi-performance-counter-types) sur Docs ou la documentation de Windows Server pour plus d’informations sur les types de compteurs de performances.|  
|**pdw_node_id**|**Int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="remarks"></a>Notes  
 Si l'instance d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'affiche pas les compteurs de performance du système d'exploitation Windows, utilisez la requête [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante pour vérifier si les compteurs de performance ont été désactivés.  
  
```  
SELECT COUNT(*) FROM sys.dm_os_performance_counters;  
```  
  
 Si la valeur de retour est 0 ligne, cela signifie que les compteurs de performance ont été désactivés. Vous devez alors rechercher dans le journal d'installation l'erreur 3409, « Réinstallez sqlctr.ini pour cette instance et vérifiez que le compte de connexion à l'instance dispose des autorisations de Registre appropriées ».  Ce message indique que les compteurs de performance n'ont pas été activés. Les erreurs qui précèdent immédiatement l'erreur 3409 doivent indiquer la cause première de l'échec d'activation des compteurs de performance. Pour plus d’informations sur les fichiers journaux d’installation, consultez [afficher et lire les fichiers journaux d’installation de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
## <a name="permission"></a>Permission

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
 
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les valeurs des compteurs de performance.  
  
```  
SELECT object_name, counter_name, instance_name, cntr_value, cntr_type  
FROM sys.dm_os_performance_counters;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
  [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  


