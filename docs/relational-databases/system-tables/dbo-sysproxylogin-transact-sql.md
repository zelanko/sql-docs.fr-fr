---
title: dbo.sysproxylogin (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs: TSQL
helpviewer_keywords: sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5301ed0231793f50be14f536cd36ff2f5010df78
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enregistre les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont associées avec chaque compte proxy de SQL Server Agent. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Identificateur du compte proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette valeur correspond à la **proxy_id** colonne dans la **sysproxies** table.|  
|**SID**|**varbinary(85)**|Microsoft Windows *identificateur_sécurisé* pour la connexion SQL Server.|  
|**principal_id**|**int**|ID de l'utilisateur ou du groupe qui a l'autorisation d'utiliser le compte proxy pour une étape du sous-système spécifié.|  
|**indicateurs**|**int**|Type de connexion :<br /><br /> **0** = utilisateur Windows ou un groupe, et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion.<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rôle de système fixe<br /><br /> **2** = **msdb** rôle de base de données|  
  
## <a name="remarks"></a>Notes  
 Seuls les membres de la **sysadmin** rôle serveur fixe peut accéder à cette table.  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.sysproxies &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
