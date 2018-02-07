---
title: "Prise en main de la sécurité SQL Server sur Linux | Documents Microsoft"
description: "Cette rubrique décrit les actions de sécurité standard."
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.custom: 
ms.workload: Inactive
ms.openlocfilehash: faf7903fc945fc1ce966d6bf6560f55c8d494314
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Procédure pas à pas pour les fonctionnalités de sécurité de SQL Server sur Linux

Si vous êtes un utilisateur Linux pour qui SQL Server est une nouveauté, les tâches suivantes vous guident parmi les tâches de sécurité. Celles-ci ne sont pas uniques ou spécifiques à Linux, mais cela permet de vous donner une idée des domaines à approfondir. Dans chaque exemple, un lien est fourni, menant à la documentation détaillée pour ce domaine.

>  [!NOTE]
>  Les exemples suivants utilisent la base de données exemple **AdventureWorks2014**. Pour obtenir des instructions sur la façon d’obtenir et installer cette base de données exemple, consultez [restaurer une base de données SQL Server à partir de Windows et Linux](sql-server-linux-migrate-restore-database.md).


## <a name="create-a-login-and-a-database-user"></a>Créez une connexion et un utilisateur de base de données 

Accordez l’accès à SQL Server en créant une connexion dans la base de données master à l’aide de la commande [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md). Exemple :

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

>  [!NOTE]
>  Utilisez toujours un mot de passe à la place des astérisques ci-dessus.

Les comptes de connexion peuvent se connecter à SQL Server et avoir accès (avec des autorisations limitées) à la base de données master. Pour vous connecter à une base de données utilisateur, un compte de connexion a besoin d’une identité correspondante au niveau base de données, appelé utilisateur de base de données. Les utilisateurs sont spécifiques à chaque base de données et doivent être créés séparément dans chaque base de données pour leur accorder l’accès. L’exemple suivant vous positionne dans la base de données AdventureWorks2014 et utilise ensuite l'instruction [CREATE USER](../t-sql/statements/create-user-transact-sql.md) pour créer un utilisateur nommé Larry qui est associé à la connexion nommée Larry. Bien que la connexion et l’utilisateur soient liées (mappés l'un à l’autre), ce sont des objets différents. La connexion est un principal (entité de sécurité) de niveau serveur. L’utilisateur est un principal (entité de sécurité) au niveau de la base de données.

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

La connexion Larry peut créer d'autres connexions, et l’utilisateur Jerry peut créer d’autres utilisateurs.


## <a name="granting-access-with-least-privileges"></a>Octroi d’accès avec des privilèges minimum

Les premières personnes à se connecter à une base de données utilisateur seront l’administrateur et les comptes de propriétaire de base de données. Ces utilisateurs possèdent toutes les autorisations disponibles sur la base de données. C'est plus que la plupart des utilisateurs devraient avoir. 

Lorsque vous êtes novice, vous pouvez attribuer des catégories générales d’autorisations à l’aide des *rôles de base de données fixes*. Par exemple, le rôle de base de données fixe `db_datareader` peut lire toutes les tables de la base de données, mais ne peut effectuer aucune modification. Accordez une appartenance à un rôle de base de données fixe à l’aide de l'instruction [ALTER ROLE](../t-sql/statements/alter-role-transact-sql.md). L’exemple suivant ajoute l’utilisateur `Jerry` au rôle de base de données fixe `db_datareader`.   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

Pour obtenir la liste des rôles de base de données fixes, consultez [rôles au niveau de la base de données](../relational-databases/security/authentication-access/database-level-roles.md).

Ensuite, lorsque vous êtes prêt à configurer l’accès à vos données de manière plus précise (hautement recommandé), créez vos propres rôles de base de données définis par l’utilisateur à l’aide de l'instruction [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md). Ensuite, octroyez des autorisations granulaires spécifiques à vos rôles personnalisés.

Par exemple, les instructions suivantes créent un rôle de base de données nommé `Sales`, accordent à ce rôle `Sales` la possibilité de voir, mettre à jour et supprimer des lignes dans la table `Orders`, puis ajoutent l’utilisateur `Jerry` au rôle `Sales`.   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```   

Pour plus d’informations sur le système d’autorisation, consultez [mise en route avec des autorisations du moteur de base de données](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).


## <a name="configure-row-level-security"></a>Configurer la sécurité de niveau ligne  

La [Sécurité de niveau ligne](../relational-databases/security/row-level-security.md) vous permet de restreindre l’accès aux lignes dans une base de données en fonction de l’utilisateur qui exécute une requête. Cette fonctionnalité est utile pour les scénarios où l'on doit s’assurer que les clients peuvent accéder uniquement leurs propres données ou que les employés peuvent accéder uniquement aux données pertinentes pour leur service.   

Les étapes ci-dessous vous guident dans le paramétrage de deux utilisateurs avec différents accès au niveau des lignes de la table `Sales.SalesOrderHeader` . 

Créez deux comptes d’utilisateur pour tester la sécurité au niveau des lignes :    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```   

Accorder l’accès en lecture sur le `Sales.SalesOrderHeader` table pour les deux utilisateurs :    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;    
```   
   
Créer un nouveau schéma et une fonction table en ligne. La fonction renvoie 1 lorsqu’une ligne dans la colonne `SalesPersonID` correspond à l’ID de connexion d'un `vendeur` ou bien si l’utilisateur exécutant la requête est le manager.   
   
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

Créer une stratégie de sécurité ajoutant la fonction aussi bien comme un filtre que comme prédicat bloquant les mises à jour sur la table :  

```
CREATE SECURITY POLICY SalesFilter   
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader,   
ADD BLOCK PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

Exécutez le code suivant pour interroger la table `SalesOrderHeader` en tant que chacun des utilisateurs. Vérifiez que `SalesPerson280` voit uniquement les 95 lignes de leurs propres ventes et que les `Manager` peuvent voir toutes les lignes de la table.  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
REVERT; 
 
EXECUTE AS USER = 'Manager';   
SELECT * FROM Sales.SalesOrderHeader;   
REVERT;   
```
 
Modifiez la stratégie de sécurité pour désactiver la stratégie.  Maintenant les deux utilisateurs peuvent accéder à toutes les lignes. 

```
ALTER SECURITY POLICY SalesFilter   
WITH (STATE = OFF);    
``` 


## <a name="enable-dynamic-data-masking"></a>Activer le masquage dynamique des données

Le [Masquage dynamique des données](../relational-databases/security/dynamic-data-masking.md) vous permet de limiter l’exposition des données sensibles aux utilisateurs d’une application en masquant complètement ou partiellement certaines colonnes. 

Utilisez une instruction `ALTER TABLE` pour ajouter une fonction de masquage à la colonne `EmailAddress` dans la table `Person.EmailAddress`  : 
 
```
USE AdventureWorks2014;
GO
ALTER TABLE Person.EmailAddress    
ALTER COLUMN EmailAddress    
ADD MASKED WITH (FUNCTION = 'email()');
``` 
 
Créez un nouvel utilisateur `TestUser` avec l'autorisation `SELECT` sur la table, puis exécutez une requête en tant que `TestUser` pour afficher les données masquées :   

```  
CREATE USER TestUser WITHOUT LOGIN;   
GRANT SELECT ON Person.EmailAddress TO TestUser;    
 
EXECUTE AS USER = 'TestUser';   
SELECT EmailAddressID, EmailAddress FROM Person.EmailAddress;       
REVERT;    
```
 
Vérifiez que la fonction de masquage modifie l’adresse de messagerie dans le premier enregistrement, en transformant :
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
en 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## <a name="enable-transparent-data-encryption"></a>Activer le chiffrement transparent des données

Une menace pour votre base de données est le risque qu’une personne vole les fichiers de base de données situés sur votre disque dur. Cela peut se produire par une intrusion qui réussirait à obtenir une élévation de ses privilèges d’accès à votre système, les actions d’un employé à problème, ou en cas de vol de l’ordinateur contenant les fichiers (par exemple, un ordinateur portable).

Le chiffrement transparent des données (TDE) chiffre les fichiers de données stockés sur le disque dur. La base de données master du moteur de base de données SQL Server possède la clé de chiffrement, afin que le moteur de base de données puisse manipuler les données. Les fichiers de base de données ne peuvent pas être lus sans accès à la clé. Les administrateurs peuvent administrer, sauvegarder et recréer la clé afin de pouvoir déplacer la base de données, mais ceci ne pourra être fait que par des personnes habilitées. Lorsque le chiffrement transparent des données est configuré, la base de données `tempdb` est automatiquement chiffrée. 

Étant donné que le moteur de base de données peut lire les données, le chiffrement Transparent des données ne protège pas contre les accès non autorisés par les administrateurs de l’ordinateur qui peuvent directement lire la mémoire, ou accéder à SQL Server via un compte d’administrateur.

### <a name="configure-tde"></a>Configurer le chiffrement transparent des données

- Créez une clé principale.
- Créez ou obtenez un certificat protégé par la clé principale.
- Créez une clé de chiffrement de base de données et protégez-la à l'aide du certificat.
- Configurez la base de données pour qu'elle utilise le chiffrement.

La configuration de chiffrement transparent des données requiert l'autorisation `CONTROL` sur la base de données master et `CONTROL` sur la base de données utilisateur. En général, c'est un administrateur qui configure le chiffrement transparent des données. 

L'exemple ci-dessous illustre le chiffrement et le déchiffrement de la base de données `AdventureWorks2014` à l'aide d'un certificat installé sur le serveur nommé `MyServerCert`.


```
USE master;  
GO  

CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**********';  
GO  

CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My Database Encryption Key Certificate';  
GO  

USE AdventureWorks2014;  
GO
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO
  
ALTER DATABASE AdventureWorks2014  
SET ENCRYPTION ON;   
```

Pour supprimer le chiffrement transparent des données, exécutez`ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

Les opérations de chiffrement et le déchiffrement sont planifiées sur des threads d’arrière-plan par SQL Server. Vous pouvez consulter l'état de ces opérations à l'aide des affichages catalogue et des vues de gestion dynamique mentionnés dans la liste fournie plus loin dans cette rubrique.   

>  [!WARNING]
>  Les fichiers de sauvegarde des bases de données pour lesquelles le chiffrement transparent des données est activé sont également chiffrés à l'aide de la clé de chiffrement de base de données. En conséquence, lorsque vous restaurez ces sauvegardes, le certificat qui protège la clé de chiffrement de base de données doit être disponible. Cela signifie qu'en plus de sauvegarder la base de données, vous devez vous assurer que vous conservez des sauvegardes des certificats du serveur pour empêcher toute perte de données. Une perte de données interviendra si le certificat n'est plus disponible. Pour plus d'informations, consultez [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  

Pour plus d’informations sur le chiffrement transparent des données, consultez [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md).   


## <a name="configure-backup-encryption"></a>Configurer le chiffrement de sauvegarde
SQL Server a la possibilité de chiffrer les données lors de la création d’une sauvegarde. En spécifiant l’algorithme de chiffrement et le chiffreur (un certificat ou clé asymétrique) lors de la création d’une sauvegarde, vous pouvez créer un fichier de sauvegarde chiffré.    
  
> [!WARNING]  
>  Il est très important de sauvegarder le certificat ou la clé asymétrique, et de préférence dans un autre emplacement que le fichier de sauvegarde qu'il a servi à chiffrer. Sans le certificat ou la clé asymétrique, vous ne pouvez pas restaurer la sauvegarde, ce qui rend le fichier de sauvegarde inutilisable. 
 
 
L’exemple suivant crée un certificat, puis crée une sauvegarde protégée par le certificat.
```
USE master;  
GO  
CREATE CERTIFICATE BackupEncryptCert   
   WITH SUBJECT = 'Database backups';  
GO 
BACKUP DATABASE [AdventureWorks2014]  
TO DISK = N'/var/opt/mssql/backups/AdventureWorks2014.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
```

Pour plus d’informations, consultez [chiffrement de sauvegarde](../relational-databases/backup-restore/backup-encryption.md).


## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les fonctionnalités de sécurité de SQL Server, consultez [centre de sécurité pour le moteur de base de données SQL Server et la base de données SQL Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).
