---
title: sys. database_automatic_tuning_options (Transact-SQL) | Microsoft Docs
description: Découvrez comment afficher les options de réglage automatique sur un SQL Database
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 437dbbc4ea7deb32a9723febb443cc67941fdc5e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67940220"
---
# <a name="sysdatabase_automatic_tuning_options-transact-sql"></a>sys. Database\_tuning_options\_automatique (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Retourne les options de réglage automatique pour cette base de données.  

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nomme**|**nvarchar(128)**|Nom de l’option d’optimisation automatique. Reportez-vous à la rubrique [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) pour obtenir les options disponibles.|  
|**desired_state**|**smallint**|Indique le mode d’opération souhaité pour l’option de réglage automatique, défini explicitement par l’utilisateur.<br />0 = désactivé<br />1 = activé|  
|**desired_state_desc**|**nvarchar (60)**|Description textuelle du mode d’opération souhaité de l’option d’optimisation automatique.<br />OFF<br />ACTIVÉ|  
|**actual_state**|**smallint**|Indique le mode d’opération de l’option de réglage automatique.<br />0 = désactivé<br />1 = activé|  
|**actual_state_desc**|**nvarchar (60)**|Description textuelle du mode d’opération réel de l’option d’optimisation automatique.<br />OFF<br />ACTIVÉ|  
|**donc**|**smallint**|Indique pourquoi les États réels et souhaités sont différents.<br />2 = DÉSACTIVÉ<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar (60)**|Description textuelle de la raison pour laquelle les États réels et souhaités sont différents.<br />Disabled = l’option est désactivée par le système<br />QUERY_STORE_OFF = Magasin des requêtes est désactivé<br />QUERY_STORE_READ_ONLY = Magasin des requêtes est en mode lecture seule<br />NOT_SUPPORTED = disponible uniquement dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’édition Enterprise| 
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation `VIEW DATABASE STATE`.  
  
## <a name="see-also"></a>Voir aussi  
 [Réglage automatique](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys. database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys. dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
