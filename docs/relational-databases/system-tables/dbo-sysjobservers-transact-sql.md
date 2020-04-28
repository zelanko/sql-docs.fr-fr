---
title: dbo. sysjobservers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/26/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03a4457cb5dd087639a439e9e9bb883eaf924366
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70026204"
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Stocke les associations ou les relations existant entre un travail particulier et un ou plusieurs serveurs cibles. Cette table est stockée dans la base de données msdb.
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|Numéro d’identification du travail.|  
|server_id|**int**|Numéro d’identification du serveur.|  
|last_run_outcome|**tinyint**|Issue de la dernière exécution du travail :<br /><br /> **0** = échec<br /><br /> **1** = opération réussie<br /><br /> **2** = nouvelle tentative<br /><br /> **3** = annuler<br /><br /> **4** = en cours<br /><br /> **5** = Unknown (voir la section Notes suivante) |  
|last_outcome_ message|**nvarchar(1024)**|Message associé, le cas échéant, à la colonne last_run_outcome.|  
|last_run_date|**int**|Date de la dernière exécution du travail.|  
|last_run_time|**int**|Heure de la dernière exécution du travail.|  
|last_run_duration|**int**|Durée d'exécution du travail, en heures, minutes et secondes. Calculé à l’aide de la formule suivante : (*heures*\*10000) + (*minutes*\*100) + *secondes*.|  


## <a name="remarks"></a>Notes

Une valeur supérieure à *4* signifie que l’agent SQL ne connaît pas l’état de ce travail. La *last_run_outcome* est initialement définie sur *5* lorsqu’un travail est créé.


## <a name="see-also"></a>Voir aussi

[Tables SQL Server Agent &#40;&#41;Transact-SQL](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
