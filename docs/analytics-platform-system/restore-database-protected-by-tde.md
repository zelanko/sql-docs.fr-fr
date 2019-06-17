---
title: Restaurer une base de données protégée par TDE - Parallel Data Warehouse | Microsoft Docs
description: Utilisez les étapes suivantes pour restaurer une base de données est chiffrée à l’aide du chiffrement transparent des données dans Analytique Platform System Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: a791d4110dc70c506025f8f11fb06b9ba2e5dcb3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63157016"
---
# <a name="restore-a-database-protected-by-tde-in-parallel-data-warehouse"></a>Restaurer une base de données protégée par TDE dans Parallel Data Warehouse
Utilisez les étapes suivantes pour restaurer une base de données est chiffrée à l’aide du chiffrement transparent des données.  
  
Le [à l’aide de Transparent Data Encryption](transparent-data-encryption.md#using-tde) exemple a du code pour activer TDE sur la `AdventureWorksPDW2012` base de données. Le code suivant poursuit à cet exemple, en créant une sauvegarde de la base de données sur l’appliance Analytique Platform System (APS) d’origine, puis en restaurant le certificat et la base de données sur un matériel différent.  
  
La première étape consiste à créer une sauvegarde de la base de données source.  
  
```sql  
BACKUP DATABASE AdventureWorksPDW2012   
TO DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
Préparer le nouveau SQL Server PDW pour le chiffrement transparent des données en créant une clé principale, l’activation du chiffrement et création d’une information d’identification réseau.  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
Les deux dernières étapes recréez le certificat à l’aide de sauvegardes à partir de l’origine de SQL Server PDW. Utilisez le mot de passe que vous avez utilisé lorsque vous avez créé la sauvegarde du certificat.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert  
    FROM FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'   
    WITH PRIVATE KEY (FILE = '\\SECURE_SERVER\cert\MyServerCert.key',   
    DECRYPTION BY PASSWORD = '<password>');  
  
RESTORE DATABASE AdventureWorksPDW2012   
    FROM DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>Voir aussi  
[BASE DE DONNÉES DE SAUVEGARDE](../t-sql/statements/backup-database-parallel-data-warehouse.md)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md) 
[sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[CREATE CERTIFICATE](../t-sql/statements/create-certificate-transact-sql.md)  
[RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)
  
