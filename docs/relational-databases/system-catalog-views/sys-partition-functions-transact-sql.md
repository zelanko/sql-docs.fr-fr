---
title: Sys.partition_functions (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.partition_functions_TSQL
- partition_functions
- sys.partition_functions
- partition_functions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_functions catalog view
ms.assetid: 96515727-728b-4bea-804a-36ce915b8b75
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5605fa1b5ef261083c8e26205de92c3f76b10256
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="syspartitionfunctions-transact-sql"></a>sys.partition_functions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Contient une ligne par fonction de partition dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de la fonction de partition Unique dans la base de données.|  
|**function_id supérieures**|**int**|ID de la fonction de partition. Unique dans la base de données.|  
|**type**|**char(2)**|Type de fonction.<br /><br /> R = plage|  
|**type_desc**|**nvarchar(60)**|Type de fonction.<br /><br /> RANGE|  
|**distribution ramifiée**|**int**|Nombre de partitions créées par la fonction.|  
|**boundary_value_on_right**|**bit**|Pour le partitionnement par spécification de plages de valeurs.<br /><br /> 1 = la valeur limite est incluse dans la plage RIGHT de la limite.<br /><br /> 0 = LEFT.|  
|**is_system**||**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = l'objet est utilisé pour les fragments d'index de recherche en texte intégral.<br /><br /> 0 = l'objet n'est pas utilisé pour les fragments d'index de recherche en texte intégral.|  
|**create_date**|**datetime**|Date de création de la fonction.|  
|**modify_date**|**datetime**|Date de la dernière modification de la fonction à l'aide d'une instruction ALTER.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue des fonctions de partition &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.partition_range_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [Sys.partition_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)  
  
  
