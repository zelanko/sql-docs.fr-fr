---
title: sys.dm_database_encryption_keys (Transact-SQL) Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6e716c826fd366fda4505b7fcf9ec8e3b756ec25
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531050"
---
# <a name="sysdm_database_encryption_keys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur l'état de chiffrement d'une base de données et de ses clés de chiffrement de base de données associées. Pour plus d’informations sur le chiffrement des bases de données, consultez [Chiffrement transparent des données &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
 
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|database_id|**Int**|ID de la base de données.|  
|encryption_state|**Int**|Indique si la base de données est chiffrée ou non chiffrée.<br /><br /> 0 = aucune clé de chiffrement de base de données présente, pas de chiffrement<br /><br /> 1 = non chiffré<br /><br /> 2 = chiffrement en cours<br /><br /> 3 = chiffrée.<br /><br /> 4 = modification de clé en cours<br /><br /> 5 = déchiffrement en cours<br /><br /> 6 = modification de la protection en cours (Le certificat ou la clé asymétrique qui chiffre la clé de chiffrement de base de données est en cours de modification.)|  
|create_date|**Datetime**|Affiche la date (dans UTC) la clé de chiffrement a été créée.|  
|regenerate_date|**Datetime**|Affiche la date (dans UTC) la clé de chiffrement a été régénérée.|  
|modify_date|**Datetime**|Affiche la date (dans UTC) la clé de chiffrement a été modifiée.|  
|set_date|**Datetime**|Affiche la date (dans UTC) la clé de chiffrement a été appliquée à la base de données.|  
|opened_date|**Datetime**|Indique quand (dans UTC) la clé de base de données a été ouverte pour la dernière fois.|  
|key_algorithm|**nvarchar(32)**|Affiche l'algorithme utilisé pour la clé.|  
|key_length|**Int**|Affiche la longueur de la clé.|  
|encryptor_thumbprint|**varbinary(20)**|Affiche l'empreinte numérique du chiffreur.|  
|encryptor_type|**nvarchar(32)**|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (par[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] la version [actuelle](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> Décrit le chiffreur.|  
|percent_complete|**real**|Pourcentage accompli de la modification de l'état de chiffrement de la base de données. La valeur 0 indique aucune modification d'état.|
|encryption_state_desc|**nvarchar(32)**|**S’applique à**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] et plus tard.<br><br> Chaîne qui indique si la base de données est cryptée ou non cryptée.<br><br>Aucune<br><br>Clair<br><br>COMMUNICATIONS<br><br>DECRYPTION_IN_PROGRESS<br><br>ENCRYPTION_IN_PROGRESS<br><br>KEY_CHANGE_IN_PROGRESS<br><br>PROTECTION_CHANGE_IN_PROGRESS|
|encryption_scan_state|**Int**|**S’applique à**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] et plus tard.<br><br>Indique l’état actuel de l’analyse de cryptage. <br><br>0 - Aucun scan n’a été lancé, TDE n’est pas activé<br><br>1 - L’analyse est en cours.<br><br>2 - L’analyse est en cours, mais a été suspendue, l’utilisateur peut reprendre.<br><br>3 - L’analyse a été avortée pour une raison quelconque, une intervention manuelle est nécessaire. Contactez Microsoft Support pour plus d’assistance.<br><br>4 - L’analyse a été complétée avec succès, la TDE est activée et le chiffrement est terminé.|
|encryption_scan_state_desc|**nvarchar(32)**|**S’applique à**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] et plus tard.<br><br>Chaîne qui indique l’état actuel de l’analyse de cryptage.<br><br> Aucune<br><br>RUNNING<br><br>SUSPENDED<br><br>ABORTED<br><br>Complet|
|encryption_scan_modify_date|**Datetime**|**S’applique à**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] et plus tard.<br><br> Affiche la date (dans UTC) l’état d’analyse de chiffrement a été modifié pour la dernière fois.|
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], `VIEW SERVER STATE` exige la permission.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium Tiers, `VIEW DATABASE STATE` nécessite l’autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard and Basic Tiers, nécessite **l’administrateur Server** ou un compte **d’administration Azure Active Directory.**   

## <a name="see-also"></a>Voir aussi  

 [Points de vue et fonctions de gestion dynamique liés à la sécurité &#40;&#41;de Transact-SQL](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Chiffrement de données transparent &#40;&#41;TDE](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Chiffrement du serveur SQL](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE BASE DE DONNÉES DE CHIFFREMENT KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [MODIFIER LA CLÉ DE CHIFFREMENT DE LA BASE DE DONNÉES &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
