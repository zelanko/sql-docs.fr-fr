---
title: dbo. remplir (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: ff13af62635273773551ded6df3175bc80157a45
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82806540"
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo.syssubsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [dbo. sysproxysubsystem &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo. sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
