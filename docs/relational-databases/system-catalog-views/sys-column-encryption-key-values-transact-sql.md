---
title: Sys.column_encryption_key_values (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- column_encryption_key_values
- column_encryption_key_values_TSQL
- sys.column_encryption_key_values
- sys.column_encryption_key_values_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_encryption_key_values catalog view
ms.assetid: 440875ab-b0e9-4966-8c16-01503558fedd
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7bc9fa475e7e7fba6a8fac7bdb4e014742b6ad21
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="syscolumnencryptionkeyvalues-transact-sql"></a>Sys.column_encryption_key_values (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les valeurs chiffrées de la colonne clés de chiffrement (clés cek) créés avec la [CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) ou [ALTER COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-column-encryption-key-transact-sql.md) instruction. Chaque ligne représente une valeur d’une clé CEK, chiffrée avec une clé principale de colonne (CMK).  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_id**|**int**|ID de la clé CEK dans la base de données.|  
|**column_master_key_id**|**int**|ID de la clé principale de colonne qui a été utilisée pour chiffrer la valeur de la clé CEK.|  
|**encrypted_value**|**varbinary (8000)**|Valeur de la clé CEK chiffrée avec la clé CMK spécifiée dans column_master_key_id.|  
|**encryption_algorithm_name**|**sysname**|Nom de l’algorithme utilisé pour chiffrer la valeur de la clé CEK.<br /><br /> Nom de l’algorithme de chiffrement utilisé pour chiffrer la valeur. L’algorithme pour les fournisseurs de système doit être **RSA_OAEP**.|  
  
## <a name="permissions"></a>Permissions  
 Requiert le **VIEW ANY COLUMN ENCRYPTION KEY** autorisation.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ALTER COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sys.column_encryption_keys  &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys.column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Always Encrypted &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
  
  
