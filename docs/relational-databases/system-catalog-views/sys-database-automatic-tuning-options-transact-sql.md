---
title: Sys.database_automatic_tuning_options (Transact-SQL) | Microsoft Docs
description: Découvrez comment afficher les options de réglage automatique sur une base de données SQL
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_automatic_tuning_options_tsql
- database_automatic_tuning_options
- sys.database_automatic_tuning_options_tsql
- sys.database_automatic_tuning_options
dev_langs:
- TSQL
helpviewer_keywords:
- database_automatic_tuning_options catalog view
- sys.database_automatic_tuning_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
caps.latest.revision: 24
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 6a9fc30a86c3033264dc723de282caffd03289fd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38065399"
---
# <a name="sysdatabaseautomatictuningoptions-transact-sql"></a>Sys.Database\_automatique\_tuning_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Retourne les options de réglage automatique pour cette base de données.  

|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**nvarchar(128)**|Le nom de l’option de réglage automatique. Reportez-vous à [AUTOMATIC_TUNING de définir de base de données ALTER &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) pour les options disponibles.|  
|**desired_state**|**smallint**|Indique le mode de fonctionnement souhaité pour l’option d’optimisation automatique, définissez explicitement par l’utilisateur.<br />0 = désactivé<br />1 = activé|  
|**desired_state_desc**|**nvarchar(60)**|Description textuelle du mode de fonctionnement souhaité de l’option d’optimisation automatique.<br />OFF<br />ON|  
|**actual_state**|**smallint**|Indique le mode de fonctionnement de l’option d’optimisation automatique.<br />0 = désactivé<br />1 = activé|  
|**actual_state_desc**|**nvarchar(60)**|Description textuelle du mode de fonctionnement réel de l’option d’optimisation automatique.<br />OFF<br />ON|  
|**raison**|**smallint**|Indique pourquoi États souhaitées et réels sont différents.<br />2 = DÉSACTIVÉ<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar(60)**|Description textuelle de la raison pour laquelle les États souhaitées et réels sont différents.<br />DÉSACTIVÉ = Option est désactivée par le système<br />QUERY_STORE_OFF = Query Store est mis hors tension<br />QUERY_STORE_READ_ONLY = Store de la requête est en mode lecture seule<br />NOT_SUPPORTED = disponible uniquement dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition| 
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation `VIEW DATABASE STATE`.  
  
## <a name="see-also"></a>Voir aussi  
 [Le réglage automatique](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
