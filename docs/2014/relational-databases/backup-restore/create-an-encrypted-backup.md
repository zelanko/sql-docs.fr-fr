---
title: Créer une sauvegarde chiffrée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b2f16425978b1e6ddc560aabd445b6cfe6737b57
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70154754"
---
# <a name="create-an-encrypted-backup"></a>Créer une sauvegarde chiffrée
  Cette rubrique décrit les étapes nécessaires pour créer une sauvegarde chiffrée à l'aide de Transact-SQL.  
  
## <a name="backup-to-disk-with-encryption"></a>Sauvegarde sur disque avec chiffrement  
 **Conditions préalables**  
  
-   Accès à un disque local ou à un stockage disposant de l'espace approprié pour créer une sauvegarde de la base de données.  
  
-   Une clé principale de base de données pour la base de données master, et un certificat ou une clé asymétrique disponible sur l'instance de SQL Server. Pour les conditions et les autorisations de chiffrement, consultez [Backup Encryption](backup-encryption.md).  
  
 Utilisez la procédure suivante pour créer une sauvegarde chiffrée d'une base de données sur un disque local. Cet exemple utilise une base de données utilisateur appelée MyTestDB.  
  
1.  **Créez une clé principale de base de données de la base de données Master :** Choisissez un mot de passe pour chiffrer la copie de la clé principale qui sera stockée dans la base de données. Connectez-vous au moteur de base de données, ouvrez une nouvelle fenêtre de requête, copiez et collez l'exemple, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  **Créer un certificat de sauvegarde :** Créez un certificat de sauvegarde dans la base de données Master. Copiez et collez l’exemple suivant dans la fenêtre de requête et cliquez sur **exécuter** .  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  **Sauvegardez la base de données :** Spécifiez l’algorithme de chiffrement et le certificat à utiliser. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 Pour obtenir un exemple de chiffrement d’une sauvegarde protégée par une gestion de clés extensible, consultez [Gestion de clés extensible à l’aide d’Azure Key Vault &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
### <a name="backup-to-azure-storage-with-encryption"></a>Sauvegarder dans le Stockage Azure avec chiffrement  
 Si vous créez une sauvegarde dans le stockage Azure à l’aide de l’option **Sauvegarde SQL Server vers une URL**, les étapes de chiffrement sont identiques, mais vous devez utiliser l’URL de destination et les informations d’identification SQL pour l’authentification dans le stockage Azure. Si vous souhaitez configurer [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] à l’aide des options de chiffrement, consultez Configuration de la [SQL Server gestion de la sauvegarde sur Azure](enable-sql-server-managed-backup-to-microsoft-azure.md) et configuration d' [SQL Server sauvegarde managée sur Azure pour les groupes de disponibilité](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 **Conditions préalables**  
  
-   Un compte de stockage Windows et un conteneur. Pour plus d’informations, consultez. [Leçon 1 : créer des objets de stockage Azure](../../tutorials/lesson-1-create-windows-azure-storage-objects.md).  
  
-   Une clé principale de base de données pour la base de données master, et un certificat ou une clé asymétrique sur l'instance de SQL Server. Pour les conditions et les autorisations de chiffrement, consultez [Backup Encryption](backup-encryption.md).  
  
1.  **Créer SQL Server informations d’identification :** Pour créer des informations d’identification de SQL Server, connectez-vous à la Moteur de base de données, ouvrez une nouvelle fenêtre de requête, copiez et collez l’exemple suivant, puis cliquez sur **exécuter**.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  **Créer une clé principale de base de données :** Choisissez un mot de passe pour chiffrer la copie de la clé principale qui sera stockée dans la base de données. Connectez-vous au moteur de base de données, ouvrez une nouvelle fenêtre de requête, copiez et collez l'exemple, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  **Créer un certificat de sauvegarde :** Créez un certificat de sauvegarde dans la base de données Master. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  **Sauvegardez la base de données :** Spécifiez l’algorithme de chiffrement et le certificat à utiliser. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' - this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
