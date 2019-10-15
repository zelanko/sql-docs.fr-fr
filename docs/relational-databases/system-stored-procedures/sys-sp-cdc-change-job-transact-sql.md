---
title: sys.sp_cdc_change_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_change_job_TSQL
- sys.sp_cdc_change_job
- sp_cdc_change_job_TSQL
- sp_cdc_change_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_change_job
ms.assetid: ea918888-0fc5-4cc1-b301-26b2a9fbb20d
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bd906f9a359a73a15d89a4cb60b6646a2abe53a
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305065"
---
# <a name="syssp_cdc_change_job-transact-sql"></a>sys.sp_cdc_change_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie la configuration d'un travail de capture ou de nettoyage de capture de données modifiées dans la base de données actuelle. Pour afficher la configuration actuelle d’un travail, interrogez la table [dbo. CDC _jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) ou utilisez [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.sp_cdc_change_job [ [ @job_type = ] 'job_type' ]  
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ @threshold = ] 'delete threshold'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_type = ] 'job_type'` type de travail à modifier. *job_type* est de type **nvarchar (20)** avec « capture » comme valeur par défaut. Les entrées valides sont 'capture' et 'cleanup'.  
  
`[ @maxtrans ] = max_trans_` nombre maximal de transactions à traiter dans chaque cycle d’analyse. *max_trans* est de **type int** avec NULL comme valeur par défaut, qui n’indique aucune modification pour ce paramètre. Si elle est spécifiée, la valeur doit être un entier positif.  
  
 *max_trans* est valide uniquement pour les travaux de capture.  
  
`[ @maxscans ] = max_scans_` nombre maximal de cycles d’analyse à exécuter afin d’extraire toutes les lignes du journal. *max_scans* est de **type int** avec NULL comme valeur par défaut, qui n’indique aucune modification pour ce paramètre.  
  
 *max_scan* est valide uniquement pour les travaux de capture.  
  
`[ @continuous ] = continuous_` indique si le travail de capture doit s’exécuter en continu (1) ou s’exécuter une seule fois (0). *Continuous* est de type **bit** , avec NULL comme valeur par défaut, qui n’indique aucune modification pour ce paramètre.  
  
 Lorsque *Continuous* = 1, le travail [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) analyse le journal et traite les transactions jusqu’à (*max_trans* \* *max_scans*). Il attend ensuite le nombre de secondes spécifié dans *polling_interval* avant de commencer la prochaine analyse du journal.  
  
 Lorsque *Continuous* = 0, le travail **sp_cdc_scan** s’exécute jusqu’à *max_scans* analyses du journal, en traitant jusqu’à *max_trans* transactions pendant chaque analyse, puis se ferme.  
  
 Si **\@continuous** passe de 1 à 0, **\@pollinginterval** a automatiquement la valeur 0. Une valeur spécifiée pour **\@pollinginterval** autre que 0 est ignorée.  
  
 Si **\@continuous** est omis ou a explicitement la valeur null et que **\@pollinginterval** est défini explicitement sur une valeur supérieure à 0, **\@continuous** a automatiquement la valeur 1.  
  
 *Continuous* est valide uniquement pour les travaux de capture.  
  
`[ @pollinginterval ] = polling_interval_` nombre de secondes entre les cycles d’analyse du journal. *polling_interval* est de type **bigint** , avec NULL comme valeur par défaut, qui n’indique aucune modification pour ce paramètre.  
  
 *polling_interval* est valide uniquement pour les travaux de capture quand *Continuous* a la valeur 1.  
  
`[ @retention ] = retention_` nombre de minutes pendant lesquelles les lignes modifiées doivent être conservées dans les tables de modifications. *Retention* est de type **bigint** , avec NULL comme valeur par défaut, qui n’indique aucune modification pour ce paramètre. La valeur maximale est égale à 52494800 (100 ans). Si elle est spécifiée, la valeur doit être un entier positif.  
  
 la *rétention* est valide uniquement pour les travaux de nettoyage.  
  
`[ @threshold = ] 'delete threshold'` nombre maximal d’entrées qui peuvent être supprimées à l’aide d’une instruction unique lors du nettoyage. le *seuil de suppression* est de type **bigint** , avec NULL comme valeur par défaut, qui n’indique aucune modification pour ce paramètre. le *seuil de suppression* est valide uniquement pour les travaux de nettoyage.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 Si un paramètre est omis, la valeur associée dans la table [dbo. CDC _jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) n’est pas mise à jour. Un paramètre qui a pour valeur explicite NULL est traité comme s'il était omis.  
  
 La spécification d'un paramètre qui n'est pas valide pour le type de travail provoquera l'échec de l'instruction.  
  
 Les modifications apportées à un travail n’entrent pas en vigueur tant que le travail n’est pas arrêté à l’aide de [sp_cdc_stop_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md) et redémarré à l’aide de [sp_cdc_start_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Requiert l’appartenance au rôle de base de données fixe **db_owner** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-a-capture-job"></a>R. Modification d'un travail de capture  
 L’exemple suivant met à jour les paramètres `@job_type`, `@maxscans` et `@maxtrans` d’un travail de capture dans la base de données `AdventureWorks2012`. Les autres paramètres valides pour un travail de capture, `@continuous` et `@pollinginterval`, sont omis ; leurs valeurs ne sont pas modifiées.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'capture',  
    @maxscans = 1000,  
    @maxtrans = 15;  
GO  
```  
  
### <a name="b-changing-a-cleanup-job"></a>B. Modification d'un travail de nettoyage  
 L'exemple suivant met à jour un travail de nettoyage dans la base de données `AdventureWorks2012`. Tous les paramètres valides pour ce type de tâche, à l’exception **de @threshold** , sont spécifiés. La valeur de **@threshold** n’est pas modifiée.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'cleanup',  
    @retention = 2880;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
