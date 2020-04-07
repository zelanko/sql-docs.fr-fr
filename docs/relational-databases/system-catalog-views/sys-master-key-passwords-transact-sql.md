---
title: sys.master_key_passwords (Transact-SQL) Microsoft Docs
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.master_key_passwords_TSQL
- master_key_passwords_TSQL
- sys.master_key_passwords
- master_key_passwords
dev_langs:
- TSQL
helpviewer_keywords:
- sys.master_key_passwords catalog view
ms.assetid: b8e18cff-a9e6-4386-98ce-1cd855506e03
author: stevestein
ms.author: sstein
ms.openlocfilehash: 926acd9beb00102e19dbc2844e282d74bc890915
ms.sourcegitcommit: c6a2efe551e37883c1749bdd9e3c06eb54ccedc9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80752899"
---
# <a name="sysmaster_key_passwords-transact-sql"></a>sys.master_key_passwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Renvoie une ligne pour chaque mot de passe clé de base de données ajouté en utilisant la procédure **stockée sp_control_dbmasterkey_password.** Les mots de passe utilisés pour protéger les clés principales sont stockés dans la banque d'informations d'identification. Le nom d’accréditation suit ce format : #DBMKEY_<database_family_guid>_<random_password_guid>. Le mot de passe est stocké en tant que secret des informations d'identification. Pour chaque mot de passe ajouté en utilisant **sp_control_dbmasterkey_password**, il ya une rangée dans **sys.credentials**.  
  
 Chaque rangée de cette vue montre un **credential_id** et le **family_guid** d’une base de données dont la clé principale est protégée par le mot de passe associé à cette identification. Un joint avec **sys.credentials** sur le **credential_id** retournera champs utiles, tels que le **create_date** et le nom d’identification.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**credential_id**|**Int**|ID de l'information d'identification à laquelle appartient le mot de passe. Cet ID est unique dans l'instance du serveur.|  
|**family_guid**|**Uniqueidentifier**|ID unique de la base de données d'origine lors de sa création. Ce GUID reste identique après la restauration ou l'association de la base de données, même si le nom de la base de données est modifié.<br /><br /> Si le décryptage automatique par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la clé du maître de service échoue, utilise le **family_guid** pour identifier les informations d’identification qui peuvent contenir le mot de passe utilisé pour protéger la clé de base de données.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue &#40;&#41;De Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [Vue du catalogue de sécurité &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE KEY SYMÉTRIQUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
