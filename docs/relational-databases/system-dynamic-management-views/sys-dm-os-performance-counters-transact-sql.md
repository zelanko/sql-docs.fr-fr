---
title: sys. dm_os_performance_counters (Transact-SQL) | Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5c7b4d78f73af003e93bc662f10f1f95acda2b6a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265710"
---
# <a name="sysdm_os_performance_counters-transact-sql"></a>sys.dm_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie une ligne par compteur de performance maintenu par le serveur. Pour plus d’informations sur chaque compteur de performance, consultez [utiliser des objets SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).  
  
> [!NOTE]  
>  Pour appeler cette valeur [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] à [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]partir de ou, utilisez le nom **sys. dm_pdw_nodes_os_performance_counters**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar (128)**|Catégorie à laquelle ce compteur appartient.|  
|**counter_name**|**nchar (128)**|Nom du compteur. Pour obtenir plus d’informations sur un compteur, il s’agit du nom de la rubrique à sélectionner dans la liste des compteurs [utilisés SQL Server objets](../../relational-databases/performance-monitor/use-sql-server-objects.md). |  
|**instance_name**|**nchar (128)**|Nom d'une instance particulière du compteur. Contient souvent le nom de la base de données.|  
|**cntr_value**|**bigint**|Valeur actuelle du compteur.<br /><br /> **Remarque :** Pour les compteurs par seconde, cette valeur est cumulative. La valeur de la fréquence doit se calculer en échantillonnant la valeur à des intervalles de temps discrets. La différence entre deux valeurs prélevées successives est égale à la fréquence de l'intervalle de temps utilisé.|  
|**cntr_type**|**int**|Type de compteur défini par l'architecture de performances Windows. Pour plus d’informations sur les types de compteurs de performance, consultez [types de compteurs de performance WMI](https://docs.microsoft.com/windows/desktop/WmiSdk/wmi-performance-counter-types) sur docs ou la documentation de Windows Server.|  
|**pdw_node_id**|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="remarks"></a>Notes  
 Si l'instance d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'affiche pas les compteurs de performance du système d'exploitation Windows, utilisez la requête [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante pour vérifier si les compteurs de performance ont été désactivés.  
  
```  
SELECT COUNT(*) FROM sys.dm_os_performance_counters;  
```  
  
 Si la valeur de retour est 0 ligne, cela signifie que les compteurs de performance ont été désactivés. Vous devez alors rechercher dans le journal d'installation l'erreur 3409, « Réinstallez sqlctr.ini pour cette instance et vérifiez que le compte de connexion à l'instance dispose des autorisations de Registre appropriées ».  Ce message indique que les compteurs de performance n'ont pas été activés. Les erreurs qui précèdent immédiatement l'erreur 3409 doivent indiquer la cause première de l'échec d'activation des compteurs de performance. Pour plus d’informations sur les fichiers journaux d’installation, consultez [afficher et lire SQL Server fichiers journaux d’installation](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
## <a name="permission"></a>Autorisation

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   
 
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les valeurs des compteurs de performance.  
  
```  
SELECT object_name, counter_name, instance_name, cntr_value, cntr_type  
FROM sys.dm_os_performance_counters;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
  [SQL Server vues de gestion dynamique liées au système d’exploitation &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  


