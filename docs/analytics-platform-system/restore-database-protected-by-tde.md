---
title: Restaurer une base de données protégée par TDE
description: Procédez comme suit pour restaurer une base de données chiffrée à l’aide du chiffrement transparent des données dans Analytics Platform System Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 53707c62e018b9923f2bb923a4df46f6917d2902
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400439"
---
# <a name="restore-a-database-protected-by-tde-in-parallel-data-warehouse"></a>Restaurer une base de données protégée par TDE en parallèle Data Warehouse
Procédez comme suit pour restaurer une base de données chiffrée à l’aide du chiffrement transparent des données.  
  
L’exemple [Using transparent Data Encryption](transparent-data-encryption.md#using-tde) possède du code pour activer TDE sur `AdventureWorksPDW2012` la base de données. Le code suivant poursuit cet exemple en créant une sauvegarde de la base de données sur l’appliance Analytics Platform System (APS) d’origine, puis en restaurant le certificat et la base de données sur une autre appliance.  
  
La première étape consiste à créer une sauvegarde de la base de données source.  
  
```sql  
BACKUP DATABASE AdventureWorksPDW2012   
TO DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
Préparez le nouvel SQL Server PDW pour TDE en créant une clé principale, en activant le chiffrement et en créant des informations d’identification réseau.  
  
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
  
Les deux dernières étapes recréent le certificat à l’aide des sauvegardes du SQL Server PDW d’origine. Utilisez le mot de passe que vous avez utilisé lors de la création de la sauvegarde du certificat.  
  
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
[BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)  
[Créer une clé](../t-sql/statements/create-master-key-transact-sql.md) 
principale[sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[CRÉER UN CERTIFICAT](../t-sql/statements/create-certificate-transact-sql.md)  
[RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)
  
