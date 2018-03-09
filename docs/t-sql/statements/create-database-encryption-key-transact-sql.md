---
title: "CRÉER la clé de chiffrement de base de données (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.prod_service: pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_ENCRYPTION_KEY_TSQL
- ENCRYPTION_KEY_TSQL
- sql13.swb.dbencryptionkeyo.f1
- ENCRYPTION KEY
- DATABASE ENCRYPTION KEY
- CREATE_DATABASE_ENCRYPTION_KEY_TSQL
- CREATE DATABASE ENCRYPTION KEY
- sql13.swb.dbencryptionkeyg.f1
- CREATE DATABASE ENCRYPTION
- CREATE_DATABASE_ENCRYPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key
- CREATE DATABASE ENCRYPTION KEY statement
- database encryption key, create
ms.assetid: 2ee95a32-5140-41bd-9ab3-a947b9990688
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b108a5cddba7052d177760374d8c5047b28fb25c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="create-database-encryption-key-transact-sql"></a>CREATE DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

 Crée une clé de chiffrement permettant de chiffrer une base de données de façon transparente. Pour plus d’informations sur le chiffrement transparent de la base de données, consultez [Transparent Data Encryption &#40; Chiffrement transparent des données &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name   
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY  }  
Spécifie l'algorithme de chiffrement utilisé pour la clé de chiffrement.   
>  [!NOTE]
>    À partir de SQL Server 2016, tous les algorithmes autres que AES_128, AES_192 et AES_256 sont déconseillés. Pour utiliser des algorithmes plus anciens (ce qui n’est pas recommandé), vous devez affecter le niveau de compatibilité 120 ou un niveau inférieur à la base de données.  
  
CHIFFREMENT par Encryptor_Name de certificat de serveur  
Spécifie le nom du chiffreur utilisé pour chiffrer la clé de chiffrement de base de données.  
  
CHIFFREMENT par Encryptor_Name clé asymétrique de serveur  
Spécifie le nom de la clé asymétrique utilisée pour chiffrer la clé de chiffrement de base de données. Afin de chiffrer la clé de chiffrement de base de données avec une clé asymétrique, la clé asymétrique doit résider sur un fournisseur de gestion de clés extensible.  
  
## <a name="remarks"></a>Notes  
Une clé de chiffrement de base de données est requise avant d’une base de données peut être chiffrée à l’aide de *chiffrement Transparent de base de données* (TDE). Lorsqu'une base de données est chiffrée de façon transparente, elle l'est entièrement au niveau des fichiers, sans aucune modification de code spéciale. Le certificat ou la clé asymétrique utilisé pour chiffrer la clé de chiffrement de base de données doit se trouver dans la base de données système principale.  
  
Les instructions de chiffrement de base de données ne sont autorisées que sur les bases de données utilisateur.  
  
La clé de chiffrement de base de données ne peut pas être exportée de la base de données. Elle est uniquement disponible pour le système, les utilisateurs qui disposent d'autorisations de débogage sur le serveur et les utilisateurs qui ont accès aux certificats qui chiffrent et déchiffrent la clé de chiffrement de base de données.  
  
La clé de chiffrement de base de données n'a pas besoin d'être régénérée lorsqu'un propriétaire de base de données (dbo) est modifié.  
  
Une clé de chiffrement de base de données est automatiquement créée pour un [!INCLUDE[ssSDS](../../includes/sssds-md.md)] base de données. Vous n’avez pas besoin de créer une clé à l’aide de l’instruction CREATE DATABASE ENCRYPTION KEY.  
  
## <a name="permissions"></a>Permissions  
Nécessite l'autorisation CONTROL sur la base de données et l'autorisation VIEW DEFINITION sur le certificat ou la clé asymétrique permettant de chiffrer la clé de chiffrement de base de données.  
  
## <a name="examples"></a>Exemples  
Pour obtenir des exemples supplémentaires à l’aide du chiffrement transparent des données, consultez [Transparent Data Encryption &#40; Chiffrement transparent des données &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md), [Activer le chiffrement transparent des données sur SQL Server à l’aide de la gestion de clés extensible](../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md), et [gestion de clés Extensible à l’aide d’Azure Key Vault &#40; SQL Server &#41; ](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
Dans l'exemple suivant, une clé de chiffrement de base de données est créée à l'aide de l'algorithme `AES_256`, et protège la clé privée à l'aide d'un certificat nommé `MyServerCert`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
[Chiffrement transparent des données &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
[Chiffrement SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
[SQL Server et clés de chiffrement de base de données &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
[Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
[Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
[MODIFIER la clé de chiffrement de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
[SUPPRIMER la clé de chiffrement de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
[sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
    
