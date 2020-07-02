---
title: sp_dropdynamicsnapshot_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords:
- sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a1dffb4ba6cdd82481777496033e56ca0571e37d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786944"
---
# <a name="sp_dropdynamicsnapshot_job-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Supprime un travail d'instantané de données filtrées pour une publication avec des filtres de lignes paramétrés. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication. Lorsque le travail est supprimé, toutes les données associées sont supprimées de la table système [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) .  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication à partir de laquelle le travail d’instantané de données filtrées est supprimé. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'`Nom du travail d’instantané de données filtrées en cours de suppression. *dynamic_snapshot_jobname*est de type sysname et, s’il n’est pas fourni, par défaut, quel que soit le nom du travail associé à *dynamic_snapshot_jobid*.  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'`Identificateur du travail d’instantané de données filtrées en cours de suppression. *dynamic_snapshot_jobid*est de type **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  Seul *dynamic_snapshot_jobid*ou *dynamic_snapshot_jobname* peut être spécifié. Si aucune valeur n’est fournie pour *dynamic_snapshot_jobid*ou *dynamic_snapshot_jobname*, tous les travaux d’instantanés dynamiques pour la publication sont supprimés.  
  
`[ @ignore_distributor = ] ignore_distributor`*ignore_distributor* est de **bit**, avec **0**comme valeur par défaut. Ce paramètre peut être utilisé pour supprimer un travail d'instantané dynamique sans avoir à effectuer de tâches de nettoyage sur le serveur de distribution.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
 **sp_dropdynamicsnapshot** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_dropdynamicsnapshot**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_adddynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
