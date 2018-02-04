---
title: dbo.systaskids (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
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
- systaskids_TSQL
- dbo.systaskids
- systaskids
- dbo.systaskids_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systaskids system table
ms.assetid: 45c56d89-4160-4d84-80bf-a7a05488792d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 20f08ae12092b6d5e0ffa33ad118cbd100a96338
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="dbosystaskids-transact-sql"></a>dbo.systaskids (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient un mappage des tâches créées dans des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers des travaux [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans la version actuelle. Cette table est stockée dans le **msdb** base de données.  
  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**task_id**|**int**|ID de la tâche|  
|**job_id**|**uniqueidentifier**|ID du travail auquel la tâche est mappée.|  
  
  
