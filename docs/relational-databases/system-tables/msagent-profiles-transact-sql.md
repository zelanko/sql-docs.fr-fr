---
title: MSagent_profiles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c7e5033c5fd66141a7d6bc656f33dd5720bae016
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700397"
---
# <a name="msagentprofiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSagent_profiles** table contient une ligne pour chaque profil d’agent de réplication défini. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**Int**|ID de profil.|  
|**nom_profil**|**sysname**|Nom de profil unique pour le type d'agent.|  
|**agent_type**|**Int**|Type d'Agent:<br /><br /> **1** = Agent d’instantané<br /><br /> **2** = Agent de lecture du journal<br /><br /> **3** = Agent de distribution<br /><br /> **4** = Agent de fusion<br /><br /> **9** = Agent de lecture de file d’attente|  
|**type**|**Int**|Type de profil :<br /><br /> **0** = system**1** = personnalisé|  
|**description**|**nvarchar(3000)**|La description du profil.|  
|**def_profile**|**bit**|Indique si ce profil représente le profil par défaut pour ce type d'agent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
