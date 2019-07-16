---
title: Sys.masked_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e059265dc5f5e0d2e4bc4a3b1396d2401386d7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102374"
---
# <a name="sysmaskedcolumns-transact-sql"></a>Sys.masked_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Utilisez le **sys.masked_columns** vue pour interroger des colonnes de table qui ont une fonction est appliquée de masquage de données dynamiques. Celle-ci hérite de la vue **sys.columns** . Elle retourne toutes les colonnes de la vue **sys.columns** , ainsi que les colonnes **is_masked** et **masking_function** , en indiquant si les colonnes sont masquées et, dans ce cas, la fonction de masquage est définie. Cette vue présente uniquement les colonnes auxquelles une fonction de masquage est appliquée.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Identificateur de l'objet auquel appartient cette colonne.|  
|name|**sysname**|Nom de la colonne. Unique dans l'objet.|  
|column_id|**int**|ID de la colonne. Unique dans l'objet.<br /><br /> Les ID de colonnes peuvent ne pas être séquentiels.|  
|**Sys.masked_columns** retourne plus de colonnes héritées de **sys.columns**.|divers|Consultez [sys.columns &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) pour plusieurs définitions de colonne.|  
|is_masked|**bit**|Indique si la colonne est masquée. 1 indique masqué.|  
|masking_function|**nvarchar(4000)**|La fonction de masquage pour la colonne.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="permissions"></a>Autorisations  
 Cette vue retourne des informations sur les tables où l’utilisateur possède une autorisation sur la table ou si l’utilisateur a l’autorisation VIEW ANY DEFINITION.  
  
## <a name="example"></a>Exemple  
 La requête suivante jointures **sys.masked_columns** à **sys.tables** pour retourner des informations relatives à tous les masquées colonnes.  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Dynamic Data Masking](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
