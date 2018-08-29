---
title: sp_add_agent_parameter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_add_agent_parameter_TSQL
- sp_add_agent_parameter
helpviewer_keywords:
- sp_add_agent_parameter
ms.assetid: 055f4765-0574-47c3-bf7d-6ef6e9bd8b34
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b3947425e84734fcdd5920cac5b097426e252cb3
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43026747"
---
# <a name="spaddagentparameter-transact-sql"></a>sp_add_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un nouveau paramètre et sa valeur au profil d'un agent. Cette procédure stockée est exécutée sur le serveur de distribution sur une base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_agent_parameter [ @profile_id = ] profile_id  
        , [ @parameter_name = ] 'parameter_name'   
        , [ @parameter_value = ] 'parameter_value'   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@profile_id=** ] *profile_id*  
 Est l’ID du profil à partir de la **MSagent_profiles** table dans le **msdb** base de données. *profile_id* est **int**, sans valeur par défaut.  
  
 Pour savoir de quel type d’agent cela *profile_id* représente, recherchez le *profile_id* dans le [MSagent_profiles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) table et notez le *agent_type* valeur du champ. Les valeurs sont les suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Agent d'instantané|  
|**2**|l'Agent de lecture du journal ;|  
|**3**|Agent de distribution|  
|**4**|Agent de fusion|  
|**9**|Agent de lecture de la file d'attente|  
  
 [  **@parameter_name=** ] **'***nom_paramètre***'**  
 Est le nom du paramètre. *parameter_name* est **sysname**, sans valeur par défaut. Pour obtenir la liste des paramètres déjà définis dans les profils système, consultez [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md). Pour obtenir la liste complète des paramètres valides pour chaque agent, consultez les rubriques suivantes :  
  
-   [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Agent de lecture du journal des réplications](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Agent de fusion de réplication](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Agent de lecture de la file d’attente de réplication](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 [  **@parameter_value=**] **'***parameter_value***'**  
 Valeur à affecter au paramètre. *parameter_value* est **nvarchar (255)**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_add_agent_parameter** est utilisé dans la réplication de capture instantanée, la réplication transactionnelle et la réplication de fusion.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_add_agent_parameter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des profils d’Agent de réplication](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Profils de l’Agent de réplication](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_change_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_change_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)  
  
  
