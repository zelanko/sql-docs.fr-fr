---
title: MSsnapshot_agents (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSsnapshot_agents
- MSsnapshot_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshot_agents system table
ms.assetid: aeae0a2e-4c21-4c45-be65-1e426fa52bdd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a0890b30946f2a2033d43712e62fc031fa8451c8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836397"
---
# <a name="mssnapshotagents-transact-sql"></a>MSsnapshot_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsnapshot_agents** table contient une ligne pour chaque Agent d’instantané associé à un serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|ID de l'Agent d'instantané.|  
|**nom**|**nvarchar(100)**|Nom de l'Agent d'instantané.|  
|**publisher_id**|**smallint**|L’ID du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**publication**|**sysname**|Nom de la publication.|  
|**publication_type**|**Int**|Type de publication :<br /><br /> **0** = transactionnelle.<br /><br /> **1** = instantané.<br /><br /> **2** = fusion.|  
|**local_job**|**bit**|Indique s'il existe un travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le serveur de distribution local.|  
|**job_id**|**binary (16)**|Numéro d’identification.|  
|**profile_id**|**Int**|L’ID de configuration à partir de la [MSagent_profiles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) table.|  
|**dynamic_filter_login**|**sysname**|La valeur utilisée pour évaluer la [SUSER_SNAME &#40;Transact-SQL&#41; ](../../t-sql/functions/suser-sname-transact-sql.md) fonction dans les filtres paramétrés qui définissent une partition. Cette colonne est utilisée pour un instantané partitionné.|  
|**dynamic_filter_hostname**|**sysname**|La valeur utilisée pour évaluer la [HOST_NAME &#40;Transact-SQL&#41; ](../../t-sql/functions/host-name-transact-sql.md) fonction dans les filtres paramétrés qui définissent une partition. Cette colonne est utilisée pour un instantané partitionné.|  
|**publisher_security_mode**|**smallint**|Mode de sécurité utilisé par l'agent lors de la connexion au serveur de publication et pouvant prendre la valeur suivante :<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] l’authentification Windows.|  
|**publisher_login**|**sysname**|Nom de connexion utilisé lors de la connexion au serveur de publication.|  
|**publisher_password**|**nvarchar (524)**|Valeur chiffrée du mot de passe utilisée lors de la connexion au serveur de publication.|  
|**job_step_uid**|**uniqueidentifier**|ID unique de l'étape de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle l'Agent est démarré.|  
|**job_login**|**sysname**||  
|**job_password**|**nvarchar (524)**||  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
