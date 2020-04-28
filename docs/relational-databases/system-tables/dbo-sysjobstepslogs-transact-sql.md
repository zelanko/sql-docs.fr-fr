---
title: dbo. sysjobstepslogs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobstepslogs_TSQL
- sysjobstepslogs_TSQL
- sysjobstepslogs
- dbo.sysjobstepslogs
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobstepslogs system table
ms.assetid: 128c25db-0b71-449d-bfb2-38b8abcf24a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: fec1b43f3e129a752e79024f3800d6f4fb3fb60a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67984927"
---
# <a name="dbosysjobstepslogs-transact-sql"></a>dbo.sysjobstepslogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient le journal des étapes de travail pour toutes les étapes de travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent configurées pour écrire la sortie des étapes dans une table. Cette table est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**log_id**|**int**|ID du journal d'étapes de travail.|  
|**Sign**|**nvarchar(max)**|Contenu du journal d'étapes de travail.|  
|**date_created**|**datetime**|Date et heure de création du journal d'étapes de travail.|  
|**date_modified**|**datetime**|Date et heure de la dernière modification du journal d'étapes de travail.|  
|**log_size**|**int**|Taille, en octets, du journal d'étapes de travail.|  
|**step_uid**|**uniqueidentifier**|Identificateur unique de l'étape de travail.|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_help_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)  
  
  
