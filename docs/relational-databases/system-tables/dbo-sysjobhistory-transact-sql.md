---
title: dbo.sysjobhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2016
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
manager: craigg
ms.openlocfilehash: 1797fb6183863bb0249bd0cda6024d0e95914e82
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470847"
---
# <a name="dbosysjobhistory-transact-sql"></a>dbo.sysjobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations sur l'exécution des travaux planifiés par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans le **msdb** base de données.  
  
> **REMARQUE :** Données sont mis à jour seulement après l’achèvement de l’étape de travail.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**Int**|Identificateur unique de la ligne.|  
|**job_id**|**uniqueidentifier**|ID de travail.|  
|**step_id**|**Int**|ID de l'étape dans le travail|  
|**step_name**|**sysname**|Nom de l'étape|  
|**sql_message_id**|**Int**|Identificateur de tout message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourné en cas d'échec du travail.|  
|**sql_severity**|**Int**|Gravité des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**message**|**nvarchar(4000)**|Texte éventuel d'une erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**run_status**|**Int**|État de l'exécution du travail :<br /><br /> **0** = Échec<br /><br /> **1** = a réussi<br /><br /> **2** = Retry<br /><br /> **3** = annulée<br /><br /> **4** = en cours|  
|**run_date**|**Int**|Date du début d'exécution du travail ou de l'étape. Pour l'historique des travaux en cours, date et heure de l'écriture de l'historique.|  
|**run_time**|**Int**|Heure de début de l'étape ou du travail.|  
|**run_duration**|**Int**|Temps écoulé dans l’exécution du travail ou de l’étape de **HHMMSS** format.|  
|**operator_id_emailed**|**Int**|Identificateur de l'opérateur averti de la fin du travail.|  
|**operator_id_netsent**|**Int**|Identificateur de l'opérateur averti par un message de la fin du travail.|  
|**operator_id_paged**|**Int**|Identificateur de l'opérateur averti par radiomessagerie de la fin du travail.|  
|**retries_attempted**|**Int**|Nombre de nouvelles tentatives pour le travail ou l'étape.|  
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
