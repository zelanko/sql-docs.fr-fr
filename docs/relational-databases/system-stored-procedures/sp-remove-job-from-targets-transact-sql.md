---
title: sp_remove_job_from_targets (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_remove_job_from_targets_TSQL
- sp_remove_job_from_targets
dev_langs:
- TSQL
helpviewer_keywords:
- sp_remove_job_from_targets
ms.assetid: b8171fb1-c11d-4244-8618-a12e28a150ce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6ec60d6b11f9d17a6f5446e2840688fd1e4cb75
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536831"
---
# <a name="spremovejobfromtargets-transact-sql"></a>sp_remove_job_from_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime le travail spécifié des serveurs cibles ou des groupes de serveurs cibles donnés.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_remove_job_from_targets [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name'   
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_id = ] job_id` Numéro d’identification du travail à partir duquel supprimer les groupes de serveurs cibles ou les serveurs cibles spécifiés. Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
`[ @job_name = ] 'job_name'` Le nom du travail à partir duquel supprimer les groupes de serveurs cibles ou les serveurs cibles spécifiés. Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @target_server_groups = ] 'target_server_groups'` Une liste séparée par des virgules de groupes de serveurs cibles à supprimer du travail spécifié. *groupes_serveurs_cibles* est **nvarchar (1024)**, avec NULL comme valeur par défaut.  
  
`[ @target_servers = ] 'target_servers'` Une liste séparée par des virgules de serveurs cibles à supprimer du travail spécifié. *serveurs_cibles* est **nvarchar (1024)**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d'exécution de cette procédure sont accordées par défaut aux membres du rôle de serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 Dans cet exemple, le travail `Weekly Sales Backups`, créé au préalable, est supprimé du groupe de serveurs cibles `Servers Processing Customer Orders` et des serveurs `SEATTLE1` et `SEATTLE2`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_remove_job_from_targets  
    @job_name = N'Weekly Sales Backups',  
    @target_server_groups = N'Servers Processing Customer Orders',   
    @target_servers = N'SEATTLE2,SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_apply_job_to_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
