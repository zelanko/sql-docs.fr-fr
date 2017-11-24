---
title: MSrepl_originators (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- MSrepl_originators_TSQL
- MSrepl_originators
dev_langs: TSQL
helpviewer_keywords: MSrepl_originators system table
ms.assetid: a3ac20a6-73f6-4fdc-ad5f-5f72746c9871
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7fca669ba119dba475b39d41b657815a854836d4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="msreploriginators-transact-sql"></a>MSrepl_originators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSrepl_originators** table contient une ligne pour chaque abonné de mettre à jour à partir de laquelle la transaction a débuté. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifie l'Abonné associé à la mise à jour|  
|**publisher_database_id**|**int**|Identifie la base de données de publication.|  
|**SRVNAME**|**sysname**|Nom du serveur de mise à jour.|  
|**dbname**|**sysname**|Nom de la base de données de mise à jour.|  
|**id_de_la_publication**|**int**|Identifie la publication.|  
|**dbversion**|**int**|Identifie la version de base de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
