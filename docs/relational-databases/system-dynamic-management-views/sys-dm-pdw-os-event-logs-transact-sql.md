---
title: sys.dm_pdw_os_event_logs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 44a24b12c284cf253838bc1c2252e4081b8efe98
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58657233"
---
# <a name="sysdmpdwoseventlogs-transact-sql"></a>sys.dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations concernant l’événement Windows différents journaux sur les différents nœuds.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**Int**|Nœud d’appliance que provient ce journal.<br /><br /> pdw_node_id et nom_journal forment la clé pour cette vue.||  
|log_name|**nvarchar(255)**|Nom du journal des événements Windows.<br /><br /> pdw_node_id et nom_journal forment la clé pour cette vue.||  
|log_source|**nvarchar(255)**|Nom de source de journal des événements Windows.||  
|event_id|**Int**|ID de l’événement. N’est pas unique.||  
|event_type|**nvarchar(255)**|Type de l’événement, en identifiant la gravité.|« Informations », « Avertissement », « Erreur »|  
|event_message|**nvarchar(4000)**|Détails de l’événement.||  
|generate_time|**datetime**|Heure de que création de l’événement.||  
|write_time|**datetime**|Heure de que l’événement a été réellement écrits dans le journal.||  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section de métadonnées dans le [limites de capacité](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) rubrique. 
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
