---
title: 'Leçon 7 : Déplacer vos fichiers de données vers le stockage Windows Azure | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d88e1fa7853c1207f1a8c95da2f96bb77dd7d49c
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53355336"
---
# <a name="lesson-7-move-your-data-files-to-windows-azure-storage"></a>Leçon 7 : Déplacement des fichiers de données dans le Stockage Microsoft Azure
  Dans cette leçon, vous allez apprendre comment déplacer les fichiers de données vers le Stockage Microsoft Azure (mais pas vers l'instance SQL Server). Pour suivre cette leçon, vous n'avez pas besoin de terminer les leçons 4, 5 et 6.  
  
 Pour déplacer les fichiers de données vers le Stockage Microsoft Azure, utilisez l'instruction `ALTER DATABASE`, car elle permet de modifier l'emplacement des fichiers de données.  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous disposez d'un compte Microsoft Azure Storage.  
  
-   Vous avez créé un conteneur sous votre compte Microsoft Azure Storage.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé des informations d'identification SQL Server sur l'ordinateur source.  
  
 Ensuite, procédez comme suit pour déplacer les fichiers de données vers le Stockage Microsoft Azure :  
  
1.  Tout d'abord, créez une base de données de test dans la machine source et ajoutez-lui des données.  
  
    ```tsql  
  
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
  
    ```tsql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Windows Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  Lorsque vous exécutez ce code, le message suivant s'affiche : « Le fichier « TestDB1Alter » a été modifié dans le catalogue système. Le nouveau chemin sera utilisé au prochain que démarrage de la base de données. »  
  
4.  Ensuite, mettez la base de données hors connexion.  
  
    ```tsql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  Vous devez maintenant copier les fichiers de données dans le Stockage Microsoft Azure à l'aide de l'une des méthodes suivantes : [Outil AzCopy](https://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [référence de bibliothèque cliente de stockage](https://msdn.microsoft.com/library/azure/dn261237.aspx), ou un outil Explorateur de stockage tiers.  
  
     **Important :** si vous utilisez cette amélioration, vérifiez systématiquement que vous créez un objet blob de pages et non un objet blob de blocs.  
  
6.  Ensuite, mettez la base de données en ligne.  
  
    ```tsql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **Leçon suivante :**  
  
 [Leçon 8 : Restaurer une base de données dans Stockage Microsoft Azure](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
