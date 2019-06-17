---
title: 'Leçon 6 : Migrer une base de données à partir d’une source de l’ordinateur local vers un ordinateur de destination dans Windows Azure | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1a5787a3f5aecd746ac9aafd5850e6109ebcd999
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66090693"
---
# <a name="lesson-6-migrate-a-database-from-a-source-machine-on-premises-to-a-destination-machine-in-windows-azure"></a>Leçon 6 : Migrer une base de données d’une machine source locale vers une machine de destination dans Windows Azure
  Cette leçon suppose que vous avez déjà une autre instance SQL Server, pouvant résider sur un autre ordinateur local ou dans une machine virtuelle Windows Azure. Pour plus d’informations sur la création d’une machine virtuelle SQL Server dans Windows Azure, consultez [approvisionnement d’une Machine virtuelle de SQL Server sur Windows Azure](http://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/). Après avoir déployé une machine virtuelle SQL Server dans Windows Azure, assurez-vous que vous pouvez vous connecter à une instance de SQL Server dans cette machine virtuelle via SQL Server Management Studio sur un autre ordinateur.  
  
 Cette leçon suppose également que vous avez déjà effectué les étapes suivantes :  
  
-   Vous disposez d'un compte Microsoft Azure Storage.  
  
-   Vous avez créé un conteneur sous votre compte Microsoft Azure Storage.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé des informations d'identification SQL Server sur l'ordinateur source.  
  
-   Vous avez déjà créé une machine virtuelle SQL Server de destination dans Windows Azure. Nous vous recommandons de la créer en sélectionnant une image de plateforme comprenant SQL Server 2014.  
  
 Pour migrer une base de données de SQL Server local vers une autre machine virtuelle dans Windows Azure, procédez comme suit :  
  
1.  Dans l'ordinateur source (un ordinateur local dans ce didacticiel), ouvrez une fenêtre de requête dans SQL Server Management Studio. Détachez votre base de données pour la déplacer vers un autre ordinateur en exécutant ces instructions :  
  
    ```  
    -- Detach the database in the source machine   
    USE master  
    EXEC sp_detach_db 'TestDB1', 'true';  
    ```  
  
2.  Si vous devez transférer une base de données vers un ordinateur de destination, vous devez d'abord le préparer. Pour préparer l'ordinateur de destination, vous devez d'abord créer des informations d'identification SQL Server sur l'ordinateur de destination. S'il s'agit d'une base de données chiffrée, vous devez également importer le certificat de l'ordinateur source vers l'ordinateur de destination.  
  
    1.  Pour créer des informations d'identification SQL Server sur l'ordinateur de destination, procédez comme suit :  
  
        1.  Connectez-vous à l'ordinateur de destination via SQL Server Management Studio sur votre ordinateur source.  Sinon, démarrez SQL Server Management Studio directement sur votre ordinateur de destination.  
  
        2.  Dans la barre d’outils Standard, cliquez sur **nouvelle requête**.  
  
        3.  Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire. L’instruction suivante crée une information d’identification du serveur SQL pour stocker le certificat d’accès partagé de votre conteneur de stockage.  
  
            ```sql  
  
            USE master   
            GO   
            CREATE CREDENTIAL [http://teststorageaccnt.blob.core.windows.net/testcontainer]   
            WITH IDENTITY='SHARED ACCESS SIGNATURE',   
            SECRET = 'your SAS key'   
            GO  
  
            ```  
  
        4.  Pour voir toutes les informations d'identification disponibles, exécutez l'instruction suivante dans la fenêtre de requête :  
  
            ```sql  
            SELECT * from sys.credentials   
            ```  
  
        5.  Une fois connecté au serveur de destination, ouvrez la fenêtre de requête, et exécutez :  
  
            ```sql  
  
            -- Create a master key and a server certificate   
            USE master   
            GO   
            CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01'; -- You may use a different password.   
            GO   
            CREATE CERTIFICATE MySQLCert   
            FROM FILE = 'C:\certs\MySQLCert.CER'   
            WITH PRIVATE KEY   
            (   
            FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
            DECRYPTION BY PASSWORD = 'MySQLKey01'   
            );   
            GO  
  
            ```  
  
             À l'issue de cette étape, l'ordinateur de destination a importé le certificat de chiffrement qui a été sauvegardé depuis l'ordinateur source. Ensuite, joignez les fichiers de données dans l'ordinateur de destination.  
  
    2.  Ensuite, créez une base de données avec des données et des fichiers journaux pointant vers les fichiers existants dans le Stockage Microsoft Azure en utilisant l'option FOR ATTACH. Dans la fenêtre de requête, exécutez l'instruction suivante :  
  
        ```sql  
  
        --Create a database on the destination server   
        CREATE DATABASE TestDB1onDest   
        ON   
        (NAME = TestDB1_data,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf' )   
        LOG ON   
         (NAME = TestDB1_log,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
        FOR ATTACH   
        GO  
  
        ```  
  
    3.  Dans l'Explorateur d'objets, cliquez avec le bouton droit sur Bases de données, puis cliquez sur Actualiser. La base de données TestDB1onDest nouvellement créée doit s'afficher.  
  
    4.  Ensuite, dans la fenêtre de requête, exécutez l'instruction suivante :  
  
        ```sql  
  
        USE TestDB1onDest   
        SELECT * FROM Table1;   
        GO  
  
        ```  
  
         Elle doit répertorier toutes les données entrées dans la leçon 4.  
  
 Notez que la base de données chiffrée a été transférée vers une autre instance de calcul sans déplacer de données.  
  
 Pour créer une base de données avec des fichiers de données et des fichiers journaux pointant vers les fichiers existants dans le Stockage Microsoft Azure à l'aide de l'interface utilisateur de SQL Server Management Studio, procédez comme suit :  
  
1.  Dans l’ **Explorateur d’objets**, connectez-vous à une instance du moteur de base de données SQL Server et développez-la.  
  
2.  Cliquez avec le bouton droit sur **Bases de données**, puis cliquez sur **Nouvelle base de données**. Ensuite, cliquez avec le bouton droit sur TestDB1. Cliquez sur Tâches, puis cliquez sur Détacher. Dans la fenêtre de dialogue Détacher, cochez Supprimer les connexions. Cliquez sur **OK**.  
  
3.  Connectez-vous à l'ordinateur de destination, sur lequel SQL Server 2014 CTP2 ou version ultérieure est installé. Pour préparer l'ordinateur de destination, vous devez créer des informations d'identification SQL Server sur l'ordinateur de destination de façon à indiquer le même conteneur que celui qui contient TestDB1. Si vous rattachez dans le même ordinateur, vous n'avez pas besoin de créer d'autres informations d'identification.  
  
4.  Dans **Explorateur d’objets**, avec le bouton droit **bases de données** et cliquez sur **attacher**.  
  
5.  Dans le **attacher les bases de données** boîte de dialogue pour spécifier la base de données à attacher, cliquez sur **ajouter**. Dans le **rechercher les fichiers de base de données** boîte de dialogue :  
  
     Pour l’emplacement du fichier de données de base de données, tapez : `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.  
  
     Pour le nom de fichier, tapez : `TestDB1Data.mdf`.  
  
6.  Cliquez sur **OK**.  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")  
  
 **Leçon suivante :**  
  
 [Leçon 7 : Déplacer vos fichiers de données vers le stockage Windows Azure](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
  
