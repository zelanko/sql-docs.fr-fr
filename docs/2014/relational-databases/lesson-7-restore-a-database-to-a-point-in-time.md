---
title: Leçon 8. Restaurer une base de données dans Azure Storage | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3f17384b979e960995a3522a81c4f0611287cb15
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153741"
---
# <a name="lesson-8-restore-a-database-to-azure-storage"></a>Leçon 8. Restaurer une base de données dans Azure Storage
  Dans cette leçon, vous allez apprendre à créer un fichier de sauvegarde localement, puis à le restaurer dans le stockage Azure. Notez que vous pouvez faire en sorte que votre base de données soit locale ou dans une machine virtuelle dans Azure. Pour suivre cette leçon, vous n'avez pas besoin de terminer les leçons 4, 5, 6 et 7.  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous avez un compte de stockage Azure.  
  
-   Vous avez créé un conteneur sous votre compte de stockage Azure.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé des informations d'identification SQL Server sur l'ordinateur source reposant sur la signature d'accès partagé.  
  
-   Vous avez créé une base de données sur l'ordinateur source.  
  
 Pour restaurer une base de données dans Azure Storage, procédez comme suit:  
  
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
  
 Pour restaurer une base de données avec des fichiers de données et des fichiers journaux pointant vers Azure Storage à l’aide de SQL Server Management Studio interface utilisateur, procédez comme suit:  
  
1.  Dans l' **Explorateur d’objets**, cliquez sur le nom du serveur pour développer l’arborescence du serveur.  
  
2.  Développez **bases de données**, puis sélectionnez votre base de données.  
  
3.  Cliquez avec le bouton droit sur la base de données, pointez sur **Tâches**, puis cliquez sur **Restaurer**.  
  
4.  Sur la page **général** , dans la section source de **restauration** , cliquez sur périphérique **source** .  
  
5.  Cliquez sur le bouton Parcourir de la zone de texte périphérique **source** pour ouvrir la boîte de dialogue **Sélectionner les unités de sauvegarde** .  
  
6.  Dans la zone de texte support de sauvegarde, sélectionnez **fichier**, puis cliquez sur le bouton **Ajouter** pour localiser le fichier de sauvegarde (. bak). Cliquez sur **OK**.  
  
7.  Cliquez sur **fichiers** sur la première page.  
  
8.  Dans la section **restaurer les fichiers de la base de données** en tant que, sous le champ **Restaurer sous** , tapez les éléments suivants:  
  
     Pour fichier de données, tapez `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`:. Pour fichier journal, tapez: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`.  
  
     ![CTP2 SQL 14](../tutorials/media/ss-was-tutlesson-8-8.gif "CTP2 SQL 14")  
  
9. Cliquez sur **OK**.  
  
 Lorsque la restauration est effectuée, connectez-vous au Portail de gestion. Vous devez pouvoir consulter les fichiers .mdf et .ldf dans le conteneur comme suit :  
  
 ![CTP2 SQL 14](../tutorials/media/ss-was-tutlesson-8-9.gif "CTP2 SQL 14")  
  
 **Leçon suivante :**  
  
 [Leçon 9 : Restaurer une base de données à partir du stockage Azure](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
