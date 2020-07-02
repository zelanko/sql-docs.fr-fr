---
title: Sous-systèmes dbo.sys(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syssubsystems
- syssubsystems
- syssubsystems_TSQL
- dbo.syssubsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syssubsystems system table
ms.assetid: 114b3d55-1ad6-4777-b868-8ef0c86ba596
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4a4374f0ffddb380f56e5c51e26a59e253e7585b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750276"
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo.syssubsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Contient des informations sur tous les sous-systèmes proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibles. La table **remplir** est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|ID du sous-système.|  
|**sous-système**|**nvarchar(40)**|Nom du sous-système.|  
|**description_id**|**int**|ID de message de la ligne dans l’affichage catalogue **sys. messages** qui contient la description du sous-système.|  
|**subsystem_dll**|**nvarchar(255)**|Emplacement de la DLL du sous-système.|  
|**agent_exe**|**nvarchar(255)**|Chemin d'accès complet à l'exécutable qui utilise le sous-système.|  
|**start_entry_point**|**nvarchar(30)**|Fonction appelée lors de l'initialisation du sous-système.|  
|**event_entry_point**|**nvarchar(30)**|Fonction appelée lors de l'exécution d'une étape du sous-système.|  
|**stop_entry_point**|**nvarchar(30)**|Fonction appelée au terme de l'exécution du sous-système.|  
|**max_worker_threads**|**int**|Nombre maximal d'étapes simultanées pour un sous-système donné.|  
  
## <a name="remarks"></a>Remarques  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent accéder à cette table.  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.sysproxysubsystem &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [Proxiesdbo.sys&#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
