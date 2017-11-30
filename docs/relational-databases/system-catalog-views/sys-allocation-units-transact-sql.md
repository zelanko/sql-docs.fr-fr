---
title: Sys.allocation_units (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.allocation_units_TSQL
- sys.allocation_units
- allocation_units_TSQL
- allocation_units
dev_langs: TSQL
helpviewer_keywords: sys.allocation_units catalog view
ms.assetid: ec9de780-68fd-4551-b70b-2d3ab3709b3e
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ae268f41550268aab1afb03b587d2fd5e735e911
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="sysallocationunits-transact-sql"></a>sys.allocation_units (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contient une ligne pour chaque unité d'allocation de la base de données.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|allocation_unit_id|**bigint**|Identificateur de l'unité d'allocation. Unique dans une base de données.|  
|Type|**tinyint**|Type de l'unité d'allocation :<br /><br /> 0 = Supprimée<br /><br /> 1 = Données dans les lignes (tous types de données à l'exception du type LOB)<br /><br /> 2 = les données LOB (large object) (**texte**, **ntext**, **image**, **xml**, types de valeur élevée et les types CLR définis par l’utilisateur)<br /><br /> 3 = Données en dépassement de capacité des lignes|  
|type_desc|**nvarchar (60)**|Description du type d'unité d'allocation :<br /><br /> **SUPPRIMÉ**<br /><br /> **IN_ROW_DATA**<br /><br /> **LOB_DATA**<br /><br /> **ROW_OVERFLOW_DATA**|  
|container_id|**bigint**|ID du conteneur de stockage associé à l'unité d'allocation.<br /><br /> Si type est égal à 1 ou à 3, container_id = sys.partitions.hobt_id.<br /><br /> Si le type est égal à 2, container_id = sys.partitions.partition_id.<br /><br /> 0 = Unité d'allocation marquée pour suppression différée.|  
|data_space_id|**int**|ID du groupe de fichiers dans lequel se trouve cette unité d'allocation.|  
|total_pages|**bigint**|Nombre total de pages allouées ou réservées par cette unité d'allocation.|  
|used_pages|**bigint**|Nombre total de pages en cours d'utilisation.|  
|data_pages|**bigint**|Nombre de pages utilisées qui comportent :<br /><br /> Données dans la ligne (In-row data)<br /><br /> Données LOB (LOB data)<br /><br /> Données de dépassement de ligne (Row-overflow data)<br /><br /> <br /><br /> Notez que la valeur retournée exclut les pages d’index interne et les pages de gestion des allocations.|  
  
> [!NOTE]  
>  Lorsque vous supprimez ou reconstruisez des index volumineux ou lorsque vous supprimez ou tronquez des tables volumineuses, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] diffère les désallocations des pages actives et de leurs blocs associés jusqu'à ce que la transaction soit validée. Les opérations de suppression différées ne libèrent pas immédiatement l'espace alloué. Par conséquent, il se peut que les valeurs renvoyées par sys.allocation_units immédiatement après la suppression ne reflètent pas l'espace disque réellement disponible.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
