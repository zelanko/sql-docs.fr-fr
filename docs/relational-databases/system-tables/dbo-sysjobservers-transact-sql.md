---
title: dbo.sysjobservers (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60a5062226e97be3e7c3a38086f0e88dbf9fb023
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stocke les associations ou les relations existant entre un travail particulier et un ou plusieurs serveurs cibles. Cette table est stockée dans la base de données msdb.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|Numéro d’identification du travail.|  
|server_id|**int**|Numéro d’identification du serveur.|  
|last_run_outcome|**tinyint**|Issue de la dernière exécution du travail :<br /><br /> **0** = Échec<br /><br /> **1** = réussite<br /><br /> **3** = Annuler|  
|message de last_outcome_|**nvarchar(1024)**|Message associé, le cas échéant, à la colonne last_run_outcome.|  
|last_run_date|**int**|Date de la dernière exécution du travail.|  
|last_run_time|**int**|Heure de la dernière exécution du travail.|  
|last_run_duration|**int**|Durée d'exécution du travail, en heures, minutes et secondes. Calculé à l’aide de la formule : (*heures*\*10000) + (*minutes*\*100) + *secondes*.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de l’Agent SQL Server &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
