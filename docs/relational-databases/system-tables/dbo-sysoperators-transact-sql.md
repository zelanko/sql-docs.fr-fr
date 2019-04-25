---
title: dbo.sysoperators (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysoperators
- dbo.sysoperators
- dbo.sysoperators_TSQL
- sysoperators_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoperators system table
ms.assetid: c2afa20c-b15f-46ca-ae74-2eb65909409e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3796714cbdfb55900447bf23904136ac5abefa9c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470655"
---
# <a name="dbosysoperators-transact-sql"></a>dbo.sysoperators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque opérateur de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|ID de l’opérateur.|  
|**nom**|**sysname**|Nom de l’opérateur.|  
|**enabled**|**tinyint**|État des notifications d'alerte (booléen). Si **1**, cet opérateur peut recevoir des notifications lorsqu’une alerte se produit.|  
|**email_address**|**nvarchar(100)**|Adresse de messagerie de cet opérateur.|  
|**last_email_date**|**Int**|Date de la dernière notification d'alerte que cet opérateur a reçue par courrier électronique.|  
|**last_email_time**|**Int**|Heure de la dernière notification d'alerte que cet opérateur a reçue par courrier électronique.|  
|**pager_address**|**nvarchar(100)**|Adresse de radiomessagerie de cet opérateur.|  
|**last_pager_date**|**Int**|Date de la dernière notification d'alerte que cet opérateur a reçue par radiomessagerie.|  
|**last_pager_time**|**Int**|Heure de la dernière notification d'alerte que cet opérateur a reçue par radiomessagerie.|  
|**weekday_pager_start_time**|**Int**|Première heure d'un jour ouvrable (du lundi au vendredi) à partir de laquelle l'opérateur peut recevoir des notifications d'alerte par radiomessagerie.|  
|**weekday_pager_end_time**|**Int**|Heure d'un jour ouvrable (du lundi au vendredi) après laquelle cet opérateur ne peut plus recevoir de notifications d'alerte par radiomessagerie.|  
|**saturday_pager_start_time**|**Int**|Première heure, le samedi, à partir de laquelle l'opérateur peut recevoir des notifications d'alerte par radiomessagerie.|  
|**saturday_pager_end_time**|**Int**|Heure, le samedi, après laquelle cet opérateur ne peut plus recevoir de notifications d'alerte par radiomessagerie.|  
|**sunday_pager_start_time**|**Int**|Heure, le dimanche, à partir de laquelle l'opérateur peut recevoir des notifications d'alerte par radiomessagerie.|  
|**sunday_pager_end_time**|**Int**|Heure, le dimanche, après laquelle cet opérateur ne peut plus recevoir de notifications d'alerte par radiomessagerie.|  
|**pager_days**|**tinyint**|Masque binaire représentant les jours de la semaine où l'opérateur peut recevoir des notifications d'alerte par radiomessagerie.|  
|**netsend_address**|**nvarchar(100)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**last_netsend_date**|**Int**|Date à laquelle le dernier message réseau a été envoyé à l'ID d'opérateur spécifié.|  
|**last_netsend_time**|**Int**|Heure à laquelle le dernier message réseau a été envoyé à l'ID d'opérateur spécifié.|  
|**category_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de l’Agent SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
