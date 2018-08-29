---
title: Sys.master_key_passwords (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a0aa45dc4ee0e54e7880837e289b2331b5ff11e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017719"
---
# <a name="sysmasterkeypasswords-transact-sql"></a>sys.master_key_passwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque mot de passe de clé principale de base de données ajouté à l’aide de la **sp_control_dbmasterkey_password** procédure stockée. Les mots de passe utilisés pour protéger les clés principales sont stockés dans la banque d'informations d'identification. Les noms des informations d'identification s'expriment dans le format suivant : ##DBMKEY_<database_family_guid>_<random_password_guid>##. Le mot de passe est stocké en tant que secret des informations d'identification. Pour chaque mot de passe ajouté à l’aide de **sp_control_dbmasterkey_password**, il existe une ligne dans **sys.credentials**.  
  
 Chaque ligne de cette vue montre un **credential_id** et **family_guid** d’une base de données que la clé principale de ce qui est protégée par mot de passe associé à ces informations d’identification. Une jointure avec **sys.credentials** sur le **credential_id** renvoie les champs utiles, telles que la **create_date** et le nom d’identification.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**credential_id**|**Int**|ID de l'information d'identification à laquelle appartient le mot de passe. Cet ID est unique dans l'instance du serveur.|  
|**family_guid**|**uniqueidentifier**|ID unique de la base de données d'origine lors de sa création. Ce GUID reste identique après la restauration ou l'association de la base de données, même si le nom de la base de données est modifié.<br /><br /> Si le déchiffrement automatique par la clé principale du service échoue, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le **family_guid** pour identifier les informations d’identification qui peuvent contenir le mot de passe utilisé pour protéger la clé principale de base de données.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
