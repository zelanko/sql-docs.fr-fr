---
title: sp_post_msx_operation (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_post_msx_operation
- sp_post_msx_operation_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_post_msx_operation
ms.assetid: 085deef8-2709-4da9-bb97-9ab32effdacf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f36ad40a2b16401218fe2a5927407464fe6ac11b
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536123"
---
# <a name="sppostmsxoperation-transact-sql"></a>sp_post_msx_operation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Insère des opérations (lignes) dans le **sysdownloadlist** (table système) pour les serveurs cibles télécharger et exécuter.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_post_msx_operation  
     [ @operation = ] 'operation'  
     [ , [ @object_type = ] 'object' ]   
     { , [ @job_id = ] job_id }   
     [ , [ @specific_target_server = ] 'target_server' ]   
     [ , [ @value = ] value ]  
     [ , [ @schedule_uid = ] schedule_uid ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @operation = ] 'operation'` Le type d’opération pour l’opération publiée. *opération*est **varchar(64)**, sans valeur par défaut. Opérations dépend de *object_type*.  
  
|Type d'objet|Opération|  
|-----------------|---------------|  
|**JOB**|INSERT<br /><br /> UPDATE<br /><br /> Suppression<br /><br /> START<br /><br /> STOP|  
|**SERVER**|RE-ENLIST<br /><br /> DEFECT<br /><br /> SYNC-TIME<br /><br /> SET-POLL|  
|**PLANIFICATION**|INSERT<br /><br /> UPDATE<br /><br /> Suppression|  
  
`[ @object_type = ] 'object'` Le type d’objet pour lequel une opération post. Les types valides sont **travail**, **SERVER**, et **planification**. *objet* est **varchar(64)**, avec une valeur par défaut **travail**.  
  
`[ @job_id = ] job_id` Numéro d’identification du travail auquel l’opération s’applique. *job_id* est **uniqueidentifier**, sans valeur par défaut. **0 x 00** indique tous les travaux. Si *objet* est **SERVER**, puis *job_id*n’est pas obligatoire.  
  
`[ @specific_target_server = ] 'target_server'` Le nom du serveur cible pour lequel l’opération spécifiée s’applique. Si *job_id* est spécifié, mais *serveur_cible* n’est pas spécifié, les opérations sont publiées pour tous les serveurs cibles du travail. *serveur_cible* est **nvarchar (30)**, avec NULL comme valeur par défaut.  
  
`[ @value = ] value` L’intervalle d’interrogation, en secondes. *value* est de type **int**, avec NULL comme valeur par défaut. Spécifiez ce paramètre uniquement si *opération* est **SET-POLL**.  
  
`[ @schedule_uid = ] schedule_uid` Identificateur unique pour la planification à laquelle s’applique l’opération. *schedule_uid* est **uniqueidentifier**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 **sp_post_msx_operation** doit être exécuté à partir de la **msdb** base de données.  
  
 **sp_post_msx_operation** peut toujours être appelée en toute sécurité, car il détermine tout d’abord si le serveur actuel est un Agent Microsoft SQL Server multiserveur et, le cas échéant, si *objet*est un travail multiserveur.  
  
 Une fois une opération a été publiée, il apparaît dans le **sysdownloadlist** table. Après qu'un travail a été créé et publié, les modifications ultérieures apportées à ce travail doivent être aussi communiquées aux serveurs cibles (TSX). L'opération est également réalisée à l'aide de la liste de téléchargement. .  
  
 Il est fortement recommandé de gérer la liste de téléchargement à l'aide de SQL Server Management Studio. Pour plus d’informations, consultez [afficher ou modifier les travaux](../../ssms/agent/view-or-modify-jobs.md).  
  
## <a name="permissions"></a>Autorisations  
 Pour exécuter cette procédure stockée, les utilisateurs doivent avoir le **sysadmin** rôle serveur fixe.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_delete_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_resync_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_stop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
