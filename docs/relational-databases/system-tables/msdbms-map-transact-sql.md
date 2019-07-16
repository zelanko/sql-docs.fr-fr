---
title: MSdbms_map (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_map
- MSdbms_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_map system table
ms.assetid: df67e691-3a50-450a-99c5-8c4a041749ae
author: stevestein
ms.author: sstein
ms.openlocfilehash: fffa30d0e252392c41cee34c1875b12b5b7a53b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67907488"
---
# <a name="msdbmsmap-transact-sql"></a>MSdbms_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSdbms_map** table contient des informations de type de données source, ainsi qu’un lien aux informations de type de données de destination par défaut pour les paires DBMS source et de destination. Cette table est stockée dans le **msdb** de base de données et est utilisé pour la publication hétérogène.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**map_id**|**int**|Identifie de manière unique un mappage de type de données.|  
|**src_dbms_id**|**Int**|Identifie la source DBMS en spécifiant son **ID DBMS** dans le [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) table.|  
|**dest_dbms_id**|**int**|Identifie le SGBD de destination en spécifiant son **ID DBMS** dans le [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) table.|  
|**src_datatype_id**|**int**|Identifie le **datatype_id** à partir de la [MSdbms_datatype](../../relational-databases/system-tables/msdbms-datatype-transact-sql.md) table pour le type de données source.|  
|**src_len_min**|**bigint**|Longueur minimale du type de données dans la source DBMS, où une valeur NULL indique que la longueur n'est pas utilisée.|  
|**src_len_max**|**bigint**|Longueur maximale du type de données dans la source DBMS, où une valeur NULL indique que la longueur n'est pas utilisée.|  
|**src_prec_min**|**bigint**|Précision minimale du type de données dans la source DBMS, où une valeur NULL indique que la précision n'est pas utilisée.|  
|**src_prec_max**|**bigint**|Précision maximale du type de données dans la source DBMS, où une valeur NULL indique que la précision n'est pas utilisée.|  
|**src_scale_min**|**Int**|Échelle minimale du type de données dans la source DBMS, où une valeur NULL indique que l'échelle n'est pas utilisée.|  
|**src_scale_max**|**Int**|Échelle maximale du type de données dans la source DBMS, où une valeur NULL indique que l'échelle n'est pas utilisée.|  
|**src_nullable**|**bit**|Indique si la colonne de destination dans le mappage autorise les valeurs NULL, où une valeur NULL signifie que cette définition n'est pas requise.|  
|**default_datatype_mapping_id**|**int**|Identifie le mappage de type de données par défaut en spécifiant son **map_id** dans la table [MSdbms_datatype_mapping](../../relational-databases/system-tables/msdbms-datatype-mapping-transact-sql.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Spécifier des mappages de types de données pour un serveur de publication Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
