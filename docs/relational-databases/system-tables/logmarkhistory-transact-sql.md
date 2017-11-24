---
title: logmarkhistory (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
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
- logmarkhistory
- logmarkhistory_TSQL
dev_langs: TSQL
helpviewer_keywords: logmarkhistory system table
ms.assetid: 5c1becc5-f34e-4869-bf69-dfafab684540
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dde90d07f786f5a9e164b0acc469c4e4552577d0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne par transaction marquée validée. Cette table est stockée dans le **msdb** base de données.  
  

|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar (128)**|Base de données locale dans laquelle une transaction marquée a été appliquée.|  
|**nom_marque**|**nvarchar (128)**|Nom, fourni par l'utilisateur, de la transaction marquée.|  
|**Description**|**nvarchar(255)**|Description, fournie par l'utilisateur, de la transaction marquée. Sa valeur peut être NULL.|  
|**nom_utilisateur**|**nvarchar (128)**|Nom de l'utilisateur de la base de données ayant appliqué la transaction marquée. Sa valeur peut être NULL.|  
|**LSN**|**NUMERIC(25,0)**|Numéro séquentiel dans le journal correspondant au marquage de l'enregistrement de la transaction.|  
|**mark_time**|**datetime**|Heure de validation de la transaction marquée (heure locale).|  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer une base de données jusqu’à une transaction marquée &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [Utiliser les transactions marquées pour récupérer des bases de données associées uniformément &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [Tables système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
