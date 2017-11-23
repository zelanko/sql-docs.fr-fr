---
title: Sys.partition_parameters (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- partition_parameters_TSQL
- partition_parameters
- sys.partition_parameters_TSQL
- sys.partition_parameters
dev_langs: TSQL
helpviewer_keywords: sys.partition_parameters catalog view
ms.assetid: 2012ed9d-3ea3-4c29-9b78-dfa54a392dce
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ea75798552d0521204e063663566b08b36a5797b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="syspartitionparameters-transact-sql"></a>sys.partition_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Contient une ligne pour chaque paramètre d'une fonction de partition.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**function_id supérieures**|**int**|Identificateur de la fonction de partition à laquelle appartient ce paramètre.|  
|**parameter_id**|**int**|ID du paramètre. Unique au sein de la fonction de partition, en commençant par 1.|  
|**system_type_id**|**tinyint**|Identificateur du type système du paramètre. Correspond à la **system_type_id** colonne de la **sys.types** affichage catalogue.|  
|**max_length**|**smallint**|Longueur maximale du paramètre, en octets.|  
|**précision**|**tinyint**|Précision du paramètre s'il est de type numérique ; sinon, 0.|  
|**mise à l’échelle**|**tinyint**|Échelle du paramètre s'il est de type numérique ; sinon, 0.|  
|**collation_name**|**sysname**|Nom du classement du paramètre s'il est constitué de caractères alphanumériques, sinon NULL.|  
|**user_type_id**|**int**|ID du type. Unique dans la base de données. Pour les types de données système **user_type_id** = **system_type_id**.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue des fonctions de partition &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Sys.partition_functions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [Sys.partition_range_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)  
  
  
