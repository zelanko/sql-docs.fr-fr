---
title: sp_change_agent_profile (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_agent_profile
- sp_change_agent_profile_TSQL
helpviewer_keywords:
- sp_change_agent_profile
ms.assetid: e73acf8d-0be8-4197-ba11-fe798d0e2820
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b0084338c2629b8ffeb208edc5ac7532105e1271
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715944"
---
# <a name="sp_change_agent_profile-transact-sql"></a>sp_change_agent_profile (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Modifie un paramètre d’un profil d’agent de réplication stocké dans la table [MSagent_profiles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) . Cette procédure stockée est exécutée sur n’importe quelle base de données du serveur de distribution.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_change_agent_profile [ @profile_id = ] profile_id   
        , [ @property = ] 'property'   
        , [ @value = ] 'value'   
```  
  
## <a name="arguments"></a>Arguments  
`[ @profile_id = ] profile_id`ID du profil. *profile_id* est de **type int**, sans valeur par défaut.  
  
`[ @property = ] 'property'`Nom de la propriété. *Property* est de **type sysname**, sans valeur par défaut.  
  
`[ @value = ] 'value'`Nouvelle valeur de la propriété. la *valeur* est de type **nvarchar (3000)**, sans valeur par défaut.  
  
 Cette table décrit les propriétés modifiables du profil.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**description**|Description du profil.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
 **sp_change_agent_profile** est utilisé dans tous les types de réplications.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_change_agent_profile**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_drop_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
