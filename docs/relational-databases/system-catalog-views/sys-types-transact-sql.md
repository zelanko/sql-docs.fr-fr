---
title: Sys.types (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- types
- types_TSQL
- sys.types_TSQL
- sys.types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.types catalog view
- table-valued parameters,sys.types
ms.assetid: a5dbc842-71a0-4f62-b5e0-f560a99b7f8c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0fab5cee5706b0d8a00638f35c3b91d639efb3b6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systypes-transact-sql"></a>sys.types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne par type système et par type défini par l'utilisateur.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du type. Est unique dans le schéma.|  
|**system_type_id**|**tinyint**|ID du type de système interne du type.|  
|**user_type_id**|**int**|ID du type. Unique dans la base de données. Pour les types de données système **user_type_id** = **system_type_id**.|  
|**schema_id**|**int**|Identificateur du schéma auquel appartient le type.|  
|**principal_id**|**int**|ID du propriétaire spécifique s'il diffère du propriétaire du schéma. Par défaut, le propriétaire du schéma détient les objets contenus dans le schéma. Cependant, il est possible de spécifier un autre propriétaire à l'aide de l'instruction ALTER AUTHORIZATION qui permet de changer de propriétaire.<br /><br /> La valeur est NULL en l'absence de propriétaire de remplacement spécifique.|  
|**max_length**|**smallint**|Longueur maximale (en octets) du type.<br /><br /> -1 = la colonne est de type de données **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, ou **xml**.<br /><br /> Pour **texte** des colonnes, le **max_length** valeur sera 16.|  
|**précision**|**tinyint**|Précision maximale du type s'il est basé sur un nombre ; sinon, 0.|  
|**mise à l’échelle**|**tinyint**|Échelle maximale du type s'il est de type numérique ; sinon, 0.|  
|**collation_name**|**sysname**|Nom du classement du type s’il est de type caractère ; autres wise, NULL.|  
|**is_nullable**|**bit**|Le type accepte les valeurs NULL.|  
|**is_user_defined**|**bit**|1 = type défini par l'utilisateur.<br /><br /> 0 = type de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**is_assembly_type**|**bit**|1 = l'implémentation du type est définie dans un assembly CLR.<br /><br /> 0 = le type est basé sur un type de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**default_object_id**|**int**|ID de la valeur par défaut autonome liée au type à l’aide de [sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md).<br /><br /> 0 = aucune valeur par défaut n'existe.|  
|**rule_object_id**|**int**|ID de la règle autonome liée au type à l’aide de [sp_bindrule](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md).<br /><br /> 0 = aucune règle n'existe.|  
|**is_table_type**|**bit**|Indique que le type est une table.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue &#40; de Types scalaires Transact-SQL &#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
