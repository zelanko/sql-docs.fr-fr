---
title: sp_drop_agent_parameter (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_drop_agent_parameter_TSQL
- sp_drop_agent_parameter
helpviewer_keywords: sp_drop_agent_parameter
ms.assetid: b99e65ff-9cca-4dce-a2ce-2968de23a76a
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4494d694c3bfb649649c65909e3f5230da74c4c1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spdropagentparameter-transact-sql"></a>sp_drop_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un ou tous les paramètres d’un profil dans le **MSagent_parameters** table. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de distribution sur lequel l'agent est en cours d'exécution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_drop_agent_parameter [ @profile_id = ] profile_id  
    [ , [ @parameter_name = ] 'parameter_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@profile_id=**] *profile_id*  
 Identificateur du profil dont l'un des paramètres doit être supprimé. *profile_id* est **int**, sans valeur par défaut.  
  
 [  **@parameter_name=**] **'***nom_paramètre***'**  
 Nom du paramètre à supprimer. *nom_paramètre* est **sysname**, avec une valeur par défaut  **%** . Si  **%** , tous les paramètres pour le profil spécifié sont supprimés.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_drop_agent_parameter** est utilisée dans tous les types de réplication.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_drop_agent_parameter**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_agent_parameter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
