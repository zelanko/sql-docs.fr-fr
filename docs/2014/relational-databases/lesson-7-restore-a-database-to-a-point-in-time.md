---
title: Leçon 8. Restaurer une base de données vers le stockage Windows Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9e0841c3473baf73033f298cfd3c8402ffc3aa19
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743344"
---
# <a name="lesson-8-restore-a-database-to-windows-azure-storage"></a>Leçon 8. Restaurer une base de données dans le Stockage Microsoft Azure
  Dans cette leçon, vous allez apprendre comment créer un fichier de sauvegarde localement, puis le restaurer dans le Stockage Microsoft Azure. Notez que vous votre base de données peut être locale ou dans une machine virtuelle Windows Azure. Pour suivre cette leçon, vous n'avez pas besoin de terminer les leçons 4, 5, 6 et 7.  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous disposez d'un compte Microsoft Azure Storage.  
  
-   Vous avez créé un conteneur sous votre compte Microsoft Azure Storage.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé des informations d'identification SQL Server sur l'ordinateur source reposant sur la signature d'accès partagé.  
  
-   Vous avez créé une base de données sur l'ordinateur source.  
  
 Pour restaurer une base de données dans le Stockage Microsoft Azure, procédez comme suit :  
  
1.  Sur l'ordinateur source, démarrez SQL Server Management Studio.  
  
2.  Lorsque vous êtes connecté à la base de données nouvellement créée, ouvrez la fenêtre de requête. Exécutez l'instruction suivante :  
  
    ```sql  
  
    USE TestDB3Restore;   
    GO   
    BACKUP DATABASE TestDB3Restore   
    TO DISK = 'C:\BACKUP\TestDB3Restore.Bak'   
       WITH FORMAT,   
       NAME = 'Full Backup of TestDB3Restore'   
    GO  
  
    ```  
  
3.  Ensuite, copiez et exécutez les instructions suivantes dans la fenêtre de requête :  
  
    ```sql  
  
    USE master;   
    GO   
    RESTORE DATABASE TestDB3Restore    
    FROM DISK = 'C:\BACKUP\TestDB3Restore.bak'    
    WITH REPLACE,   
    MOVE 'TestDB3Restore' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore.mdf',     
    MOVE 'TestDB3Restore_log' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore_log.ldf';   
    GO  
  
    ```  
  
     À l'issue de cette étape, votre conteneur doit répertorier les fichiers de données (.mdf) et les fichiers (.ldf) sur le Portail de gestion.  
  
 Pour restaurer une base de données avec des fichiers de données et des fichiers journaux pointant vers le Stockage Microsoft Azure à l'aide de l'interface utilisateur de SQL Server Management Studio, procédez comme suit :  
  
1.  Dans **Explorateur d’objets**, cliquez sur le nom du serveur pour développer l’arborescence du serveur.  
  
2.  Développez **bases de données**et sélectionnez votre base de données.  
  
3.  Cliquez avec le bouton droit sur la base de données, pointez sur **Tâches**, puis cliquez sur **Restaurer**.  
  
4.  Sur le **général** page, dans le **restaurer** section de la source, cliquez sur **Source** appareil.  
  
5.  Cliquez sur le bouton Parcourir pour le **Source** zone de texte de l’appareil, ce qui ouvre le **sélectionner les unités de sauvegarde** boîte de dialogue.  
  
6.  Dans la zone de texte de support de sauvegarde, sélectionnez **fichier**, puis cliquez sur le **ajouter** pour localiser le fichier de sauvegarde (.bak). Cliquez sur **OK**.  
  
7.  Cliquez sur **fichiers** sur la première page.  
  
8.  Dans le **restaurer les fichiers de base de données** comme section sous **restaurer sous** , tapez ce qui suit :  
  
     Pour le fichier de données, tapez : `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`. Pour le fichier journal, tapez : `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`.  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")  
  
9. Cliquez sur **OK**.  
  
 Lorsque la restauration est effectuée, connectez-vous au Portail de gestion. Vous devez pouvoir consulter les fichiers .mdf et .ldf dans le conteneur comme suit :  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")  
  
 **Leçon suivante :**  
  
 [Leçon 9 : Restaurer une base de données depuis Stockage Microsoft Azure](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
