---
title: Sys.sp_cdc_drop_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_drop_job_TSQL
- sp_cdc_drop_job_TSQL
- sp_cdc_drop_job
- sys.sp_cdc_drop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_drop_job
ms.assetid: e8265846-8051-4848-b28e-fac27c10bdeb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 36ffc0bbc703489140829dea8da594927219234f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031599"
---
# <a name="sysspcdcdropjob-transact-sql"></a>sys.sp_cdc_drop_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un travail de nettoyage ou de capture de données modifiées de msdb pour la base de données actuelle.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.sp_cdc_drop_job [ [ @job_type = ] 'job_type' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @job_type **=** ] '*type_du_travail*'  
 Type du travail à supprimer. *type_du_travail* est **nvarchar (20)** et ne peut pas être NULL. Les entrées valides sont 'capture' et 'cleanup'.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Nones  
  
## <a name="remarks"></a>Notes  
 sp_cdc_drop_job est appelée en interne par [sys.sp_cdc_disable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle de base de données fixe db_owner.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le travail de nettoyage pour la base de données `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_drop_job @job_type = N'cleanup';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [Sys.sp_cdc_disable_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)   
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
