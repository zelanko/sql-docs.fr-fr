---
title: sys. pdw_permanent_table_mappings (Transact-SQL)
ms.custom: ''
ms.date: 07/24/2020
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: mstehrani
ms.author: emtehran
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: c48cb981549d47b24152772cef9278de6557612f
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89062258"
---
# <a name="syspdw_permanent_table_mappings-transact-sql"></a>sys. pdw_permanent_table_mappings (Transact-SQL)
[!INCLUDE [applies-to-version/asa](../../includes/applies-to-version/asa.md)]

  Lie les tables utilisateur permanentes aux noms d’objets internes en **object_id**.  
  
> [!NOTE]
> **sys. pdw_permanent_table_mappings** contient des mappages à des tables permanentes et n’inclut pas de mappages de tables temporaires ou externes.

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|physical_name|**nvarchar (36)**|Nom physique de la table.<br /><br /> **physical_name** et **object_id** forment la clé de cette vue.||  
|object_id|**int**|ID d’objet de la table. Consultez [sys. objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **physical_name** et **object_id** forment la clé de cette vue.||  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys. pdw_index_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)  
  
  
