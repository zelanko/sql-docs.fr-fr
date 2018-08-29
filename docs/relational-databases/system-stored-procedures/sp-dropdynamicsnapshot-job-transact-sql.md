---
title: sp_dropdynamicsnapshot_job (Transact-SQL) | Microsoft Docs
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
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords:
- sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 89de049ad17ac51f6b166da59269b41b1101d258
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028729"
---
# <a name="spdropdynamicsnapshotjob-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un travail d'instantané de données filtrées pour une publication avec des filtres de lignes paramétrés. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication. Lorsque le travail est supprimé, toutes les données associées sont supprimées à partir de la [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) (table système).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'***publication***'**  
 Nom de la publication dans laquelle le travail d'instantané de données filtrées est supprimé. *publication* est **sysname**, sans valeur par défaut.  
  
 [ **@dynamic_snapshot_jobname**=] **'***dynamic_snapshot_jobname***'**  
 Nom du travail d'instantané de données filtrées qui va être supprimé. *dynamic_snapshot_jobname*est de type sysname, et si elle n’est pas fournis de valeurs par défaut à toute tâche nom est associé *dynamic_snapshot_jobid*.  
  
 [ **@dynamic_snapshot_jobid**=] **'***dynamic_snapshot_jobid***'**  
 Identificateur du travail d'instantané de données filtrées qui va être supprimé. *dynamic_snapshot_jobid*est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  Uniquement *dynamic_snapshot_jobid*ou *dynamic_snapshot_jobname* peut être spécifié. Si les valeurs ne sont pas fournis pour soit *dynamic_snapshot_jobid*ou *dynamic_snapshot_jobname*, tous les travaux d’instantané dynamique pour la publication sont supprimés.  
  
 [  **@ignore_distributor =**] *ignore_distributor*  
 *ignore_distributor* est **bits**, avec une valeur par défaut **0**. Ce paramètre peut être utilisé pour supprimer un travail d'instantané dynamique sans avoir à effectuer de tâches de nettoyage sur le serveur de distribution.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropdynamicsnapshot** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_dropdynamicsnapshot**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_adddynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
