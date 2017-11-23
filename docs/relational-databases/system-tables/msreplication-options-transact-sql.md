---
title: MSreplication_options (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSreplication_options
- MSreplication_options_TSQL
dev_langs: TSQL
helpviewer_keywords: MSreplication_options system table
ms.assetid: 23cf10d7-8bc1-4368-b5eb-e5576421e776
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5711a1f0de3f335867c3b5162a4ec77f52d79dfc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="msreplicationoptions-transact-sql"></a>MSreplication_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSreplication_options** table stocke les métadonnées qui sont utilisée en interne par la réplication. Cette table est stockée dans le **master** base de données.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**nom_option**|**sysname**|À usage interne uniquement|  
|**valeur**|**bit**|À usage interne uniquement|  
|**version_principale**|**int**|À usage interne uniquement|  
|**version_secondaire**|**int**|À usage interne uniquement|  
|**révision**|**int**|À usage interne uniquement|  
|**install_failures**|**int**|À usage interne uniquement|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
