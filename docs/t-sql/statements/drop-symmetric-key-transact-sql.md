---
title: "SUPPRIMER la clé symétrique (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SYMMETRIC KEY
- DROP_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], removing
- deleting symmetric keys
- encryption [SQL Server], symmetric keys
- removing symmetric keys
- dropping symmetric keys
- cryptography [SQL Server], symmetric keys
- DROP SYMMETRIC KEY statement
ms.assetid: 6150bc67-08cb-402e-9c24-b04c9654b434
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b693a5d8dd45ec410b5517e564baf8ace3efb22d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-symmetric-key-transact-sql"></a>DROP SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime une clé symétrique de la base de données active.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP SYMMETRIC KEY symmetric_key_name [REMOVE PROVIDER KEY]  
```  
  
## <a name="arguments"></a>Arguments  
 *symmetric_key_name*  
 Nom de la clé symétrique à supprimer.  
  
 REMOVE PROVIDER KEY  
 Supprime une clé EKM (Gestion de clés extensible) d'un périphérique EKM. Pour plus d’informations sur la gestion de clés Extensible, consultez [gestion de clés Extensible &#40; Gestion de clés extensible &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Notes  
 Si la clé est ouverte dans la session en cours, l'instruction échoue.  
  
 Si la clé asymétrique est mappée à une clé de gestion de clés Extensible (EKM) sur un périphérique EKM et **supprimer la clé de fournisseur** option n’est pas spécifiée, la clé doivent être supprimée de la base de données, mais pas sur l’appareil et un avertissement est émis.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL sur la clé symétrique.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous, une clé symétrique nommée `GailSammamishKey6` est supprimée de la base de données en cours.  
  
```  
CLOSE SYMMETRIC KEY GailSammamishKey6;  
DROP SYMMETRIC KEY GailSammamishKey6;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CLOSE SYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/close-symmetric-key-transact-sql.md)   
 [Gestion de clés extensible &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  

