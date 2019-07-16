---
title: sysreplicationalerts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysreplicationalerts_TSQL
- sysreplicationalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysreplicationalerts system table
ms.assetid: 6ed15828-8cca-4cf0-b2ff-1ecd0d8db11a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6cbeab4c673390cb80300eb5ced2b4cb5c1bcf1f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029743"
---
# <a name="sysreplicationalerts-transact-sql"></a>sysreplicationalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations sur les conditions déclenchant une alerte de réplication. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|Identificateur de l'alerte.|  
|**status**|**int**|Valeur définie par l'utilisateur :<br /><br /> **0** = non traitée.<br /><br /> **1** = pris en charge.|  
|**agent_type**|**Int**|Type d'agent :<br /><br /> **1** = Agent d’instantané.<br /><br /> **2** = Agent de lecture du journal.<br /><br /> **3** = Agent de distribution.<br /><br /> **4** = Agent de fusion.|  
|**agent_id**|**int**|L’ID d’agent à partir des tables **MSsnapshot_agents**, **MSlogreader_agents**, **MSdistribution_agents**, ou **MSmerge_agents**.|  
|**error_id**|**int**|L’ID de l’erreur stockée dans **MSrepl_errors**.|  
|**alert_error_code**|**int**|ID de message de l'alerte déclenchée lors de l'écriture de cet enregistrement dans le journal.|  
|**time**|**datetime**|Date et heure d'insertion de l'enregistrement.|  
|**publisher** (serveur de publication)|**sysname**|Nom du serveur de publication associé à l'Agent qui a déclenché l'alerte.|  
|**publisher_db**|**sysname**|Base de données du serveur de publication associée à l'Agent qui a déclenché l'alerte.|  
|**publication**|**sysname**|Publication associée à l'Agent qui a déclenché l'alerte.|  
|**publication_type**|**int**|Type de publication :<br /><br /> **0** = instantané.<br /><br /> **1** = transactionnelle.<br /><br /> **2** = fusion.|  
|**subscriber** (Abonné)|**sysname**|Nom de l'Abonné associé à l'Agent qui a déclenché l'alerte.|  
|**bd_abonné**|**sysname**|Nom de la base de données de l'Abonné associée à l'Agent qui a déclenché l'alerte.|  
|**article**|**sysname**|Nom de l'article associé à l'Agent qui a déclenché l'alerte.|  
|**destination_object**|**sysname**|Nom de la table d'abonnement associée à l'alerte.|  
|**source_object**|**sysname**|Nom de la table publiée associée à l'alerte.|  
|**alert_error_text**|**ntext**|Texte de l'alerte.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
