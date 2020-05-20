---
title: MSagent_profiles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0e6aa2b9a506f0ad485c4a0eb4dc16960ae44d2a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832341"
---
# <a name="msagent_profiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSagent_profiles** contient une ligne pour chaque profil d’agent de réplication défini. Cette table est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|ID de profil.|  
|**profile_name**|**sysname**|Nom de profil unique pour le type d'agent.|  
|**agent_type**|**int**|Type d'Agent:<br /><br /> **1** = agent d’instantané<br /><br /> **2** = agent de lecture du journal<br /><br /> **3** = agent de distribution<br /><br /> **4** = agent de fusion<br /><br /> **9** = agent de lecture de la file d’attente|  
|**type**|**int**|Type de profil :<br /><br /> **0** = système**1** = personnalisé|  
|**descriptive**|**nvarchar (3000)**|Description du profil.|  
|**def_profile**|**bit**|Indique si ce profil représente le profil par défaut pour ce type d'agent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
