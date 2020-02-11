---
title: dbo. sysproxysubsystem (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxysubsystem_TSQL
- dbo.sysproxysubsystem
- sysproxysubsystem_TSQL
- sysproxysubsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxysubsystem system table
ms.assetid: 6d7713f5-1253-4a19-b1fb-635c377c95c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: f3a140a4cf1c82deda3b9d6a15b419b33b411974
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097020"
---
# <a name="dbosysproxysubsystem-transact-sql"></a>dbo.sysproxysubsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enregistre le sous-système de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé par chaque compte proxy. Cette table est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|ID du sous-système. Cette valeur correspond à la colonne **subsystem_id** de la table **remplir** .|  
|**proxy_id**|**int**|ID du compte proxy. Cette valeur correspond à la colonne **proxy_id** de la table **sysproxies** .|  
  
## <a name="remarks"></a>Notes  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent accéder à cette table.  
  
## <a name="see-also"></a>Voir aussi  
 [dbo. remplir &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)   
 [dbo. sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
