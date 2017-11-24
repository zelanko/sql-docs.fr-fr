---
title: Sys.sp_cdc_help_jobs (Transact-SQL) | Documents Microsoft
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
- sp_cdc_help_jobs
- sys.sp_cdc_help_jobs_TSQL
- sp_cdc_help_jobs_TSQL
- sys.sp_cdc_help_jobs
dev_langs: TSQL
helpviewer_keywords: sp_cdc_help_jobs
ms.assetid: 9399b4bc-8293-408f-b3cb-f904e0657fb5
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af8d6c3909c7de3e2db131ca5a3b0e8c6b0c4b98
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysspcdchelpjobs-transact-sql"></a>sys.sp_cdc_help_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Signale des informations sur tous les travaux de capture ou de nettoyage de capture de données modifiées dans la base de données active.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.sp_cdc_help_jobs  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID du travail.|  
|**type_du_travail**|**nvarchar (20)**|Le type de tâche.|  
|**maxtrans**|**int**|Le nombre maximal de transactions à traiter dans chaque cycle d’analyse.<br /><br /> **maxtrans** est valide uniquement pour les travaux de capture.|  
|**maxscans**|**int**|Le nombre maximal de cycles d’analyse à exécuter afin d’extraire toutes les lignes du journal.<br /><br /> **maxscans** est valide uniquement pour les travaux de capture.|  
|**continue**|**bit**|Indicateur qui précise si le travail de capture doit être exécuté en continu (1) ou ponctuellement (0). Pour plus d’informations, consultez [sys.sp_cdc_add_job &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **continue** est valide uniquement pour les travaux de capture.|  
|**PollingInterval**|**bigint**|Nombre de secondes entre les cycles d'analyse du journal.<br /><br /> **PollingInterval** est valide uniquement pour les travaux de capture.|  
|**rétention**|**bigint**|Nombre de minutes pendant lesquelles les lignes modifiées doivent être conservées dans les tables de modifications.<br /><br /> **rétention** est valide uniquement pour les travaux de nettoyage.|  
|**seuil**|**bigint**|Nombre maximal d'entrées qui peuvent être supprimées à l'aide d'une instruction unique lors du nettoyage.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **db_owner** rôle de base de données fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des informations sur les travaux de capture et de nettoyage définis pour la base de données `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_help_jobs;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.cdc_jobs &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
