---
title: "SUPPRIMER la clé asymétrique (Transact-SQL) | Documents Microsoft"
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
- DROP ASYMMETRIC KEY
- DROP_ASYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], removing
- removing asymmetric keys
- encryption [SQL Server], asymmetric keys
- DROP ASYMMETRIC KEY statement
- dropping asymmetric keys
- deleting asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: bf94ac07-9b62-4318-b55b-1eed8f3a1ac6
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f3737521ee178f9b7287f8d86e269973841d74c6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-asymmetric-key-transact-sql"></a>DROP ASYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime une clé asymétrique de la base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP ASYMMETRIC KEY key_name [ REMOVE PROVIDER KEY ]  
```  
  
## <a name="arguments"></a>Arguments  
 *key_name*  
 Nom de la clé asymétrique à supprimer de la base de données.  
  
 REMOVE PROVIDER KEY  
 Supprime une clé EKM (Gestion de clés extensible) d'un périphérique EKM. Pour plus d’informations sur la gestion de clés Extensible, consultez [gestion de clés Extensible &#40; Gestion de clés extensible &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Notes  
 Une clé asymétrique avec laquelle une clé symétrique de la base de données a été chiffrée, ou sur laquelle un utilisateur ou une connexion est mappée, ne peut pas être supprimée. Avant de supprimer une telle clé, vous devez supprimer tout utilisateur ou connexion mappée sur cette clé. Vous devez également supprimer ou modifier toute clé symétrique chiffrée avec la clé asymétrique. Vous pouvez utiliser l’option DROP ENCRYPTION de [ALTER SYMMETRIC KEY](../../t-sql/statements/alter-symmetric-key-transact-sql.md) pour supprimer le chiffrement par une clé asymétrique.  
  
 Métadonnées des clés asymétriques sont accessibles à l’aide de la [sys.asymmetric_keys](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md) affichage catalogue. Il n'est pas possible d'afficher les clés elles-mêmes directement à partir de la base de données.  
  
 Si la clé asymétrique est mappée à une clé EKM (Gestion de clés extensible) sur un périphérique EKM et que l'option REMOVE PROVIDER KEY n'est pas spécifiée, la clé sera supprimée de la base de données, mais pas du périphérique. Un avertissement sera émis.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CONTROL sur la clé asymétrique.  
  
## <a name="examples"></a>Exemples  
 Le code exemple suivant supprime la clé asymétrique `MirandaXAsymKey6` de la base de données `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
DROP ASYMMETRIC KEY MirandaXAsymKey6;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER SYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)  
  
  

