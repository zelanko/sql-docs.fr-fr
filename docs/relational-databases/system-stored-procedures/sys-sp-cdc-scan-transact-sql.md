---
title: sys. sp_cdc_scan (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_scan_TSQL
- sp_cdc_scan
- sys.sp_cdc_scan
- sp_cdc_scan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_scan
ms.assetid: 46e4294c-97b8-47d6-9ed9-b436a9929353
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 558a2fd9ff62baa3448609eb42e5f31883fbac53
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891066"
---
# <a name="syssp_cdc_scan-transact-sql"></a>sys.sp_cdc_scan (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Exécute l'opération d'analyse du journal de la capture de données modifiées.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.sp_cdc_scan [ [ @maxtrans = ] max_trans ]   
     [ , [ @maxscans = ] max_scans ]   
     [ , [ @continuous = ] continuous ]   
     [ , [ @pollinginterval = ] polling_interval ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @maxtrans = ] max_trans`Nombre maximal de transactions à traiter dans chaque cycle d’analyse. *max_trans* est de **type int** avec 500 comme valeur par défaut.  
  
`[ @maxscans = ] max_scans`Nombre maximal de cycles d’analyse à exécuter afin d’extraire toutes les lignes du journal. *max_scans* est de **type int** avec 10 comme valeur par défaut.  
  
`[ @continuous = ] continuous`Indique si la procédure stockée doit se terminer après l’exécution d’un cycle d’analyse unique (0) ou s’exécuter en continu, ce qui interrompt l’exécution de l’opération spécifiée par *polling_interval* avant de réexécuter le cycle d’analyse (1). *Continuous* est de **type tinyint** , avec 0 comme valeur par défaut.  
  
`[ @pollinginterval = ] polling_interval`Nombre de secondes entre les cycles d’analyse du journal. *polling_interval* est de type **bigint** , avec 0 comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 sys.sp_cdc_scan est appelé en interne par sys.sp_MScdc_capture_job si le travail de capture de l'agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est utilisé par la capture de données modifiées. La procédure ne peut pas être exécutée de manière explicite lorsqu'une opération d'analyse du journal de capture de données modifiées est déjà active ou lorsque la base de données est activée pour la réplication transactionnelle. Cette procédure stockée doit être utilisée par les administrateurs qui souhaitent personnaliser le comportement du travail de capture configuré automatiquement.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle de base de données fixe db_owner.  
  
## <a name="see-also"></a>Voir aussi  
 [dbo. cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
