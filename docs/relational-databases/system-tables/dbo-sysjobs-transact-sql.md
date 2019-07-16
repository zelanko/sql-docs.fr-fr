---
title: dbo.sysjobs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobs
- sysjobs_TSQL
- dbo.sysjobs
- dbo.sysjobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobs system table
ms.assetid: e244a6a5-54c2-47a6-8039-dd1852b0ae59
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3ea2b3196e159b19a1baaa032c622a4cf9132402
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097603"
---
# <a name="dbosysjobs-transact-sql"></a>dbo.sysjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stocke les informations de chaque travail planifié qui doit être exécuté par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID unique de la tâche.|  
|**originating_server_id**|**int**|ID du serveur d'où le travail provient.|  
|**name**|**sysname**|Nom du travail.|  
|**enabled**|**tinyint**|Indique si le travail est activé pour être exécuté.|  
|**description**|**nvarchar(512)**|Description pour le travail.|  
|**start_step_id**|**Int**|Identificateur de l'étape du travail à partir de laquelle l'exécution doit débuter.|  
|**category_id**|**Int**|ID de la catégorie du travail.|  
|**owner_sid**|**varbinary(85)**|Numéro d'identification de sécurité (SID) du propriétaire du travail.|  
|**notify_level_eventlog**|**Int**|**Masque de bits** qui indique dans quelles circonstances un événement de notification doit être journalisé dans le journal des applications Microsoft Windows :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_level_email**|**int**|Masque binaire indiquant les circonstances entraînant l'envoi d'un courrier électronique en fin de travail :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_level_netsend**|**Int**|Masque binaire indiquant les circonstances entraînant l'envoi d'un message sur le réseau en fin de travail :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_level_page**|**int**|Masque binaire indiquant les circonstances entraînant l'envoi d'un message par radiomessagerie en fin de travail :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**notify_email_operator_id**|**Int**|Nom d'adresse électronique de l'opérateur à avertir.|  
|**notify_netsend_operator_id**|**int**|ID de l'ordinateur ou de l'utilisateur utilisé pour envoyer les messages sur le réseau.|  
|**notify_page_operator_id**|**int**|ID de l'ordinateur ou de l'utilisateur utilisé pour envoyer un radiomessage.|  
|**delete_level**|**Int**|**Masque de bits** qui indique dans quelles circonstances le travail doit être supprimé à l’issue de l’exécution d’un travail :<br /><br /> **0** = jamais<br /><br /> **1** = lors de la réussite du travail<br /><br /> **2** = lors de l’échec du travail<br /><br /> **3** = chaque fois que le travail est terminé (quel que soit le résultat du travail)|  
|**date_created**|**datetime**|Date de que création du travail.|  
|**date_modified**|**datetime**|Date de dernière modification du travail.|  
|**version_number**|**Int**|Version du travail.|  
  
  
