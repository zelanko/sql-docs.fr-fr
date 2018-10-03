---
title: dbo.sysschedules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysschedules_TSQL
- sysschedules
- sysschedules_TSQL
- dbo.sysschedules
dev_langs:
- TSQL
helpviewer_keywords:
- sysschedules system table
ms.assetid: 4cac9237-7a69-4035-bb3e-928b76aad698
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a1922fd8b9cdfb327186afe453fc1904d698579
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674377"
---
# <a name="dbosysschedules-transact-sql"></a>dbo.sysschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations sur les planifications de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans le **msdb** base de données.  
  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**Int**|ID de la planification de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**schedule_uid**|**uniqueidentifier**|Identificateur unique de la planification du travail. Cette valeur permet d'identifier une planification pour les travaux distribués.|  
|**originating_server_id**|**Int**|ID du serveur principal duquel provient la planification du travail.|  
|**nom**|**sysname (nvarchar(128))**|Nom de la planification du travail défini par l'utilisateur. Ce nom doit être unique au sein d'un travail.|  
|**owner_sid**|**varbinary(85)**|Microsoft Windows *identificateur_sécurisé* de l’utilisateur ou le groupe propriétaire de la planification du travail.|  
|**enabled**|**Int**|État de la planification du travail :<br /><br /> **0** = non activé.<br /><br /> **1** = activé.<br /><br /> Si la planification n'est pas activée, aucun travail n'est exécuté sur la planification.|  
|**freq_type**|**Int**|Fréquence d'exécution d'un travail pour cette planification.<br /><br /> **1** = une seule fois<br /><br /> **4** = quotidienne<br /><br /> **8** = hebdomadaire<br /><br /> **16** = mensuelle<br /><br /> **32** = mensuellement, fonction **freq_interval**<br /><br /> **64** = s’exécute au démarrage du service SQL Server Agent<br /><br /> **128** = s’exécute lorsque l’ordinateur est inactif|  
|**freq_interval**|**Int**|Jours d'exécution du travail. Dépend de la valeur de **freq_type**. La valeur par défaut est **0**, ce qui indique que **freq_interval** n’est pas utilisé. Consultez le tableau ci-dessous pour les valeurs possibles et leurs effets.|  
|**freq_subday_type**|**Int**|Unités pour la **freq_subday_interval**. Voici les valeurs possibles et leurs descriptions.<br /><br /> <br /><br /> **1** : à l’heure spécifiée<br /><br /> **2** : secondes<br /><br /> **4** : minutes<br /><br /> **8** : heures|  
|**freq_subday_interval**|**Int**|Nombre de **freq_subday_type** périodes entre chaque exécution du travail.|  
|**freq_relative_interval**|**Int**|Lorsque **freq_interval** se produit chaque mois, si **freq_interval** est **32** (fréquence mensuelle relative). Il peut s'agir de l'une des valeurs suivantes :<br /><br /> **0** = **freq_relative_interval** n’est pas utilisé<br /><br /> **1** = premier<br /><br /> **2** = seconde<br /><br /> **4** = troisième<br /><br /> **8** = quatrième<br /><br /> **16** = dernier|  
|**freq_recurrence_**<br /><br /> **factor**|**Int**|Nombre de semaines ou mois entre chaque exécution d’une tâche planifiée. **freq_recurrence_factor** est utilisé uniquement si **freq_type** est **8**, **16**, ou **32**. Si cette colonne contient **0**, **freq_recurrence_factor** n’est pas utilisé.|  
|**active_start_date**|**Int**|Date de démarrage de l'exécution d'un travail. La date est au format AAAAMMJJ. NULL indique la date du jour.|  
|**active_end_date**|**Int**|Date d'arrêt de l'exécution d'un travail. La date se présente sous la forme AAAAMMJJ.|  
|**active_start_time**|**Int**|Heure sur n’importe quel jour entre **active_start_date** et **active_end_date** que le travail commence à exécuter. L'heure est au format HHMMSS, exprimée sur 24 h.|  
|**active_end_time**|**Int**|Heure sur n’importe quel jour entre **active_start_date** et **active_end_date** cette tâche arrête l’exécution. L'heure est au format HHMMSS, exprimée sur 24 h.|  
|**date_created**|**datetime**|Date et heure de création de la planification.|  
|**date_modified**|**datetime**|Date et heure de dernière modification de la planification.|  
|**version_number**|**Int**|Numéro de version en cours de la planification. Par exemple, si une planification a été modifiée 10 fois, le **numéro_version** est 10.|  
  
|Valeur de freq_type|Effet sur freq_interval|  
|-------------------------|------------------------------|  
|**1** (une fois)|**freq_interval** n’est pas utilisé (**0**)|  
|**4** (quotidienne)|Chaque **freq_interval** jours|  
|**8** (hebdomadaire)|**freq_interval** prend une ou plusieurs des opérations suivantes :<br /><br /> **1** = dimanche<br /><br /> **2** = lundi<br /><br /> **4** = mardi<br /><br /> **8** = mercredi<br /><br /> **16** = jeudi<br /><br /> **32** = vendredi<br /><br /> **64** = samedi|  
|**16** (mensuellement)|Sur le **freq_interval** jour du mois|  
|**32** (mensuel, relatif)|**freq_interval** est une des opérations suivantes :<br /><br /> **1** = dimanche<br /><br /> **2** = lundi<br /><br /> **3** = mardi<br /><br /> **4** = mercredi<br /><br /> **5** = jeudi<br /><br /> **6** = vendredi<br /><br /> **7** = samedi<br /><br /> **8** = jour<br /><br /> **9** = jour de semaine<br /><br /> **10** = jour de week-end|  
|**64** (lance au démarrage du service SQL Server Agent)|**freq_interval** n’est pas utilisé (**0**)|  
|**128** (s’exécute lorsque l’ordinateur est inactif)|**freq_interval** n’est pas utilisé (**0**)|  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.sysjobschedules &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobschedules-transact-sql.md)  
  
  
