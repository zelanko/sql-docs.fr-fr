---
title: sp_helpdynamicsnapshot_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdynamicsnapshot_TSQL
- sp_helpdynamicsnapshot_job_TSQL
- job_TSQL
- helpdynamicsnapshot
- job
- sp_helpdynamicsnapshot
- sp_helpdynamicsnapshot_job
- helpdynamicsnapshot_TSQL
helpviewer_keywords:
- sp_helpdynamicsnapshot_job
ms.assetid: d6dfdf26-f874-495f-a8a6-8780699646d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cede3c4419f4e11d2110e7c3f735c3dec2474ec4
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531481"
---
# <a name="sphelpdynamicsnapshotjob-transact-sql"></a>sp_helpdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur les travaux d'un Agent qui génèrent des instantanés filtrés. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpdynamicsnapshot_job [ [ @publication = ] 'publication' ]   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]  
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, avec une valeur par défaut **%**, qui retourne des informations sur tous les travaux d’instantané de données filtrées qui correspondent à la chaîne *dynamic_ snapshot_jobid*et *dynamic_snapshot_jobname*pour toutes les publications.  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'` Est le nom d’un travail de capture instantanée de données filtrées. *dynamic_snapshot_jobname*est **sysname**, avec comme valeur par défaut **%**», qui retourne tous les travaux dynamiques d’une publication avec spécifié *dynamic_ snapshot_jobid*. Si aucun nom de travail n'est défini explicitement lors de la création du travail, le nom du travail a le format suivant :  
  
```  
'dyn_' + <name of the standard snapshot job> + <GUID>  
```  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'` Est un identificateur pour un travail d’instantané de données filtrées. *dynamic_snapshot_jobid*est **uniqueidentifier**, avec la valeur NULL par défaut, qui retourne tous les travaux d’instantané qui correspondent à la chaîne *dynamic_snapshot_jobname*.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|Identifie le travail d'instantané de données filtrées.|  
|**job_name**|**sysname**|Nom du travail d'instantané de données filtrées.|  
|**job_id**|**uniqueidentifier**|Identifie le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] travail de l’Agent sur le serveur de distribution.|  
|**dynamic_filter_login**|**sysname**|Valeur utilisée pour évaluer la [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) fonction dans un filtre de lignes paramétrable défini pour la publication.|  
|**dynamic_filter_hostname**|**sysname**|Valeur utilisée pour évaluer la [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) fonction dans un filtre de lignes paramétrable défini pour la publication.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Chemin d'accès au dossier où les fichiers d'instantané sont lus si un filtre de lignes paramétrable est utilisé.|  
|**frequency_type**|**Int**|Fréquence à laquelle l'Agent s'exécute. La valeur peut être l'une des valeur suivantes.<br /><br /> **1** = une fois<br /><br /> **2** = à la demande<br /><br /> **4** = quotidienne<br /><br /> **8** = hebdomadaire<br /><br /> **16** = Monthly<br /><br /> **32** = fréquence mensuelle relative<br /><br /> **64** = démarrage automatique<br /><br /> **128** = périodique|  
|**frequency_interval**|**Int**|Jours d'exécution de l'Agent. La valeur peut être l'une des valeur suivantes.<br /><br /> **1** = dimanche<br /><br /> **2** = lundi<br /><br /> **3** = mardi<br /><br /> **4** = mercredi<br /><br /> **5** = jeudi<br /><br /> **6** = vendredi<br /><br /> **7** = samedi<br /><br /> **8** = jour<br /><br /> **9** = jours de la semaine<br /><br /> **10** = jours de week-end|  
|**frequency_subday_type**|**Int**|Est le type qui définit la fréquence à laquelle l’agent s’exécute lorsque *frequency_type* est **4** (quotidienne), et peut prendre l’une des valeurs suivantes.<br /><br /> **1** = à l’heure spécifiée<br /><br /> **2** = secondes<br /><br /> **4** = minutes<br /><br /> **8** = heures|  
|**frequency_subday_interval**|**Int**|Nombre d’intervalles de *frequency_subday_type* qui se produisent entre chaque exécution planifiée de l’agent.|  
|**frequency_relative_interval**|**Int**|Est la semaine où l’agent s’exécute dans un mois donné lorsque *frequency_type* est **32** (mensuel relatif), et peut prendre l’une des valeurs suivantes.<br /><br /> **1** = premier<br /><br /> **2** = seconde<br /><br /> **4** = troisième<br /><br /> **8** = quatrième<br /><br /> **16** = dernier|  
|**frequency_recurrence_factor**|**Int**|Nombre de semaines ou de mois entre les exécutions planifiées de l'Agent.|  
|**active_start_date**|**Int**|Date de la première exécution planifiée de l'Agent, au format AAAAMMJJ.|  
|**active_end_date**|**Int**|Date de la dernière exécution planifiée de l'Agent, au format AAAAMMJJ.|  
|**active_start_time**|**Int**|Heure de la première exécution planifiée de l'Agent, au format HHMMSS.|  
|**active_end_time**|**Int**|Heure de la dernière exécution planifiée de l'Agent, au format HHMMSS.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpdynamicsnapshot_job** est utilisé dans la réplication de fusion.  
  
 Si toutes les valeurs par défaut des paramètres sont utilisées, les informations sur tous les travaux d'instantané de données partitionnées pour l'ensemble de la base de données de publication sont renvoyées.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe le **db_owner** fixe le rôle de base de données et de la liste d’accès pour la publication peut exécuter **sp_helpdynamicsnapshot_job**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
