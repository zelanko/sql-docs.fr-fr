---
title: sp_delete_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_job
- sp_delete_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_job
ms.assetid: b85db6e4-623c-41f1-9643-07e5ea38db09
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e56bfe08d9279408cc7bdbc4b57a9719a04946fb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857053"
---
# <a name="spdeletejob-transact-sql"></a>sp_delete_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un travail.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_job { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
     [ , [ @originating_server = ] 'server' ]   
     [ , [ @delete_history = ] delete_history ]  
     [ , [ @delete_unused_schedule = ] delete_unused_schedule ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_id=** ] *job_id*  
 Numéro d'identification du travail à supprimer. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
 [  **@job_name=** ] **'***nom_travail***'**  
 Nom du travail à supprimer. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *job_id* ou *nom_travail*doit être spécifié ; ne peut pas être spécifiés.  
  
 [  **@originating_server=** ] **'***server***»**  
 À usage interne uniquement.  
  
 [  **@delete_history=** ] *delete_history*  
 Spécifie s'il faut supprimer l'historique du travail. *delete_history* est **bits**, avec une valeur par défaut **1**. Lorsque *delete_history* est **1**, l’historique des travaux pour le travail sont supprimé. Lorsque *delete_history* est **0**, l’historique des travaux ne sont pas supprimé.  
  
 Notez que lorsqu’un travail est supprimé et l’historique n’est pas supprimé, les informations d’historique pour le travail ne seront pas visibles dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent utilisateur graphique historique de l’interface, mais les informations seront trouvent toujours dans le **sysjobhistory**de table dans le **msdb** base de données.  
  
 [ **@delete_unused_schedule=** ] *delete_unused_schedule*  
 Indique s'il faut supprimer les planifications associées à ce travail si aucun autre travail n'y fait référence. *delete_unused_schedule* est **bits**, avec une valeur par défaut **1**. Lorsque *delete_unused_schedule* est **1**, les planifications associées à ce travail sont supprimées si aucun autre travail fait référence à la planification. Lorsque *delete_unused_schedule* est **0**, les planifications ne sont pas supprimées.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Le **@originating_server** argument est réservé à un usage interne.  
  
 Le **@delete_unused_schedule** argument fournit la compatibilité descendante avec les versions précédentes de SQL Server en supprimant automatiquement les planifications qui ne sont pas attachées à n’importe quel travail. Notez que, par défaut, ce paramètre permet la compatibilité amont. Pour conserver les planifications qui ne sont pas associées à une tâche, vous devez fournir la valeur **0** en tant que le **@delete_unused_schedule** argument.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est un outil dont l'interface graphique permet de gérer facilement les travaux. Son utilisation est recommandée pour créer et gérer l'infrastructure des travaux.  
  
 Cette procédure stockée ne peut pas supprimer les plans de maintenance ni les travaux relevant de plans de maintenance. Pour supprimer les plans de maintenance, vous devez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_delete_job** pour supprimer un travail. Un utilisateur qui n'est pas membre du rôle serveur fixe **sysadmin** n'a le droit de supprimer que les travaux dont il est propriétaire.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le travail `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
