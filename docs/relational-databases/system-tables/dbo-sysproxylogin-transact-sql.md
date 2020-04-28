---
title: dbo. sysproxylogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fb62d70c1b0a41edf684a8216205fb43e070eea
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67984877"
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enregistre les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont associées avec chaque compte proxy de SQL Server Agent. Cette table est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Identificateur du compte proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette valeur correspond à la colonne **proxy_id** de la table **sysproxies** .|  
|**sid**|**varbinary (85)**|Microsoft Windows *security_identifier* pour la connexion SQL Server.|  
|**principal_id**|**int**|ID de l'utilisateur ou du groupe qui a l'autorisation d'utiliser le compte proxy pour une étape du sous-système spécifié.|  
|**flags**|**int**|Type de connexion :<br /><br /> **0** = utilisateur ou groupe Windows, et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion.<br /><br /> **1** =  1[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rôle de système fixe<br /><br /> **2** = rôle de base de données**msdb**|  
  
## <a name="remarks"></a>Notes  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent accéder à cette table.  
  
## <a name="see-also"></a>Voir aussi  
 [dbo. sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
