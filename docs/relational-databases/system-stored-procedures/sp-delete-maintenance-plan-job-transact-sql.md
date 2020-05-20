---
title: sp_delete_maintenance_plan_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan_job
- sp_delete_maintenance_plan_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan_job
ms.assetid: 1c2148c3-2928-4d9b-b1c8-3512cfbd6a63
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7e408132edbfc042335fd1e0297f0e8a4b07223b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833366"
---
# <a name="sp_delete_maintenance_plan_job-transact-sql"></a>sp_delete_maintenance_plan_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Dissocie le plan de maintenance spécifié du travail spécifié.  
  
> [!NOTE]  
>  Cette procédure stockée s'utilise avec des plans de maintenance de base de données. Cette fonctionnalité a été remplacée par des plans de maintenance qui n'utilisent pas cette procédure stockée. Utilisez cette procédure pour gérer des plans de maintenance de base de données sur des installations qui ont été mises à niveau à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_maintenance_plan_job [ @plan_id = ] 'plan_id' ,   
   [ @job_id = ] 'job_id'   
```  
  
## <a name="arguments"></a>Arguments  
`[ @plan_id = ] 'plan\_id'`Spécifie l’ID du plan de maintenance. *plan_id* est de type **uniqueidentifier**et doit être un ID valide.  
  
`[ @job_id = ] 'job\_id'`Spécifie l’ID du travail auquel le plan de maintenance est associé. *job_id* est de type **uniqueidentifier**et doit être un ID valide.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_delete_maintenance_plan_job** doit être exécuté à partir de la base de données **msdb** .  
  
 Lorsque toutes les tâches ont été supprimées du plan de maintenance, nous recommandons aux utilisateurs d’exécuter **sp_delete_maintenance_plan_db** pour supprimer les bases de données restantes du plan.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_delete_maintenance_plan_job**.  
  
## <a name="examples"></a>Exemples  
 Cet exemple supprime le travail « B8FCECB1-E22C-11D2-AA64-00C04F688EAE » du plan de maintenance.  
  
```  
EXECUTE   sp_delete_maintenance_plan_job N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'B8FCECB1-E22C-11D2-AA64-00C04F688EAE';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Plans de maintenance](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Procédures stockées de plan de maintenance de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
