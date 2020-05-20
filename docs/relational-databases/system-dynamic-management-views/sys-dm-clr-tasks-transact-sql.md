---
title: sys. dm_clr_tasks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8a4726504794c70909664633168bfc3730ff65c7
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824704"
---
# <a name="sysdm_clr_tasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour toutes les tâches CLR (Common Language Runtime) en cours d'exécution. Un traitement [!INCLUDE[tsql](../../includes/tsql-md.md)] qui contient une référence à une routine CLR crée une tâche distincte pour exécuter l'ensemble du code managé de ce traitement. Les diverses instructions du traitement qui nécessitent l'exécution de code managé utilisent la même tâche CLR. Cette tâche CLR est chargée de tenir à jour les objets et les états liés à l'exécution du code managé, mais aussi les transitions entre l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le CLR.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary (8)**|Adresse de la tâche CLR.|  
|**sos_task_address**|**varbinary (8)**|Adresse de la tâche du traitement [!INCLUDE[tsql](../../includes/tsql-md.md)] sous-jacent.|  
|**appdomain_address**|**varbinary (8)**|Adresse du domaine d'application dans lequel cette tâche s'exécute.|  
|**state**|**nvarchar(128)**|État actuel de la tâche.|  
|**abort_state**|**nvarchar(128)**|État actuel de la procédure d'annulation (si la tâche a été annulée). L'abandon d'une tâche passe par plusieurs états.|  
|**type**|**nvarchar(128)**|Type de tâche.|  
|**affinity_count**|**int**|Affinité de la tâche.|  
|**forced_yield_count**|**int**|Nombre de fois où la tâche a dû être abandonnée.|  
  
## <a name="permissions"></a>Autorisations  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , requiert l' `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   
  
## <a name="see-also"></a>Voir aussi  
 [Vues et fonctions de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées au Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

