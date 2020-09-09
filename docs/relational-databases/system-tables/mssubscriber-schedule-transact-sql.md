---
description: MSsubscriber_schedule (Transact-SQL)
title: MSsubscriber_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriber_schedule
- MSsubscriber_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_schedule system table
ms.assetid: ff428306-0ef4-49a3-b536-07ccdf6e2196
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6f65d855a118031fd34bcf69257a90bca6e41933
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540885"
---
# <a name="mssubscriber_schedule-transact-sql"></a>MSsubscriber_schedule (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La table **MSsubscriber_schedule** contient les planifications de synchronisation transactionnelle et de fusion par défaut pour chaque paire serveur de publication/abonné. Cette table est stockée dans la base de données de distribution.  
  
> [!NOTE]
>  Cette table système est déconseillée et est en cours de maintenance pour prendre en charge les versions antérieures de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nom du serveur de publication.|  
|**côté**|**sysname**|Nom de l'Abonné.|  
|**agent_type**|**smallint**|Type d'Agent:<br /><br /> 0 = Agent de distribution.<br /><br /> 1 = Agent de fusion.|  
|**frequency_type**|**int**|Fréquence de planification de l'Agent de distribution :<br /><br /> **1** = une fois.<br /><br /> **2** = à la demande.<br /><br /> **4** = tous les jours.<br /><br /> **8** = hebdomadaire.<br /><br /> **16** = mensuelle.<br /><br /> **32** = mensuelle relative.<br /><br /> **64** = démarrage automatique.<br /><br /> **128** = périodique.|  
|**frequency_interval**|**int**|Valeur à appliquer à la fréquence définie par **frequency_type**.|  
|**frequency_relative_interval**|**int**|Date de l'Agent de distribution :<br /><br /> **1** = tout d’abord.<br /><br /> **2** = seconde.<br /><br /> **4** = troisième.<br /><br /> **8** = quatrième.<br /><br /> **16** = dernier.|  
|**frequency_recurrence_factor**|**int**|Facteur de récurrence utilisé par **frequency_type**.|  
|**frequency_subday**|**int**|Fréquence de replanification nécessaire pendant la période définie :<br /><br /> **1** = une fois.<br /><br /> **2** = seconde.<br /><br /> **4** = minute.<br /><br /> **8** = heure.|  
|**frequency_subday_interval**|**int**|Intervalle de **frequency_subday**.|  
|**active_start_time_of_day**|**int**|Heure de première planification de l'Agent de distribution, au format HHMMSS.|  
|**active_end_time_of_day**|**int**|Heure d'arrêt de la planification de l'Agent de distribution, au format HHMMSS.|  
|**active_start_date**|**int**|Date de première planification de l'Agent de distribution, au format AAAAMMJJ.|  
|**active_end_date**|**int**|Date d'arrêt de la planification de l'Agent de distribution, au format AAAAMMJJ.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
