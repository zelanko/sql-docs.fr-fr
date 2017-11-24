---
title: sp_delete_maintenance_plan_job (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan_job
- sp_delete_maintenance_plan_job_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_delete_maintenance_plan_job
ms.assetid: 1c2148c3-2928-4d9b-b1c8-3512cfbd6a63
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b9d203fd5fccb59ad6ac981d3639e6c74401c4c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spdeletemaintenanceplanjob-transact-sql"></a>sp_delete_maintenance_plan_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Dissocie le plan de maintenance spécifié du travail spécifié.  
  
> [!NOTE]  
>  Cette procédure stockée s'utilise avec des plans de maintenance de base de données. Cette fonctionnalité a été remplacée par des plans de maintenance qui n'utilisent pas cette procédure stockée. Utilisez cette procédure pour gérer des plans de maintenance de base de données sur des installations qui ont été mises à niveau à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_maintenance_plan_job [ @plan_id = ] 'plan_id' ,   
   [ @job_id = ] 'job_id'   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@plan_id =**] **'***plan_id***'**  
 Spécifie l'identificateur du plan de maintenance. *plan_id* est **uniqueidentifier**, et doit être un ID valide.  
  
 [  **@job_id =**] **'***job_id***'**  
 Spécifie l'ID du travail auquel le plan de maintenance est associé. *job_id* est **uniqueidentifier**, et doit être un ID valide.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_delete_maintenance_plan_job** doit être exécuté à partir de la **msdb** base de données.  
  
 Lorsque tous les travaux ont été supprimés du plan de maintenance, nous vous recommandons d’exécutent les utilisateurs **sp_delete_maintenance_plan_db** pour supprimer les bases de données à partir du plan.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_delete_maintenance_plan_job**.  
  
## <a name="examples"></a>Exemples  
 Cet exemple supprime le travail « B8FCECB1-E22C-11D2-AA64-00C04F688EAE » du plan de maintenance.  
  
```  
EXECUTE   sp_delete_maintenance_plan_job N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'B8FCECB1-E22C-11D2-AA64-00C04F688EAE';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Plans de maintenance](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Plan de Maintenance de base de données stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
