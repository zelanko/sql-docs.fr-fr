---
title: dbo.sysjobschedules (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysjobschedules
- dbo.sysjobschedules
- dbo.sysjobschedules_TSQL
- sysjobschedules_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobschedules system table
ms.assetid: ccdafec7-2a9b-4356-bffb-1caa3a12db59
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 745f3e858a195e2004c3b67e0b3ec973df58a3fb
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient les informations de planification pour les travaux qui doivent être exécutés par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans le **msdb** base de données.  
  
> **Remarque :** le **sysjobschedules** table actualise toutes les 20 minutes, ce qui peut affecter les valeurs retournées par la **sp_help_jobschedule** procédure stockée.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**id_de_la_planification**|**int**|ID de la planification.|  
|**job_id**|**uniqueidentifier**|ID du travail.|  
|**next_run_date**|**int**|Date à laquelle est planifiée la prochaine exécution du travail. La date se présente sous la forme AAAAMMJJ.|  
|**next_run_time**|**int**|Heure à laquelle est planifiée la prochaine exécution du travail. L'heure se présente sous la forme HHMMSS et est exprimée sur 24 heures.|  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.sysschedules &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
