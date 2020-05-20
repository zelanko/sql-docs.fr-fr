---
title: 'Leçon 7 : déplacer vos fichiers de données vers le stockage Azure | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e31789b1f2cf5b2206af400c7c7798f7761f1e6c
ms.sourcegitcommit: 37a3e2c022c578fc3a54ebee66d9957ff7476922
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82922069"
---
# <a name="lesson-7-move-your-data-files-to-azure-storage"></a>Leçon 7 : Déplacer vos fichiers de données dans le Stockage Azure
  Dans cette leçon, vous allez apprendre à déplacer vos fichiers de données vers le stockage Azure (mais pas votre instance SQL Server). Pour suivre cette leçon, vous n'avez pas besoin de terminer les leçons 4, 5 et 6.  
  
 Pour déplacer vos fichiers de données vers le stockage Azure, vous pouvez utiliser l' `ALTER DATABASE` instruction, car elle permet de modifier l’emplacement des fichiers de données.  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous avez un compte de stockage Azure.  
  
-   Vous avez créé un conteneur sous votre compte de stockage Azure.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé des informations d'identification SQL Server sur l'ordinateur source.  
  
 Ensuite, procédez comme suit pour déplacer vos fichiers de données vers le stockage Azure :  
  
1.  Tout d'abord, créez une base de données de test dans la machine source et ajoutez-lui des données.  
  
    ```sql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  Exécutez le code ci-dessous :  
  
    ```sql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  Lorsque vous exécutez cette opération, le message suivant s’affiche : « le fichier «TestDB1Alter » a été modifié dans le catalogue système. Le nouveau chemin sera utilisé au prochain démarrage de la base de données.»  
  
4.  Ensuite, mettez la base de données hors connexion.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  À présent, vous devez copier les fichiers de données vers le stockage Azure à l’aide de l’une des méthodes suivantes : [outil AzCopy](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs), [page put](https://msdn.microsoft.com/library/azure/ee691975.aspx), référence de la [bibliothèque cliente de stockage](https://msdn.microsoft.com/library/azure/dn261237.aspx)ou outil d’exploration de stockage tiers.  
  
     **Important :** Lorsque vous utilisez cette nouvelle amélioration, veillez toujours à créer un objet blob de pages et non un objet blob de blocs.  
  
6.  Ensuite, mettez la base de données en ligne.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **Leçon suivante :**  
  
 [Leçon 8. Restaurer une base de données dans Azure Storage](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
