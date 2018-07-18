---
title: Leçon 5. (Facultatif) Chiffrer votre base de données à l’aide du chiffrement transparent des données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c73078a44d45d10fae144eb0d15db8995b556ed8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275165"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a>Leçon 5. (Facultatif) Chiffrer votre base de données avec TDE
  En tant qu'étape facultative, chiffrez la base de données créée. Le chiffrement transparent des données (TDE, Transparent Data Encryption) effectue le chiffrement et le déchiffrement des E/S en temps réel des fichiers de données et des fichiers journaux. Le type de chiffrement utilise une clé de chiffrement de base de données (DEK), stockée dans l'enregistrement de démarrage de base de données pour être disponible pendant la récupération. Pour plus d’informations, consultez [Transparent Data Encryption &#40;TDE&#41; ](security/encryption/transparent-data-encryption.md) et [déplacer une base de données protégé par chiffrement transparent des données vers un autre serveur SQL](security/encryption/move-a-tde-protected-database-to-another-sql-server.md).  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous disposez d'un compte Microsoft Azure Storage.  
  
-   Vous avez créé un conteneur sous votre compte Microsoft Azure Storage.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé des informations d'identification SQL Server sur l'ordinateur source.  
  
-   Vous avez créé une base de données en suivant la procédure décrite dans la leçon 4.  
  
 Si vous souhaitez chiffrer une base de données, procédez comme suit :  
  
1.  Sur l'ordinateur source, modifiez et exécutez les instructions suivantes dans une fenêtre de requête :  
  
    ```  
  
    -- Create a master key and a server certificate   
    USE master   
    GO   
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01';   
    GO   
    CREATE CERTIFICATE MySQLCert WITH SUBJECT = 'SQL - Azure Storage Certification'   
    GO   
    -- Create a backup of the server certificate in the master database.   
    -- Store TDS certificates in the source machine locally.   
    BACKUP CERTIFICATE MySQLCert   
    TO FILE = 'C:\certs\MySQLCert.CER'   
    WITH PRIVATE KEY   
    (   
    FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
    ENCRYPTION BY PASSWORD = 'MySQLKey01'   
    );  
  
    ```  
  
2.  Ensuite, chiffrez votre nouvelle base de données dans l'ordinateur source en procédant comme suit :  
  
    ```  
  
    -- Switch to the new database.   
    -- Create a database encryption key, that is protected by the server certificate in the master database.    
    -- Alter the new database to encrypt the database using TDE.   
    USE TestDB1;   
    GO   
    -- Encrypt your database   
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE MySQLCert   
    GO   
  
    ALTER DATABASE TestDB1   
    SET ENCRYPTION ON   
    GO  
  
    ```  
  
 Si vous voulez connaître l'état de chiffrement d'une base de données et ses clés de chiffrement associées, exécutez l'instruction suivante :  
  
```  
  
SELECT * FROM sys.dm_database_encryption_keys;   
GO  
  
```  
  
 Pour les instructions Transact-SQL des informations détaillées qui ont été utilisées dans cette leçon, consultez [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER DATABASE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql), [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql), et [sys.dm_database_ encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).  
  
 **Leçon suivante :**  
  
 [Leçon 6 : Migrer une base de données d’une machine source locale vers une machine de destination dans Microsoft Azure](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
