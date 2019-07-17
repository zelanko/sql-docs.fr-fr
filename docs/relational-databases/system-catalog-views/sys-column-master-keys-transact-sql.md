---
title: sys.column_master_keys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_master_key_definitions_TSQL
- column_master_key_definitions
- sys.column_master_key_definitions_TSQL
- sys.column_master_key_definitions
- column_master_keys_TSQL
- column_master_keys
- sys.column_master_keys_TSQL
- sys.column_master_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_key_definitions catalog view
- sys.column_master_keys catalog view
ms.assetid: fbec2efa-5fe9-4121-9b34-60497b0b2aca
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8ae8a4077c0fe4e3f6b7754b4fc53a401d03e355
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140061"
---
# <a name="syscolumnmasterkeys-transact-sql"></a>sys.column_master_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque clé principale de base de données ajouté à l’aide de la [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) instruction. Chaque ligne représente une clé principale de colonne (CMK).  
    
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Le nom de la clé CMK.|  
|**column_master_key_id**|**int**|ID de la clé principale de colonne.|  
|**create_date**|**datetime**|Date de que création de la clé principale de colonne.|  
|**modify_date**|**datetime**|Date de que dernière modification de la clé principale de colonne.|  
|**key_store_provider_name**|**sysname**|Nom du fournisseur pour le magasin de clés principales de colonne qui contient la clé CMK. Les valeurs autorisées sont les suivantes :<br /><br /> MSSQL_CERTIFICATE_STORE - si le magasin de clés principales de colonne est un Store de certificat.<br /><br /> Défini par l’utilisateur valeur, si le magasin de clés principales de colonne est d’un type personnalisé.|  
|**key_path**|**nvarchar(4000)**|Un chemin de spécifiques aux magasins de clé principale de colonne de la clé. Le format du chemin d’accès varie selon le type de magasin de clé principale de colonne. Exemple :<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Pour un magasin de clés principales de colonne personnalisée, le développeur est chargé de définir un chemin de clé est pour le magasin de clés principales de colonne personnalisée.|  
|**allow_enclave_computations**|**bit**|Indique si la clé principale de colonne est enclave compatibles, (si les clés de chiffrement de colonne, chiffrées avec cette clé principale, peuvent être utilisés pour effectuer des calculs à l’intérieur d’enclaves sécurisés côté serveur). Pour plus d’informations, consultez [Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md).|  
|**signature**|**varbinary(max)**|Une signature numérique du **key_path** et **allow_enclave_computations**, généré à l’aide de la clé principale de colonne, référencée par **key_path**.|


  
## <a name="permissions"></a>Autorisations  
 Nécessite le **VIEW ANY COLUMN MASTER KEY** autorisation.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Always Encrypted &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
