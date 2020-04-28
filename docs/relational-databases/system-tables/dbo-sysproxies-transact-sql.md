---
title: dbo. sysproxies (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxies_TSQL
- sysproxies_TSQL
- dbo.sysproxies
- sysproxies
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxies system table
ms.assetid: a73da875-be22-45fc-b5e2-ea7ebd48e2d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1dd486757a912d8f0364f55570a368292cf39ab7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67984894"
---
# <a name="dbosysproxies-transact-sql"></a>dbo.sysproxies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit les attributs d'un compte proxy de l'agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|ID du compte proxy.|  
|**name**|**sysname**|Nom du compte proxy.|  
|**credential_id**|**int**|ID des informations d'identification utilisées par le compte proxy.|  
|**désactivé**|**tinyint**|État du compte proxy :<br /><br /> **0** = désactivé. **1** = activé.|  
|**descriptive**|**nvarchar(512)**|Description entrée par l'utilisateur lors de la création du compte proxy.|  
|**user_sid**|**varbinary (85)**|Microsoft Windows *security_identifier* de l’utilisateur ou du groupe associé aux informations d’identification du proxy.|  
|**credential_date_created**|**datetime**|Date et heure de création des informations d'identification.|  
  
## <a name="remarks"></a>Notes  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent accéder à la table **sysproxies** .  
  
## <a name="see-also"></a>Voir aussi  
 [dbo. sysproxylogin &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)   
 [dbo. sysproxysubsystem &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo. remplir &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)  
  
  
