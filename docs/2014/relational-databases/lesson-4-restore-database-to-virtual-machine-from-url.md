---
title: Leçon 5. Facultatif Chiffrer votre base de données à l’aide de TDE | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fb9eaf62514b76e35b73ea87b7820751f670a90f
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70175576"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a>Leçon 5. (Facultatif) Chiffrer votre base de données avec TDE
  En tant qu'étape facultative, chiffrez la base de données créée. Le chiffrement transparent des données (TDE, Transparent Data Encryption) effectue le chiffrement et le déchiffrement des E/S en temps réel des fichiers de données et des fichiers journaux. Le type de chiffrement utilise une clé de chiffrement de base de données (DEK), stockée dans l'enregistrement de démarrage de base de données pour être disponible pendant la récupération. Pour plus d’informations, [consultez &#40;transparent Data Encryption&#41; TDE](security/encryption/transparent-data-encryption.md) et [déplacer une base de données protégée TDE vers une autre SQL Server](security/encryption/move-a-tde-protected-database-to-another-sql-server.md).  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous avez un compte de stockage Azure.  
  
-   Vous avez créé un conteneur sous votre compte de stockage Azure.  
  
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
  
 Pour obtenir des informations détaillées sur les instructions Transact-SQL utilisées dans cette leçon, consultez [Create &#40;Database SQL Server Transact-&#41;SQL](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER &#40;Database Transact-&#41;SQL](/sql/t-sql/statements/alter-database-transact-sql), [Create &#40; Master Key Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [Create &#40;Certificate Transact&#41;-SQL](/sql/t-sql/statements/create-certificate-transact-sql)et [sys. DM &#40;_database_encryption_keys Transact-&#41;SQL](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).  
  
 **Leçon suivante :**  
  
 [Leçon 6 : Migrer une base de données d’une machine source locale vers une machine de destination dans Azure](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
