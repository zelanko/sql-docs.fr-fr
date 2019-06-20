---
title: sp_enum_sqlagent_subsystems (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_sqlagent_subsystems
- sp_enum_sqlagent_subsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_sqlagent_subsystems
ms.assetid: 019a3c9d-bac3-495b-a70a-2c19f1d2e20e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5aac3e1471f969ea324008c03f97b9b26c05c4ec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62445578"
---
# <a name="spenumsqlagentsubsystems-transact-sql"></a>sp_enum_sqlagent_subsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Énumère les sous-systèmes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_enum_sqlagent_subsystems  
```  
  
## <a name="arguments"></a>Arguments  
 None  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**subsystem**|**nvarchar(40)**|Nom du sous-système.|  
|**description**|**nvarchar(512)**|Description du sous-système.|  
|**subsystem_dll**|**nvarchar(510)**|Module DLL qui contient le sous-système.|  
|**agent_exe**|**nvarchar(510)**|Module exécutable utilisé par le sous-système.|  
|**start_entry_point**|**nvarchar(30)**|Procédure appelée par l'Agent SQL Server pendant l'exécution d'une étape du travail.|  
|**event_entry_point**|**nvarchar(30)**|Procédure appelée par l'Agent SQL Server pendant l'exécution d'une étape du travail.|  
|**stop_entry_point**|**nvarchar(30)**|Procédure appelée par l'Agent SQL Server pendant l'exécution d'une étape du travail.|  
|**max_worker_threads**|**Int**|Nombre maximal de threads que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] va démarrer pour ce sous-système.|  
|**subsystem_id**|**Int**|Identificateur pour le sous-système.|  
  
## <a name="remarks"></a>Notes  
 Cette procédure énumère les sous-systèmes disponibles dans l'instance.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
 Pour plus d’informations sur **SQLAgentOperatorRole**, consultez [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter la sécurité SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
  
