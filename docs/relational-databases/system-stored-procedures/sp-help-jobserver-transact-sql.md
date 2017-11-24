---
title: sp_help_jobserver (Transact-SQL) | Documents Microsoft
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
- sp_help_jobserver
- sp_help_jobserver_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_jobserver
ms.assetid: 57971787-f9f5-4199-9f64-c2b61a308906
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 44d44897f3d7ade90eb6849c6deae5a9a1d5cca9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpjobserver-transact-sql"></a>sp_help_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur le serveur pour un travail donné.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_jobserver  
     { [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name' }  
     [ , [ @show_last_run_details = ] show_last_run_details ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_id=** ] *job_id*  
 Numéro d'identification du travail pour lequel renvoyer des informations. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
 [  **@job_name=** ] **'***job_name***'**  
 Nom du travail pour lequel renvoyer des informations. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *job_id* ou *job_name* doit être spécifié, mais ne peut pas être spécifiés.  
  
 [  **@show_last_run_details=** ] *afficher_les_détails_de_dernière_exécution*  
 Indique si les informations de la dernière exécution doivent faire partie du jeu de résultats. *afficher_les_détails_de_dernière_exécution* est **tinyint**, avec une valeur par défaut **0**. **0** n’inclut pas les informations de la dernière exécution, et **1** est.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Numéro d'identification du serveur cible.|  
|**nom_serveur**|**nvarchar (30)**|Nom de l'ordinateur du serveur cible.|  
|**enlist_date**|**datetime**|Date d'inscription du serveur cible sur le serveur maître.|  
|**last_poll_date**|**datetime**|Date à laquelle le serveur cible a interrogé pour la dernière fois le serveur maître.|  
  
 Si **sp_help_jobserver** est exécutée avec *afficher_les_détails_de_dernière_exécution* la valeur **1**, le jeu de résultats comporte ces colonnes supplémentaires.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**last_run_date**|**int**|Date du début de la dernière exécution du travail sur ce serveur cible.|  
|**last_run_time**|**int**|Heure du début de la dernière exécution du travail sur ce serveur.|  
|**last_run_duration**|**int**|Durée du travail lors de sa dernière exécution sur ce serveur cible (en secondes).|  
|**last_outcome_message**|**nvarchar (1024)**|Décrit le dernier résultat du travail.|  
|**last_run_outcome**|**int**|Résultat du travail à l'issue de sa dernière exécution sur ce serveur.<br /><br /> **0** = Échec<br /><br /> **1** = a réussi<br /><br /> **3** = annulée<br /><br /> **5** = inconnu|  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Membres de **SQLAgentUserRole** peut uniquement afficher des informations sur les travaux dont ils sont propriétaires.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renvoie des informations, dont les informations sur la dernière exécution, du travail `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobserver  
    @job_name = N'NightlyBackups',  
    @show_last_run_details = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_jobserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
