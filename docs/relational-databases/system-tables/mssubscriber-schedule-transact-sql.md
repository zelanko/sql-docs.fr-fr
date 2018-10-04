---
title: MSsubscriber_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSsubscriber_schedule
- MSsubscriber_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_schedule system table
ms.assetid: ff428306-0ef4-49a3-b536-07ccdf6e2196
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 91b04c358adcce0aa1cb02b702096d215298a11a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856487"
---
# <a name="mssubscriberschedule-transact-sql"></a>MSsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsubscriber_schedule** table contient des planifications de synchronisation transactionnelle pour chaque paire serveur de publication/abonné et de fusion par défaut. Cette table est stockée dans la base de données de distribution.  
  
> [!NOTE]  
>  Cette table système a été déconseillée et est maintenue pour prendre en charge les versions antérieures de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Le nom du serveur de publication.|  
|**subscriber** (Abonné)|**sysname**|Nom de l'Abonné.|  
|**agent_type**|**smallint**|Type d'Agent:<br /><br /> 0 = Agent de distribution.<br /><br /> 1 = Agent de fusion.|  
|**frequency_type**|**Int**|Fréquence de planification de l'Agent de distribution :<br /><br /> **1** = une fois.<br /><br /> **2** = à la demande.<br /><br /> **4** = quotidienne.<br /><br /> **8** = hebdomadaire.<br /><br /> **16** = mensuelle.<br /><br /> **32** = fréquence mensuelle relative.<br /><br /> **64** = démarrage automatique.<br /><br /> **128** = périodique.|  
|**frequency_interval**|**Int**|La valeur à appliquer à la fréquence définie par **frequency_type**.|  
|**frequency_relative_interval**|**Int**|Date de l'Agent de distribution :<br /><br /> **1** = premier.<br /><br /> **2** = seconde.<br /><br /> **4** = troisième.<br /><br /> **8** = quatrième.<br /><br /> **16** = dernier.|  
|**frequency_recurrence_factor**|**Int**|Facteur de récurrence utilisé par **frequency_type**.|  
|**frequency_subday**|**Int**|Fréquence de replanification nécessaire pendant la période définie :<br /><br /> **1** = une fois.<br /><br /> **2** = seconde.<br /><br /> **4** = minute.<br /><br /> **8** = heure.|  
|**frequency_subday_interval**|**Int**|L’intervalle pour **frequency_subday**.|  
|**active_start_time_of_day**|**Int**|Heure de première planification de l'Agent de distribution, au format HHMMSS.|  
|**active_end_time_of_day**|**Int**|Heure d'arrêt de la planification de l'Agent de distribution, au format HHMMSS.|  
|**active_start_date**|**Int**|Date de première planification de l'Agent de distribution, au format AAAAMMJJ.|  
|**active_end_date**|**Int**|Date d'arrêt de la planification de l'Agent de distribution, au format AAAAMMJJ.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
