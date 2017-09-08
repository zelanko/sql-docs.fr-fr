---
title: KILL STATS JOB (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KILL STATS JOB
- KILL_STATS_JOB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ending statistics update jobs [SQL Server]
- stopping statistics update jobs
- terminating statistics update jobs
- asynchronous statistics updates [SQL Server]
- KILL STATS JOB statement
- statistics update jobs [SQL Server]
ms.assetid: 55a8f9f1-3259-45c0-8ab9-60b9c088b4b4
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7f1738c96709d2eb1489c9ec25c598459842e3ab
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="kill-stats-job-transact-sql"></a>KILL STATS JOB (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Met fin à un travail de mise à jour asynchrone des statistiques dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
KILL STATS JOB job_id   
```  
  
## <a name="arguments"></a>Arguments  
 *job_id*  
 Champ job_id renvoyé par la vue de gestion dynamique sys.dm_exec_background_job_queue du travail.  
  
## <a name="remarks"></a>Notes  
 L'argument job_id n'est pas lié à session_id ou à l'unité de travail utilisée dans d'autres formes de l'instruction KILL.  
  
## <a name="permissions"></a>Permissions  
 L'utilisateur doit bénéficier de l'autorisation VIEW SERVER STATE pour accéder aux données de la vue de gestion dynamique sys.dm_exec_background_job_queue.  
  
 Les autorisations de l'instruction KILL STATS JOB sont octroyées par défaut aux membres des rôles de base de données fixes sysadmin et processadmin et ne sont pas transmissibles.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment mettre fin à la mise à jour des statistiques associée à un travail dans lequel le *job_id* = `53`.  
  
```  
KILL STATS JOB 53;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [KILL &#40; Transact-SQL &#41;](../../t-sql/language-elements/kill-transact-sql.md)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION &#40; Transact-SQL &#41;](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)   
 [Sys.dm_exec_background_job_queue &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-background-job-queue-transact-sql.md)   
 [Statistiques](../../relational-databases/statistics/statistics.md)  
  
  

