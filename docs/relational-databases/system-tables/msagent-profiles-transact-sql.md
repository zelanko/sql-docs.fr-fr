---
title: MSagent_profiles (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs: TSQL
helpviewer_keywords: MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a5423c227bd16008e08bc3a70f25dd899e392f5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="msagentprofiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSagent_profiles** table contient une ligne pour chaque profil d’agent de réplication défini. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|ID de profil.|  
|**profile_name**|**sysname**|Nom de profil unique pour le type d'agent.|  
|**agent_type**|**int**|Type d'Agent:<br /><br /> **1** = Agent de capture instantanée<br /><br /> **2** = Agent de lecture du journal<br /><br /> **3** = Agent de distribution<br /><br /> **4** = Agent de fusion<br /><br /> **9** = Agent de lecture de file d’attente|  
|**type**|**int**|Type de profil :<br /><br /> **0** = système**1** = personnalisé|  
|**Description**|**nvarchar (3000)**|La description du profil.|  
|**def_profile**|**bit**|Indique si ce profil représente le profil par défaut pour ce type d'agent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
