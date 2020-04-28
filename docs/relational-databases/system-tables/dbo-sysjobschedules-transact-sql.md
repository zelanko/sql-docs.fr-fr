---
title: dbo. sysjobschedules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobschedules
- dbo.sysjobschedules
- dbo.sysjobschedules_TSQL
- sysjobschedules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobschedules system table
ms.assetid: ccdafec7-2a9b-4356-bffb-1caa3a12db59
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7f2dfc6196bfba6c274eb45a45745159447cc39
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68061180"
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient les informations de planification pour les travaux qui doivent être exécutés par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans la base de données **msdb** .  
  
> **Remarque :** La table **sysjobschedules** est actualisée toutes les 20 minutes, ce qui peut affecter les valeurs retournées par la procédure stockée **sp_help_jobschedule** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|ID de la planification.|  
|**job_id**|**uniqueidentifier**|ID du travail.|  
|**next_run_date**|**int**|Date à laquelle est planifiée la prochaine exécution du travail. La date se présente sous la forme AAAAMMJJ.|  
|**next_run_time**|**int**|Heure à laquelle est planifiée la prochaine exécution du travail. L'heure se présente sous la forme HHMMSS et est exprimée sur 24 heures.|  
  
## <a name="see-also"></a>Voir aussi  
 [dbo. sysschedules &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
