---
title: Sys.all_sql_modules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- all_sql_modules_TSQL
- sys.all_sql_modules
- all_sql_modules
- sys.all_sql_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_sql_modules catalog view
ms.assetid: 7477a3fe-afb3-44c8-bb2c-c6e1d9bdee6f
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 49d2ae259d2c91316a8134a7a92c39b73673d897
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001313"
---
# <a name="sysallsqlmodules-transact-sql"></a>sys.all_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne l’union de **sys.sql_modules** et **sys.system_sql_modules**.  
  
 La vue retourne une ligne pour chaque fonction définie par l’utilisateur compilée en mode natif, scalaire. Pour plus d’informations, consultez [Fonctions scalaires définies par l’utilisateur pour l’OLTP en mémoire](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|ID d'objet de l'objet conteneur. Unique dans une base de données.|  
|**definition**|**nvarchar(max)**|Texte SQL qui définit ce module.<br /><br /> NULL = chiffré|  
|**uses_ansi_nulls**|**bit**|Le module a été créé avec SET ANSI_NULLS ON.|  
|**uses_quoted_identifier**|**bit**|Le module a été créé avec SET QUOTED_IDENTIFIER ON.|  
|**is_schema_bound**|**bit**|Le module a été créé avec l'option SCHEMABINDING.|  
|**uses_database_collation**|**bit**|1 = La définition d'un module lié au schéma dépend du classement par défaut de la base de données pour une évaluation correcte ; dans tous les autres cas, 0. Une telle dépendance permet d'éviter le changement du classement par défaut de la base de données.|  
|**is_recompiled**|**bit**|La procédure a été créée avec l'option WITH RECOMPILE.|  
|**null_on_null_input**|**bit**|Le module a été déclaré pour produire une sortie NULL sur n'importe quelle entrée NULL.|  
|**execute_as_principal_id**|**int**|ID du principal de base de données EXECUTE AS.<br /><br /> Valeur NULL par défaut ou dans le cas de l'instruction EXECUTE AS CALLER.<br /><br /> ID du principal spécifié si EXECUTE AS SELF ou EXECUTE AS \<principal >.<br /><br /> -2 = EXECUTE AS OWNER.|  
|**uses_native_compilation**|bit|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = Non compilé en mode natif<br /><br /> 1 = Compilé en mode natif<br /><br /> La valeur par défaut est 0.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Sys.system_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-sql-modules-transact-sql.md)   
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
