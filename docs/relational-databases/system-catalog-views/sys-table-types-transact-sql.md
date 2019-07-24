---
title: Sys.table_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- table_types_TSQL
- sys.table_types
- sys.table_types_TSQL
- table_types
dev_langs:
- TSQL
helpviewer_keywords:
- table types [SQL Server]
- table-valued parameters, sys.table_types
- sys.table_types
- UDTT
ms.assetid: c05fd873-aff2-4a89-9936-a54c2ea09996
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1c31a2c72666229dbe214c07e31102e647b372d3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68078596"
---
# <a name="systabletypes-transact-sql"></a>sys.table_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Affiche les propriétés des types de tables définis par l'utilisateur dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un type de table est un type à partir duquel il est possible de déclarer des variables de table ou des paramètres table. Chaque type de table a un **type_table_object_id** qui est une clé étrangère dans la [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) vue de catalogue. Vous pouvez utiliser cette colonne d’ID pour interroger différents affichages catalogue, de manière similaire à un **object_id** colonne d’une table normale, pour découvrir la structure du type de table tels que ses colonnes et contraintes.    
 
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|*\<héritée de colonnes >*||Pour obtenir la liste des colonnes qui hérite de cette vue, consultez [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md).|  
|**type_table_object_id**|**int**|Numéro d'identification de l'objet. Ce numéro est unique dans la base de données.|  
|**is_memory_optimized**|**bit**|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Les valeurs possibles sont les suivantes :<br /><br /> 0 = Non optimisé en mémoire<br /><br /> 1 = Optimisé en mémoire<br /><br /> La valeur 0 est la valeur par défaut.<br /><br /> Les types de tables sont toujours créés avec DURABILITY = SCHEMA_ONLY. Seul le schéma est rendu persistant sur le disque.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Utiliser les paramètres table &#40;moteur de base de données&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
