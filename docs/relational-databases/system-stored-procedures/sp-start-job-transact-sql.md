---
title: sp_start_job (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_start_job
- sp_start_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_start_job
ms.assetid: 8a91df6a-eb84-4512-9a17-4a6e32a9538a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5939e906cee691c2b6f13ff10677eb4f4129622f
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="spstartjob-transact-sql"></a>sp_start_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ordonne à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent d'exécuter immédiatement un travail.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_start_job   
     {   [@job_name =] 'job_name'  
       | [@job_id =] job_id }  
     [ , [@error_flag =] error_flag]  
     [ , [@server_name =] 'server_name']  
     [ , [@step_name =] 'step_name']  
     [ , [@output_flag =] output_flag]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@job_name=** ] **'***job_name***'**  
 Nom du travail à démarrer. Soit *job_id* ou *job_name* doit être spécifié, mais ne peut pas être spécifiés. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
 [ **@job_id=** ] *job_id*  
 Numéro d'identification du travail à démarrer. Soit *job_id* ou *job_name* doit être spécifié, mais ne peut pas être spécifiés. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
 [ **@error_flag=** ] *error_flag*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ **@server_name=** ] **'***server_name***'**  
 Serveur cible sur lequel doit être lancé le travail. *nom_serveur* est **nvarchar (128)**, avec NULL comme valeur par défaut. *nom_serveur* doit être un des serveurs cibles sur lesquels le travail est actuellement ciblé.  
  
 [ **@step_name=** ] **'***step_name***'**  
 Nom de l'étape où doit commencer l'exécution du travail. S'applique uniquement aux travaux locaux. *nom_de_l* est **sysname**, avec NULL comme valeur par défaut  
  
 [ **@output_flag=** ] *output_flag*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 Cette procédure stockée se trouve dans le **msdb** base de données.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Membres de **SQLAgentUserRole** et **SQLAgentReaderRole** peuvent lancer uniquement les travaux dont ils sont propriétaires. Membres de **SQLAgentOperatorRole** peut démarrer tous les travaux locaux, y compris ceux qui appartiennent à d’autres utilisateurs. Membres de **sysadmin** peut démarrer tous les travaux locaux et multiserveurs.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant démarre un travail appelé `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_stop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
