---
title: dbo.sysjobhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/24/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobhistory_TSQL
- dbo.sysjobhistory
- sysjobhistory
- sysjobhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobhistory system table
ms.assetid: 1b1fcdbb-2af2-45e6-bf3f-e8279432ce13
author: stevestein
ms.author: sstein
ms.openlocfilehash: 85710deec2e7ab5e79ed7a514e3b625c6232484e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67902198"
---
# <a name="dbosysjobhistory-transact-sql"></a>dbo.sysjobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Contient des informations sur l'exécution des travaux planifiés par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
> [!NOTE]
> Dans la plupart des cas les données sont mis à jour uniquement après la fin de l’étape de travail et la table ne contient généralement aucun enregistrement des étapes de travail qui sont actuellement en cours d’exécution, mais dans certains cas, processus sous-jacents *faire* fournissent des informations à propos de étapes de travail en cours.

Cette table est stockée dans le **msdb** base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Identificateur unique de la ligne.|  
|**job_id**|**uniqueidentifier**|ID de travail.|  
|**step_id**|**int**|ID de l'étape dans le travail|  
|**step_name**|**sysname**|Nom de l'étape|  
|**sql_message_id**|**Int**|Identificateur de tout message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourné en cas d'échec du travail.|  
|**sql_severity**|**int**|Gravité des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**message**|**nvarchar(4000)**|Texte éventuel d'une erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**run_status**|**int**|État de l'exécution du travail :<br /><br /> **0** = Échec<br /><br /> **1** = a réussi<br /><br /> **2** = nouvelle tentative<br /><br /> **3** = annulée<br /><br />**4** = en cours|  
|**run_date**|**Int**|Date du début d'exécution du travail ou de l'étape. Pour l'historique des travaux en cours, date et heure de l'écriture de l'historique.|  
|**run_time**|**int**|Heure de début de l'étape ou du travail.|  
|**run_duration**|**int**|Temps écoulé dans l’exécution du travail ou de l’étape de **HHMMSS** format.|  
|**operator_id_emailed**|**int**|Identificateur de l'opérateur averti de la fin du travail.|  
|**operator_id_netsent**|**int**|Identificateur de l'opérateur averti par un message de la fin du travail.|  
|**operator_id_paged**|**Int**|Identificateur de l'opérateur averti par radiomessagerie de la fin du travail.|  
|**retries_attempted**|**int**|Nombre de nouvelles tentatives pour le travail ou l'étape.|  
|**server**|**sysname**|Nom du serveur sur lequel le travail a été exécuté.|  
  
  ## <a name="example"></a>Exemple
 Ce qui suit [!INCLUDE[tsql](../../includes/tsql-md.md)] requête convertira le **run_time** et **run_duration** colonnes dans un format plus convivial.  Exécutez le script dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 
 ```sql
 SET NOCOUNT ON;
 
 SELECT sj.name,
        sh.run_date,
        sh.step_name,
        STUFF(STUFF(RIGHT(REPLICATE('0', 6) +  CAST(sh.run_time as varchar(6)), 6), 3, 0, ':'), 6, 0, ':') 'run_time',
        STUFF(STUFF(STUFF(RIGHT(REPLICATE('0', 8) + CAST(sh.run_duration as varchar(8)), 8), 3, 0, ':'), 6, 0, ':'), 9, 0, ':') 'run_duration (DD:HH:MM:SS)  '
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobhistory sh
ON sj.job_id = sh.job_id
```
