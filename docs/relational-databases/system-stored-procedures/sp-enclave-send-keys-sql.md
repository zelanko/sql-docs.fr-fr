---
title: sp_enclave_send_keys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enclave_send_keys
- sp_enclave_send_keys_TSQL
- sys.sp_enclave_send_keys
- sys.sp_enclave_send_keys_TSQL
helpviewer_keywords:
- sp_enclave_send_keys
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 6540cdd36cccba4f5a7ccb3beddf31ce00cd9107
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394141"
---
# <a name="spenclavesendkeys----transact-sql"></a>sp_enclave_send_keys    (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Envoie toutes les enclave prenant en charge la colonne clés de chiffrement dans la base de données à l’enclave utilisé par [Always Encrypted avec enclaves sécurisés &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

## <a name="syntax"></a>Syntaxe  
  
```
sp_enclave_send_keys
[ ;]  
```

## <a name="arguments"></a>Arguments

Cette procédure stockée n’a aucun argument.

## <a name="return-value"></a>Valeur de retour

Cette procédure stockée n’a aucune valeur de retour.
  
## <a name="result-sets"></a>Jeux de résultats

Cette procédure stockée n’a aucun jeu de résultats.
  
## <a name="remarks"></a>Notes

**sp_enclave_send_keys** envoie les clés de chiffrement de colonne prenant en charge l’enclave à l’enclave si toutes les conditions suivantes sont remplies :

- L’enclave est activée dans l’instance de SQL Server.
- **sp_enclave_send_keys** a été appelée à partir d’une application en utilisant un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote du client, prise en charge d’Always Encrypted avec enclaves sécurisés à l’aide d’une connexion de base de données présentant des calculs Always Encrypted et de l’enclave activés.

## <a name="permissions"></a>Autorisations

 Exiger le **VIEW ANY COLUMN ENCRYPTION KEY DEFINITION** et **VIEW ANY COLUMN MASTER KEY DEFINITION** autorisations dans la base de données.  
  
## <a name="examples"></a>Exemples  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>Voir aussi

 [Always Encrypted avec enclaves sécurisés &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Tutoriel : Création et utilisation d’index sur des colonnes de l’enclave à l’aide d’un chiffrement aléatoire](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md#step-3-create-an-index-with-role-separation)   
 [Appeler des opérations d’indexation à l’aide de clés de chiffrement de colonne mises en cache](../security/encryption/configure-always-encrypted-enclaves.md#invoke-indexing-operations-using-cached-column-encryption-keys)   
 [Index sur des colonnes de l’Enclave à l’aide du chiffrement aléatoire](../security/encryption/always-encrypted-enclaves.md#indexes-on-enclave-enabled-columns-using-randomized-encryption)   
 [Considérations relatives à AlwaysOn et de Migration de base de données](../security/encryption/always-encrypted-enclaves.md#considerations-for-alwayson-and-database-migration)
