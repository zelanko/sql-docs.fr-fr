---
title: sys.system_sql_modules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- system_sql_modules_TSQL
- sys.system_sql_modules
- sys.system_sql_modules_TSQL
- system_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_sql_modules catalog view
ms.assetid: ad3548bc-4780-4821-b962-b421d52daed9
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0462b231ee46a7e4ccce3bb498c6271d450c5e26
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85664325"
---
# <a name="syssystem_sql_modules-transact-sql"></a>sys.system_sql_modules (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asdw-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Renvoie une ligne par objet système qui contient un module défini par le langage SQL. Les objets système de type FN, IF, P, PC, TF, V sont associés à un module SQL. Pour identifier l’objet conteneur, vous pouvez joindre cette vue à [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Numéro d'identification de l'objet conteneur, unique dans une base de données.|  
|**définition**|**nvarchar(max)**|Texte SQL qui définit ce module.|  
|**uses_ansi_nulls**|**bit**|1 = Le module a été créé lorsque l'option de base de données SET ANSI_NULLS était activée (ON).<br /><br /> Retourne toujours 1.|  
|**uses_quoted_identifier**|**bit**|1 = Le module a été créé avec l'instruction SET QUOTED_IDENTIFIER ON.<br /><br /> Retourne toujours 1.|  
|**is_schema_bound**|**bit**|0 = Le module n'a pas été créé avec l'option SCHEMABINDING.<br /><br /> Retourne toujours 0.|  
|**uses_database_collation**|**bit**|0 = Le module ne dépend pas du classement par défaut de la base de données.<br /><br /> Retourne toujours 0.|  
|**is_recompiled**|**bit**|0 = La procédure n'a pas été créée en utilisant l'option WITH RECOMPILE.<br /><br /> Retourne toujours 0.|  
|**null_on_null_input**|**bit**|0 = Le module n'a pas été créé pour produire un résultat NULL pour toute entrée NULL.<br /><br /> Retourne toujours 0.|  
|**execute_as_principal_id**|**int**|Retourne toujours la valeur NULL|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys. all_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql.md)   
 [Affichages catalogue &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
