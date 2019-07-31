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
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b4ced2feee2227ba1db492f721f57907069c5d99
ms.sourcegitcommit: 97e94b76f9f48d161798afcf89a8c2ac0f09c584
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661357"
---
# <a name="spenclavesendkeys----transact-sql"></a>sp_enclave_send_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Envoie toutes les clés de chiffrement de colonne compatibles avec les enclaves dans la base de données à l’enclave utilisée par [Always Encrypted avec les enclaves sécurisées &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

## <a name="syntax"></a>Syntaxe  
  
```
sp_enclave_send_keys
[ ;]  
```

## <a name="arguments"></a>Arguments

Cette procédure stockée n’a pas d’arguments.

## <a name="return-value"></a>Valeur de retour

Cette procédure stockée n’a pas de valeur de retour.
  
## <a name="result-sets"></a>Jeux de résultats

Cette procédure stockée n’a pas de jeu de résultats.
  
## <a name="remarks"></a>Notes

**sp_enclave_send_keys** envoie des clés de chiffrement de colonne avec enclave à l’enclave si toutes les conditions suivantes sont remplies:

- L’enclave est activée dans l’instance SQL Server.
- **sp_enclave_send_keys** a été appelé à partir d’une application à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’aide d’un pilote client, prenant en charge Always Encrypted avec des enclaves sécurisées à l’aide d’une connexion de base de données pour laquelle les calculs Always Encrypted et enclave sont activés.

## <a name="permissions"></a>Autorisations

 Exigez les autorisations **afficher une définition de clé** de chiffrement de colonne et **afficher toutes les définitions de clé principale de colonne** dans la base de données.  
  
## <a name="examples"></a>Exemples  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>Voir aussi

 [Always Encrypted avec des enclaves &#40;sécurisées moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Tutoriel : Création et utilisation d’index sur des colonnes de l’enclave à l’aide d’un chiffrement aléatoire](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md#step-3-create-an-index-with-role-separation)   
 [Appeler des opérations d’indexation à l’aide de clés de chiffrement de colonne mises en cache](../security/encryption/configure-always-encrypted-enclaves.md#invoke-indexing-operations-using-cached-column-encryption-keys)   
 [Index sur les colonnes de l’enclave utilisant le chiffrement aléatoire](../security/encryption/always-encrypted-enclaves.md#indexes-on-enclave-enabled-columns-using-randomized-encryption)   
 [Considérations relatives à la migration de bases de données et AlwaysOn](../security/encryption/always-encrypted-enclaves.md#anchorname-1-considerations-availability-groups-db-migration)
