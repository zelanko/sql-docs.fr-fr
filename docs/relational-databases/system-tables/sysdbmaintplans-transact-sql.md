---
title: sysdbmaintplans (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdbmaintplans_TSQL
- sysdbmaintplans
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplans system table
ms.assetid: 0363296a-3082-48a9-9eb5-a1020b2f541a
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9d4f8b7c90d644cb9153bf716e91c38c56bee7f0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sysdbmaintplans-transact-sql"></a>sysdbmaintplans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette table est incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour conserver les informations existantes pour les instances mises à niveau à partir d’une version antérieure de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne modifie pas le contenu de cette table. Cette table est stockée dans le **msdb** base de données.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  

  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|Identificateur du plan de maintenance de la base de données.|  
|**plan_name**|**sysname**|Nom du plan de maintenance de base de données.|  
|**date_created**|**datetime**|Date de création du plan de maintenance de base de données.|  
|**propriétaire**|**sysname**|Propriétaire du plan de maintenance de base de données.|  
|**max_history_rows**|**int**|Nombre maximal de lignes allouées à l'enregistrement de l'historique du plan de maintenance de base de données dans la table système.|  
|**remote_history_server**|**sysname**|Nom du serveur distant sur lequel le rapport de l'historique peut être écrit.|  
|**max_remote_history_rows**|**int**|Nombre maximal de lignes allouées dans la table système d'un serveur distant dans laquelle le rapport de l'historique peut être écrit.|  
|**user_defined_1**|**int**|La valeur par défaut est NULL.|  
|**user_defined_2**|**nvarchar(100)**|La valeur par défaut est NULL.|  
|**user_defined_3**|**datetime**|La valeur par défaut est NULL.|  
|**user_defined_4**|**uniqueidentifier**|La valeur par défaut est NULL.|  
|**log_shipping**|**bit**|État de l'envoi de journaux :<br /><br /> **0** = désactivé **1** = activé|  
  
  
