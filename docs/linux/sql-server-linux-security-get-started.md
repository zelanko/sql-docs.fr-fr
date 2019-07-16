---
title: Bien démarrer avec la sécurité de SQL Server sur Linux
description: Cet article décrit les actions de sécurité standard.
author: VanMSFT
ms.author: vanto
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.openlocfilehash: 1e64ce76ef2528c96ecc0206b7a56b31d4c95ef7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019499"
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Procédure pas à pas pour les fonctionnalités de sécurité de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Si vous êtes un utilisateur Linux pour qui SQL Server est une nouveauté, les tâches suivantes vous guident parmi les tâches de sécurité. Celles-ci ne sont pas uniques ou spécifiques à Linux, mais cela permet de vous donner une idée des domaines à approfondir. Dans chaque exemple, un lien est fourni, menant à la documentation détaillée pour ce domaine.

> [!NOTE]
>  Les exemples suivants utilisent la base de données exemple **AdventureWorks2014**. Pour obtenir des instructions sur la façon d’obtenir et d'installer cette base de données exemple, consultez [restaurer une base de données SQL Server à partir de Windows et Linux](sql-server-linux-migrate-restore-database.md).


## <a name="create-a-login-and-a-database-user"></a>Créer une connexion et un utilisateur de base de données 

Accordez l’accès à SQL Server en créant une connexion dans la base de données master à l’aide de la commande [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) Exemple :

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

> [!NOTE]
>  Utilisez toujours un mot de passe fort à la place les astérisques dans la commande précédente.

Connexions d’accès peuvent se connecter à SQL Server et avoir accès (avec des autorisations limitées) à la base de données master. Pour vous connecter à une base de données utilisateur, un compte de connexion a besoin d’une identité correspondante au niveau base de données, appelé un utilisateur de base de données. Les utilisateurs sont spécifiques à chaque base de données et doivent être créés séparément dans chaque base de données à leur accorder l’accès. L’exemple suivant permet de passer dans la base de données AdventureWorks2014, puis utilise le [CREATE USER](../t-sql/statements/create-user-transact-sql.md) instruction pour créer un utilisateur nommé Larry qui est associé à la connexion nommée Larry. Bien que la connexion et l’utilisateur sont liées (mappé entre eux), ce sont des objets différents. La connexion est un principe de niveau serveur. L’utilisateur est un principal au niveau de la base de données.

```
USE AdventureWorks2014;
GO
CREATE USER Larry;
GO
```

- Un compte d’administrateur SQL Server peut se connecter à n'importe quelle base de données et peut créer plusieurs connexions et utilisateurs supplémentaires dans une base de données.  
- Lorsqu’un utilisateur crée une base de données, il en devient le propriétaire, ce qui lui permet de se connecter à cette base de données. Les propriétaires de base de données peuvent créer d’autres utilisateurs.

Ultérieurement, vous pouvez autoriser des connexions à créer des connexions en leur octroyant la permission `ALTER ANY LOGIN`. À l’intérieur d’une base de données, vous pouvez autoriser certains utilisateurs à créer d’autres utilisateurs en leur octroyant la permission `ALTER ANY USER`. Exemple :   

```
GRANT ALTER ANY LOGIN TO Larry;   
GO   
   
USE AdventureWorks2014;   
GO   
GRANT ALTER ANY USER TO Jerry;    
GO   
```

La connexion Larry pouvez désormais créer des connexions plus et l’utilisateur Jerry peut créer d’autres utilisateurs.


## <a name="granting-access-with-least-privileges"></a>Octroi de l’accès avec des privilèges minimum

Les premières personnes à se connecter à une base de données utilisateur seront l’administrateur et les comptes de propriétaire de base de données. Toutefois, ces utilisateurs ont toutes les autorisations sur la base de données. C'est plus que la plupart des utilisateurs devraient avoir. 

Lorsque vous venez de démarrer, vous pouvez affecter des catégories générales d’autorisations à l’aide intégrée *les rôles de base de données fixes*. Par exemple, le `db_datareader` rôle de base de données fixe peut lire toutes les tables dans la base de données, mais n’apportez aucune modification. Accorder une appartenance à un rôle de base de données fixe à l’aide de la [ALTER ROLE](../t-sql/statements/alter-role-transact-sql.md) instruction. L’exemple suivant ajouter l’utilisateur `Jerry` à la `db_datareader` rôle de base de données fixe.   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

Pour obtenir la liste des rôles de base de données fixes, consultez [rôles au niveau de la base de données](../relational-databases/security/authentication-access/database-level-roles.md).

nsuite, lorsque vous êtes prêt à configurer l’accès à vos données de manière plus précise (hautement recommandé), créez vos propres rôles de base de données définis par l’utilisateur à l’aide de l'instruction [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md). Ensuite, octroyez des autorisations granulaires spécifiques à vos rôles personnalisés.

Par exemple, les instructions suivantes créent un rôle de base de données nommé `Sales`, accordent à ce rôle `Sales` lla possibilité de voir, mettre à jour et supprimer des lignes dans la table `Orders` , puis ajoutent l’utilisateur `Jerry` au rôle `Sales`.   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```   

For more information about the permission system, see [Getting Started with Database Engine Permissions](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).


## Configure row-level security  

[Row-Level Security](../relational-databases/security/row-level-security.md) enables you to restrict access to rows in a database based on the user executing a query. This feature is useful for scenarios like ensuring that customers can only access their own data or that workers can only access data that is pertinent to their department.   

The following steps walk through setting up two Users with different row-level access to the `Sales.SalesOrderHeader` table. 

Create two user accounts to test the row level security:    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```   

Grant read access on the `Sales.SalesOrderHeader` table to both users:    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;    
```   
   
Create a new schema and inline table-valued function. The function returns 1 when a row in the `SalesPersonID` column matches the ID of a `SalesPerson` login or if the user executing the query is the Manager user.   
   
```     
CREATE SCHEMA Security;   
GO   
   
CREATE FUNCTION Security.fn_securitypredicate(@SalesPersonID AS int)     
    RETURNS TABLE   
WITH SCHEMABINDING   
AS     
   RETURN SELECT 1 AS fn_securitypredicate_result    
WHERE ('SalesPerson' + CAST(@SalesPersonId as VARCHAR(16)) = USER_NAME())     
    OR (USER_NAME() = 'Manager');    
```   

Create a security policy adding the function as both a filter and a block predicate on the table:  

```
CRÉER SalesFilter de stratégie de sécurité   
Ajouter Security.fn_securitypredicate(SalesPersonID) de PRÉDICAT de filtre    
  SUR Sales.SalesOrderHeader,   
Ajouter Security.fn_securitypredicate(SalesPersonID) de PRÉDICAT de bloc    
  SUR Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

Execute the following to query the `SalesOrderHeader` table as each user. Verify that `SalesPerson280` only sees the 95 rows from their own sales and that the `Manager` can see all the rows in the table.  

```    
EXÉCUTER en tant qu’utilisateur = 'SalesPerson280' ;   
Sélectionnez * à partir de Sales.SalesOrderHeader ;    
RÉTABLIR ; 
 
EXÉCUTER en tant qu’utilisateur = « Gestionnaire » ;   
Sélectionnez * à partir de Sales.SalesOrderHeader ;   
RÉTABLIR ;   
```
 
Alter the security policy to disable the policy.  Now both users can access all rows. 

```
ALTER SalesFilter de stratégie de sécurité   
AVEC (ÉTAT = OFF) ;    
``` 


## Enable dynamic data masking

[Dynamic Data Masking](../relational-databases/security/dynamic-data-masking.md) enables you to limit the exposure of sensitive data to users of an application by fully or partially masking certain columns. 

Use an `ALTER TABLE` statement to add a masking function to the `EmailAddress` column in the `Person.EmailAddress` table: 
 
```
UTILISER AdventureWorks2014 ; Accédez ALTER TABLE Person.EmailAddress     ALTER colonne EmailAddress    
Ajouter MASKED WITH (fonction = ' email()') ;
``` 
 
Create a new user `TestUser` with `SELECT` permission on the table, then execute a query as `TestUser` to view the masked data:   

```  
CRÉER utilisateur TestUser sans connexion ;   
GRANT SELECT ON Person.EmailAddress à TestUser ;    
 
EXÉCUTER en tant qu’utilisateur = « TestUser » ;   
Sélectionnez EmailAddressID, EmailAddress à partir de Person.EmailAddress ;       
RÉTABLIR ;    
```
 
Verify that the masking function changes the email address in the first record from:
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## Enable Transparent Data Encryption

One threat to your database is the risk that someone will steal the database files off of your hard-drive. This could happen with an intrusion that gets elevated access to your system, through the actions of a problem employee, or by theft of the computer containing the files (such as a laptop).

Transparent Data Encryption (TDE) encrypts the data files as they are stored on the hard drive. The master database of the SQL Server database engine has the encryption key, so that the database engine can manipulate the data. The database files cannot be read without access to the key. High-level administrators can manage, backup, and recreate the key, so the database can be moved, but only by selected people. When TDE is configured, the `tempdb` database is also automatically encrypted. 

Since the Database Engine can read the data, Transparent Data Encryption does not protect against unauthorized access by administrators of the computer who can directly read memory, or access SQL Server through an administrator account.

### Configure TDE

- Create a master key
- Create or obtain a certificate protected by the master key
- Create a database encryption key and protect it by the certificate
- Set the database to use encryption

Configuring TDE requires `CONTROL` permission on the master database and `CONTROL` permission on the user database. Typically an administrator configures TDE. 

The following example illustrates encrypting and decrypting the `AdventureWorks2014` database using a certificate installed on the server named `MyServerCert`.


```
USE master;  
GO  

CRÉER LA CLÉ PRINCIPALE LE CHIFFREMENT PAR MOT DE PASSE = ' ***';  
GO  

CRÉER le certificat MyServerCert avec l’objet = 'Ma base de données clé certificat de chiffrement' ;  
GO  

UTILISER AdventureWorks2014 ;   GO
  
CREATE DATABASE ENCRYPTION KEY  
AVEC L’ALGORITHME = AES_256  
CHIFFREMENT par MyServerCert du certificat de serveur ;  
GO
  
ALTER base de données AdventureWorks2014  
DÉFINIR LE CHIFFREMENT SUR ;   
```

To remove TDE, execute `ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

The encryption and decryption operations are scheduled on background threads by SQL Server. You can view the status of these operations using the catalog views and dynamic management views in the list that appears later in this topic.   

> [!WARNING]
>  Backup files of databases that have TDE enabled are also encrypted by using the database encryption key. As a result, when you restore these backups, the certificate protecting the database encryption key must be available. This means that in addition to backing up the database, you have to make sure that you maintain backups of the server certificates to prevent data loss. Data loss will result if the certificate is no longer available. For more information, see [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  

For more information about TDE, see [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md).   


## Configure backup encryption
SQL Server has the ability to encrypt the data while creating a backup. By specifying the encryption algorithm and the encryptor (a certificate or asymmetric key) when creating a backup, you can create an encrypted backup file.    
  
> [!WARNING]  
>  It is very important to back up the certificate or asymmetric key, and preferably to a different location than the backup file it was used to encrypt. Without the certificate or asymmetric key, you cannot restore the backup, rendering the backup file unusable. 
 
 
The following example creates a certificate, and then creates a backup protected by the certificate.
```
Utilisez master ;   Accédez   BackupEncryptCert de certificat créer   avec l’objet = 'Database sauvegardes' ;   Accédez BACKUP DATABASE [AdventureWorks2014]   sur le disque = N'/var/opt/mssql/backups/AdventureWorks2014.bak'  
par  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHME = AES_256,  
   CERTIFICAT de serveur = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
```

For more information, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).


## Next steps

For more information about the security features of SQL Server, see [Security Center for SQL Server Database Engine and Azure SQL Database](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).
