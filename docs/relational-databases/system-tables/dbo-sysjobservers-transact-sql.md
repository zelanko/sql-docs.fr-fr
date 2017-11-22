---
title: dbo.sysjobservers (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a706c537f4f983563dacb1f137314680824dd30
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stocke les associations ou les relations existant entre un travail particulier et un ou plusieurs serveurs cibles. Cette table est stockée dans la base de données msdb.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|Numéro d’identification du travail.|  
|server_id|**int**|Numéro d’identification du serveur.|  
|last_run_outcome|**tinyint**|Issue de la dernière exécution du travail :<br /><br /> **0** = Échec<br /><br /> **1** = réussite<br /><br /> **3** = Annuler|  
|message de last_outcome_|**nvarchar (1024)**|Message associé, le cas échéant, à la colonne last_run_outcome.|  
|last_run_date|**int**|Date de la dernière exécution du travail.|  
|last_run_time|**int**|Heure de la dernière exécution du travail.|  
|last_run_duration|**int**|Durée d'exécution du travail, en heures, minutes et secondes. Calculé à l’aide de la formule : (*heures*\*10000) + (*minutes*\*100) + *secondes*.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de l’Agent SQL Server &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
