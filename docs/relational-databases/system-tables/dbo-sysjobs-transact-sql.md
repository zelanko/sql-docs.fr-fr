---
title: dbo.sysjobs (Transact-SQL) | Documents Microsoft
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
- sysjobs
- sysjobs_TSQL
- dbo.sysjobs
- dbo.sysjobs_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobs system table
ms.assetid: e244a6a5-54c2-47a6-8039-dd1852b0ae59
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1fd6e90a9e823e38a83f5b218027e15183ab76ae
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobs-transact-sql"></a>dbo.sysjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stocke les informations de chaque travail planifié qui doit être exécuté par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID unique du travail.|  
|**originating_server_id**|**int**|ID du serveur d'où le travail provient.|  
|**nom**|**sysname**|Nom du travail.|  
|**activé**|**tinyint**|Indique si le travail est activé pour être exécuté.|  
|**Description**|**nvarchar(512)**|Description de la tâche.|  
|**start_step_id**|**int**|Identificateur de l'étape du travail à partir de laquelle l'exécution doit débuter.|  
|**code catégorie**|**int**|ID de la catégorie du travail.|  
|**owner_sid**|**varbinary(85)**|Numéro d'identification de sécurité (SID) du propriétaire du travail.|  
|**notify_level_eventlog**|**int**|**Masque de bits** qui indique dans quelles circonstances un événement de notification doit être enregistré dans le journal des applications Microsoft Windows :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_level_email**|**int**|Masque binaire indiquant les circonstances entraînant l'envoi d'un courrier électronique en fin de travail :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_level_netsend**|**int**|Masque binaire indiquant les circonstances entraînant l'envoi d'un message sur le réseau en fin de travail :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_level_page**|**int**|Masque binaire indiquant les circonstances entraînant l'envoi d'un message par radiomessagerie en fin de travail :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_email_operator_id**|**int**|Nom d'adresse électronique de l'opérateur à avertir.|  
|**notify_netsend_operator_id**|**int**|ID de l'ordinateur ou de l'utilisateur utilisé pour envoyer les messages sur le réseau.|  
|**notify_page_operator_id**|**int**|ID de l'ordinateur ou de l'utilisateur utilisé pour envoyer un radiomessage.|  
|**niveau_suppression**|**int**|**Masque de bits** qui indique dans quelles circonstances le travail doit être supprimé lorsqu’une tâche est terminée :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**date_de_création**|**datetime**|Date de que création du travail.|  
|**date_de_modification**|**datetime**|Date de dernière modification du travail.|  
|**numéro_version**|**int**|Version de la tâche.|  
  
  
