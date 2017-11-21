---
title: ALTER PARTITION SCHEME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER PARTITION SCHEME
- ALTER_PARTITION_SCHEME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PARTITION SCHEME statement
- partition schemes [SQL Server], modifying
- modifying partition schemes
- adding filegroups
- NEXT USED filegroups
ms.assetid: f01d6880-9800-4cfb-8d11-d4be21efc8ca
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 545fe3da48f0d0c98d72b32e5a82d9fd55579d00
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-partition-scheme-transact-sql"></a>ALTER PARTITION SCHEME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un groupe de fichiers au schéma d'une partition ou modifie la désignation du groupe de fichiers NEXT USED pour le schéma de la partition.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER PARTITION SCHEME partition_scheme_name   
NEXT USED [ filegroup_name ] [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *partition_scheme_name*  
 Est le nom du schéma de partition à modifier.  
  
 *FILEGROUP_NAME*  
 Spécifie le groupe de fichiers que le schéma de partition doit marquer comme NEXT USED. Cela signifie que le groupe de fichiers accepte une nouvelle partition est créée en utilisant une [ALTER PARTITION FUNCTION](../../t-sql/statements/alter-partition-function-transact-sql.md) instruction.  
  
 Dans un schéma de partition, un seul groupe de fichiers peut être désigné comme NEXT USED. Un groupe de fichiers non vide peut être spécifié. Si *filegroup_name* est spécifié et est actuellement ne marqué d’aucun groupe de fichiers NEXT USED, *filegroup_name* est marqué comme NEXT USED. Si *filegroup_name* est spécifié et un groupe de fichiers avec la propriété NEXT USED existe déjà, la propriété NEXT USED transfère à partir du groupe de fichiers existant à *filegroup_name*.  
  
 Si *filegroup_name* n’est pas spécifié et un groupe de fichiers avec la propriété NEXT USED existe déjà, ce groupe de fichiers perd son état NEXT USED afin qu’il n’existe aucun groupe de fichiers NEXT USED dans *partition_scheme_name*.  
  
 Si *filegroup_name* n’est pas spécifié et sont ne marqués d’aucun groupe de fichiers NEXT USED, ALTER PARTITION SCHEME renvoie un avertissement.  
  
## <a name="remarks"></a>Notes  
 Tout groupe de fichiers affecté par ALTER PARTITION SCHEME doit être en ligne.  
  
## <a name="permissions"></a>Permissions  
 Estimée des autorisations suivantes peuvent être utilisées pour exécuter ALTER PARTITION SCHEME :  
  
-   Autorisation ALTER ANY DATASPACE. Cette autorisation est attribuée par défaut aux membres du rôle de serveur fixe **sysadmin** et des rôles de base de données fixes **db_owner** et **db_ddladmin** .  
  
-   Autorisation CONTROL ou ALTER sur la base de données dans laquelle le schéma de partition a été créé.  
  
-   Autorisation CONTROL SERVER ou ALTER ANY DATABASE sur le serveur de la base de données dans laquelle le schéma de partition a été créé.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant suppose que le schéma de partition `MyRangePS1` et le groupe de fichiers `test5fg` existent dans la base de données active.  
  
```  
ALTER PARTITION SCHEME MyRangePS1  
NEXT USED test5fg;  
```  
  
 Le groupe de fichiers `test5fg` recevra toute partition supplémentaire d'une table ou d'un index partitionné à la suite d'une instruction ALTER PARTITION FUNCTION.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [ALTER PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Sys.partition_schemes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [Sys.data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [Sys.destination_data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [Sys.partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  

