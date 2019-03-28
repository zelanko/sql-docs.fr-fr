---
title: Leçon 9. Restaurer une base de données du stockage Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 38d807fae60099022e847e4799196305ccfbadf8
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534441"
---
# <a name="lesson-9-restore-a-database-from-windows-azure-storage"></a>Leçon 9. Restaurer une base de données du Stockage Microsoft Azure
  Dans cette leçon, vous allez apprendre comment restaurer un fichier de sauvegarde de base de données du Stockage Microsoft Azure dans une base de données, qui s'exécute localement ou dans une machine virtuelle Microsoft Azure. Pour suivre cette leçon, vous n'avez pas besoin de terminer les leçons 4, 5, 6, 7 et 8.  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous avez créé une base de données sur l'ordinateur source.  
  
-   Vous avez créé une sauvegarde de votre base de données (.bak) dans le stockage Windows Azure à l’aide de la [Sauvegarde et restauration SQL Server avec le service de stockage d'objets blob Windows Azure](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) fonctionnalité. Notez que vous devez créer d'autres informations d'identification SQL Server au cours de cette étape. Ces informations d'identification utilisent des clés de compte de stockage.  
  
-   Vous disposez d'un compte Microsoft Azure Storage.  
  
-   Vous avez créé un conteneur sous votre compte Microsoft Azure Storage.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé des informations d'identification SQL Server sur votre ordinateur pour la fonctionnalité Intégration du Stockage Microsoft Azure. Notez que ces informations d'identification nécessitent une clé de signature d'accès partagé (SAS).  
  
 Pour restaurer une base de données du Stockage Microsoft Azure, procédez comme suit :  
  
1.  Démarrez SQL Server Management Studio. Connectez-vous à l'instance par défaut.  
  
2.  Cliquez sur **nouvelle requête** sur la barre d’outils Standard.  
  
3.  Copiez et collez la totalité du script suivant dans la fenêtre de requête. Modifiez le script en fonction des besoins.  
  
     **Remarque :** Vous exécutez le `RESTORE` instruction pour restaurer la sauvegarde de base de données (.bak) dans le stockage Windows Azure à une instance de base de données dans un autre ordinateur.  
  
    ```sql  
  
    USE master   
    GO   
    -- Create a new database to be backed up.   
    CREATE DATABASE TestDbRestoreFrom;   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    SELECT * from dbo.Table1;   
    GO   
    -- Create a credential to be used by SQL Server Backup and Restore with Windows Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Windows Azure Storage.   
    BACKUP DATABASE TestDBRestoreFrom    
    TO URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
          WITH CREDENTIAL = 'BackupCredential'    
         ,COMPRESSION   
         ,STATS = 5;   
    GO    
    -- Create a Shared Access Signature credential   
    CREATE CREDENTIAL [https://teststorageaccnt.blob.core.windows.net/testrestorefrom]   
    WITH IDENTITY='SHARED ACCESS SIGNATURE',   
    SECRET = 'sv=2012-02-12&sr=c&si=policy_resfrom&sig=EhVpzLUXjG4ThAMLmVhrnoiCt8IfmD3BsuYiMawGzxc%3D'   
    GO   
    USE master;   
    GO   
    RESTORE DATABASE TestDBRestoreFrom    
    FROM URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
    WITH    
    CREDENTIAL = 'BackupCredential',    
    REPLACE,   
    MOVE 'TestDBRestoreFrom' TO 'C:\Backup\TestDBRestoreFrom.mdf',     
    MOVE 'TestDBRestoreFrom_log' TO 'C:\Backup\TestDBRestoreFrom_log.ldf';   
    GO  
  
    ```  
  
 **Fin du didacticiel : Fichiers de données SQL Server dans le service de stockage Windows Azure**  
  
  
