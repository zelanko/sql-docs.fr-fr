---
description: sys. column_encryption_key_values (Transact-SQL)
title: sys. column_encryption_key_values (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
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
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aee9c14d1b59055cc968e9b51fa2e07005ae94bd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470009"
---
# <a name="syscolumn_encryption_key_values-transact-sql"></a>sys. column_encryption_key_values (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Retourne des informations sur les valeurs chiffrées des clés de chiffrement de colonne (clés CEK) créées à l’aide de la commande [Create Column](../../t-sql/statements/create-column-encryption-key-transact-sql.md) Encryption Key ou de l’instruction [ALTER COLUMN Encryption Key &#40;Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md) . Chaque ligne représente une valeur d’un clé CEK, chiffrée avec une clé principale de colonne (CMK).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_id**|**int**|ID du clé CEK dans la base de données.|  
|**column_master_key_id**|**int**|ID de la clé principale de colonne qui a été utilisée pour chiffrer la valeur clé CEK.|  
|**encrypted_value**|**varbinary(8000)**|Valeur clé CEK chiffrée avec le CMK spécifié dans column_master_key_id.|  
|**encryption_algorithm_name**|**sysname**|Nom d’un algorithme utilisé pour chiffrer la valeur clé CEK.<br /><br /> Nom de l’algorithme de chiffrement utilisé pour chiffrer la valeur. L’algorithme pour les fournisseurs système doit être  **RSA_OAEP**.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation **afficher une clé de chiffrement de colonne** .  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une clé de CHIFFREment de colonne &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ALTER COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [SUPPRIMER la clé de CHIFFREment de colonne &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CRÉER une clé principale de colonne &#40;&#41;Transact-SQL ](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sys. column_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys. column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Always Encrypted avec des enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Vue d’ensemble de la gestion des clés pour Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Gérer des clés pour Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   

  
  
