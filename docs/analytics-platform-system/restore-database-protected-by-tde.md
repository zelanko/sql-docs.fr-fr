---
title: "Restaurer une base de données protégée par chiffrement transparent des données dans l’entrepôt de données en parallèle"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Utilisez la procédure suivante pour restaurer une base de données est chiffrée à l’aide du chiffrement transparent des données."
ms.date: 10/20/2016
ms.topic: article
ms.assetid: ffb681ca-8598-4614-b06c-660376333fc3
caps.latest.revision: "4"
ms.openlocfilehash: 31f81447bd4fdaf5a2528f5828cc3d70618240c6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="restore-a-database-protected-by-tde"></a>Restaurer une base de données protégée par chiffrement transparent des données
Utilisez la procédure suivante pour restaurer une base de données est chiffrée à l’aide du chiffrement transparent des données.  
  
Le [à l’aide de Transparent Data Encryption](transparent-data-encryption.md#using-tde) exemple compose du code pour activer le chiffrement transparent des données sur le `AdventureWorksPDW2012` base de données. Le code suivant continue de cet exemple, en créant une sauvegarde de la base de données sur le matériel de système de plateforme Analytique (APS) d’origine, puis de restaurer le certificat et la base de données sur un autre dispositif.  
  
La première étape consiste à créer une sauvegarde de la base de données source.  
  
```sql  
BACKUP DATABASE AdventureWorksPDW2012   
TO DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
Préparer le nouveau SQL Server PDW pour le chiffrement transparent des données en créant une clé principale, l’activation du chiffrement et créer des informations d’identification réseau.  
  
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
  
Les deux dernières étapes recréez le certificat en utilisant les sauvegardes à partir de l’origine de SQL Server PDW. Utilisez le mot de passe que vous avez utilisé lorsque vous avez créé la sauvegarde du certificat.  
  
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
[CRÉER LE CERTIFICAT](../t-sql/statements/create-certificate-transact-sql.md)  
[RESTAURER LA BASE DE DONNÉES](../t-sql/statements/restore-database-parallel-data-warehouse.md)
  
