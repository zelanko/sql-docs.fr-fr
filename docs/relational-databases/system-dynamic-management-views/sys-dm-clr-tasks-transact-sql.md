---
description: sys.dm_clr_tasks (Transact-SQL)
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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 22066cd2fedee929a5d4047e20e30531728b45bb
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537938"
---
# <a name="sysdm_clr_tasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

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
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l'  **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées au Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

