---
title: dbo.sysoperators (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sysoperators
- dbo.sysoperators
- dbo.sysoperators_TSQL
- sysoperators_TSQL
dev_langs: TSQL
helpviewer_keywords: sysoperators system table
ms.assetid: c2afa20c-b15f-46ca-ae74-2eb65909409e
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0b48cdf057e17d0c043f2716071868b9188874d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysoperators-transact-sql"></a>dbo.sysoperators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque opérateur de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID de l’opérateur.|  
|**nom**|**sysname**|Nom de l’opérateur.|  
|**activé**|**tinyint**|État des notifications d'alerte (booléen). Si **1**, cet opérateur peut recevoir des notifications lorsqu’une alerte se produit.|  
|**email_address**|**nvarchar (100)**|Adresse de messagerie de cet opérateur.|  
|**last_email_date**|**int**|Date de la dernière notification d'alerte que cet opérateur a reçue par courrier électronique.|  
|**last_email_time**|**int**|Heure de la dernière notification d'alerte que cet opérateur a reçue par courrier électronique.|  
|**adresse_radiomessagerie**|**nvarchar (100)**|Adresse de radiomessagerie de cet opérateur.|  
|**last_pager_date**|**int**|Date de la dernière notification d'alerte que cet opérateur a reçue par radiomessagerie.|  
|**last_pager_time**|**int**|Heure de la dernière notification d'alerte que cet opérateur a reçue par radiomessagerie.|  
|**weekday_pager_start_time**|**int**|Première heure d'un jour ouvrable (du lundi au vendredi) à partir de laquelle l'opérateur peut recevoir des notifications d'alerte par radiomessagerie.|  
|**au vendredi**|**int**|Heure d'un jour ouvrable (du lundi au vendredi) après laquelle cet opérateur ne peut plus recevoir de notifications d'alerte par radiomessagerie.|  
|**heure_début_radiomessagerie_samedi**|**int**|Première heure, le samedi, à partir de laquelle l'opérateur peut recevoir des notifications d'alerte par radiomessagerie.|  
|**heure_fin_radiomessagerie_samedi**|**int**|Heure, le samedi, après laquelle cet opérateur ne peut plus recevoir de notifications d'alerte par radiomessagerie.|  
|**heure_début_radiomessagerie_dimanche**|**int**|Heure, le dimanche, à partir de laquelle l'opérateur peut recevoir des notifications d'alerte par radiomessagerie.|  
|**sunday_pager_end_time**|**int**|Heure, le dimanche, après laquelle cet opérateur ne peut plus recevoir de notifications d'alerte par radiomessagerie.|  
|**jours_radiomessagerie**|**tinyint**|Masque binaire représentant les jours de la semaine où l'opérateur peut recevoir des notifications d'alerte par radiomessagerie.|  
|**netsend_address**|**nvarchar (100)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**last_netsend_date**|**int**|Date à laquelle le dernier message réseau a été envoyé à l'ID d'opérateur spécifié.|  
|**last_netsend_time**|**int**|Heure à laquelle le dernier message réseau a été envoyé à l'ID d'opérateur spécifié.|  
|**code catégorie**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de l’Agent SQL Server &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
