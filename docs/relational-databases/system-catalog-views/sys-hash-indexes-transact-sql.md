---
title: sys.hash_indexes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.hash_indexes_TSQL
- hash_indexes
- sys.hash_indexes
- hash_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.hash_indexes catalog view
ms.assetid: d9e230fb-d3ff-486f-86ef-44898f0a703e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 99e3a647c55380e1731b97c267eb754a1f3c6a32
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122740"
---
# <a name="syshashindexes-transact-sql"></a>sys.hash_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indique les index de hachage actuels et leurs propriétés. Index de hachage sont pris en charge uniquement sur [In-Memory OLTP &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
 La vue sys.hash_indexes contient les mêmes colonnes que la vue sys.indexes et une colonne supplémentaire nommée **bucket_count**. Pour plus d’informations sur les autres colonnes dans la vue sys.hash_indexes, consultez [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**\<héritée de colonnes >**||Hérite des colonnes de [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).|  
|**bucket_count**|**Int**|Nombre de compartiments de hachage pour les index de hachage.<br /><br /> Pour plus d’informations sur la valeur de bucket_count, notamment les instructions pour définir la valeur, consultez [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Exemples  
  
```  
SELECT object_name([object_id]) AS 'table_name', [object_id],  
     [name] AS 'index_name', [type_desc], [bucket_count]   
FROM sys.hash_indexes   
WHERE OBJECT_NAME([object_id]) = 'T1';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
