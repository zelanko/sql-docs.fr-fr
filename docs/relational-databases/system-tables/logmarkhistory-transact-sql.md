---
title: logmarkhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- logmarkhistory
- logmarkhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logmarkhistory system table
ms.assetid: 5c1becc5-f34e-4869-bf69-dfafab684540
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0674bf993087b349d4e8b6f9947c65167e94df8e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001803"
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne par transaction marquée validée. Cette table est stockée dans le **msdb** base de données.  
  

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Base de données locale dans laquelle une transaction marquée a été appliquée.|  
|**nom_marque**|**nvarchar(128)**|Nom, fourni par l'utilisateur, de la transaction marquée.|  
|**description**|**nvarchar(255)**|Description, fournie par l'utilisateur, de la transaction marquée. Sa valeur peut être NULL.|  
|**user_name**|**nvarchar(128)**|Nom de l'utilisateur de la base de données ayant appliqué la transaction marquée. Sa valeur peut être NULL.|  
|**LSN**|**numeric(25,0)**|Numéro séquentiel dans le journal correspondant au marquage de l'enregistrement de la transaction.|  
|**mark_time**|**datetime**|Heure de validation de la transaction marquée (heure locale).|  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer une base de données jusqu’à une transaction marquée &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [Utiliser les transactions marquées pour récupérer des bases de données associées uniformément &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [Tables système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
