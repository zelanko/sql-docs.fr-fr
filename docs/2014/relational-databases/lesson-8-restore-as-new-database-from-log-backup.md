---
title: Leçon 9. Restaurer une base de données à partir du stockage Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 464961600f69f14a2b66515a75906c0fd4af3f82
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70175356"
---
# <a name="lesson-9-restore-a-database-from-azure-storage"></a>Leçon 9. Restaurer une base de données à partir du Stockage Azure
  Dans cette leçon, vous allez apprendre à restaurer un fichier de sauvegarde de base de données à partir du stockage Azure dans une base de données, qui réside localement ou dans une machine virtuelle dans Azure. Pour suivre cette leçon, vous n'avez pas besoin de terminer les leçons 4, 5, 6, 7 et 8.  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous avez créé une base de données sur l'ordinateur source.  
  
-   Vous avez créé une sauvegarde de votre base de données (. bak) dans le stockage Azure à l’aide de la fonctionnalité [SQL Server sauvegarde et restauration avec le service de stockage d’objets BLOB Azure](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) . Notez que vous devez créer d'autres informations d'identification SQL Server au cours de cette étape. Ces informations d'identification utilisent des clés de compte de stockage.  
  
-   Vous avez un compte de stockage Azure.  
  
-   Vous avez créé un conteneur sous votre compte de stockage Azure.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé un SQL Server des informations d’identification sur votre ordinateur pour la fonctionnalité d’intégration du stockage Azure. Notez que ces informations d'identification nécessitent une clé de signature d'accès partagé (SAS).  
  
 Pour restaurer une base de données à partir du stockage Azure, procédez comme suit :  
  
1.  Exécutez SQL Server Management Studio. Connectez-vous à l'instance par défaut.  
  
2.  Cliquez sur **nouvelle requête** dans la barre d’outils standard.  
  
3.  Copiez et collez la totalité du script suivant dans la fenêtre de requête. Modifiez le script en fonction des besoins.  
  
     **Remarque :** Vous exécutez l' `RESTORE` instruction pour restaurer la sauvegarde de base de données (. bak) dans le stockage Azure vers une instance de base de données sur un autre ordinateur.  
  
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
    -- Create a credential to be used by SQL Server Backup and Restore with Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Azure Storage.   
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
  
 **Fin du didacticiel : SQL Server de fichiers de données dans le service de stockage Azure**  
  
  
