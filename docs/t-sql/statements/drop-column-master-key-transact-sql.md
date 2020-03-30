---
title: DROP COLUMN MASTER KEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP COLUMN MASTER KEY
- DROP_COLUMN_MASTER_KEY_TSQL
- DROP COLUMN MASTER
- DROP_COLUMN_MASTER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_keys catalog view
ms.assetid: fd5e77c8-a3ae-4795-bb46-b322c0500041
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: f6267189a83816f1c77740e5df176cc2dda86428
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "73594159"
---
# <a name="drop-column-master-key-transact-sql"></a>DROP COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Supprime une clé principale de colonne d’une base de données. Il s’agit d’une opération sur les métadonnées.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP COLUMN MASTER KEY key_name;  
```  
  
## <a name="arguments"></a>Arguments  
 *key_name*  
 Nom de la clé principale de colonne.  
  
## <a name="remarks"></a>Notes  
 La clé principale de colonne ne peut être supprimée que s’il n’existe aucune valeur de clé de chiffrement chiffrées avec cette clé principale de colonne. Pour supprimer des valeurs de clé de chiffrement de colonne, utilisez l’instruction [DROP COLUMN ENCRYPTION KEY](../../t-sql/statements/drop-column-encryption-key-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Exige l’autorisation **ALTER ANY COLUMN MASTER KEY** sur la base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-dropping-a-column-master-key"></a>R. Suppression d’une clé principale de colonne  
 L’exemple suivant supprime une clé principale de colonne appelée `MyCMK`.  
  
```  
DROP COLUMN MASTER KEY MyCMK;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [sys.column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Vue d’ensemble de la gestion des clés pour Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Gérer des clés pour Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   
  
  
