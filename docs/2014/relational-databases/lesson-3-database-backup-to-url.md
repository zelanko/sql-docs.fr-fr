---
title: 'Leçon 4 : Créer une base de données dans le stockage Windows Azure | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7361cb5d0e68cfa3f45f46d7f99d68c88c1a556b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66090819"
---
# <a name="lesson-4-create-a-database-in-windows-azure-storage"></a>Leçon 4 : Créer une base de données dans Stockage Microsoft Azure
  Dans cette leçon, vous allez apprendre comment créer une base de données à l'aide de la fonctionnalité Fichiers de données SQL Server dans Microsoft Azure. Notez que vous devez avoir terminé les leçons 1, 2 et 3 avant d'effectuer les tâches de cette leçon. La leçon 3 est une étape très importante, car vous devez supprimer les informations sur votre conteneur de stockage Windows Azure et le nom de stratégie associée, ainsi que la clé SAS dans le magasin d'informations d'identification SQL Server avant de passer à la leçon 4.  
  
 Pour chaque conteneur de stockage utilisé par un fichier de données ou un fichier journal, vous devez créer des informations d'identification SQL Server dont le nom correspond au chemin d'accès du conteneur. Ensuite, créez une base de données dans le Stockage Microsoft Azure.  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous disposez d'un compte Microsoft Azure Storage.  
  
-   Vous avez créé un conteneur sous votre compte Microsoft Azure Storage.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé des informations d'identification SQL Server sur l'ordinateur source.  
  
 Pour créer une base de données dans Windows Azure à l'aide de la fonctionnalité Fichiers de données SQL Server dans le Stockage Microsoft Azure, procédez comme suit :  
  
1.  Connectez-vous à SQL Server Management Studio.  
  
2.  Dans l'Explorateur d'objets, connectez-vous à l'instance du moteur de base de données installée.  
  
3.  Dans la barre d'outils standard, cliquez sur Nouvelle requête.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête et modifiez-le si nécessaire. Notez que le champ FILENAME fait référence au chemin d'accès d'URI de la base de données dans le conteneur de stockage et doit commencer par https.  
  
    ```  
  
    --Create a database that uses a SQL Server credential    
    CREATE DATABASE TestDB1    
    ON   
    (NAME = TestDB1_data,   
       FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf')   
     LOG ON   
    (NAME = TestDB1_log,   
        FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
    GO  
  
    ```  
  
     Ajoutez des données à votre base de données.  
  
    ```  
  
    USE TestDB1;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
5.  Pour afficher la nouvelle base de données TestDB1 sur votre serveur SQL Server local, actualisez les bases de données dans l'Explorateur d'objets.  
  
6.  De même, pour afficher la base de données nouvellement créée dans votre compte de stockage, connectez-vous à votre compte de stockage via SQL Server Management Studio (SSMS). Pour plus d'informations sur la façon de se connecter à un stockage Windows Azure à l'aide de SQL Server Management Studio, suivez ces étapes :  
  
    1.  Tout d'abord, obtenez les informations sur le compte de stockage. Connectez-vous au Portail de gestion. Ensuite, cliquez sur **stockage** et sélectionnez votre compte de stockage. Lorsqu’un compte de stockage est sélectionné, cliquez sur **gérer les clés d’accès** en bas de la page. Cela permet d'ouvrir une fenêtre de dialogue similaire :  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")  
  
    2.  Copie le **nom de compte de stockage** et **clé d’accès primaire** valeurs à la **se connecter à Windows Azure Storage** fenêtre de boîte de dialogue dans SSMS. Ensuite, cliquez sur **Connect**. Les informations sur les conteneurs du compte de stockage s'affichent dans SSMS, comme illustré dans la capture d'écran suivante :  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")  
  
 La capture d'écran suivante illustre la base de données nouvellement créée localement et dans l'environnement de Stockage Microsoft Azure.  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")  
  
 **Remarque :** S’il existe des références actives aux fichiers de données dans un conteneur, toute tentative pour supprimer les informations d’identification SQL Server associée échoue. De même, s'il existe déjà un bail sur un fichier de base de données spécifique d'un objet blob et que vous voulez le supprimer, vous devez d'abord résilier le bail sur l'objet blob. Pour interrompre le bail, vous pouvez utiliser [Lease Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx).  
  
 Grâce à cette nouvelle fonctionnalité, configurez SQL Server afin que les instructions CREATE DATABASE créent par défaut une base de données activée pour le cloud. En d'autres termes, définissez des données par défaut et consignez des emplacements dans les propriétés de l'instance SQL Server Management Studio de façon à ce que lorsque vous créez une base de données, tous les fichiers de base de données (.mdf, .ldf) soient créés en tant qu'objets blob de page dans le Stockage Microsoft Azure.  
  
 Pour créer une base de données dans le Stockage Microsoft Azure à l'aide de l'interface utilisateur de SQL Server Management Studio, procédez comme suit :  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du moteur de base de données SQL Server et développez-la.  
  
2.  Cliquez avec le bouton droit sur Bases de données, puis cliquez sur Nouvelle base de données.  
  
3.  Dans la boîte de dialogue Nouvelle base de données, tapez un nom de base de données.  
  
4.  Modifiez les valeurs par défaut des données primaires et des fichiers journaux de transactions, dans la grille Fichiers de la base de données, cliquez sur la cellule appropriée, puis entrez la nouvelle valeur. Spécifiez également le chemin d'accès de l'emplacement du fichier. Pour le chemin d'accès, tapez le chemin d'accès de l'URL du conteneur de stockage, notamment `https://teststorageaccnt.blob.core.windows.net/testcontainer/`. Pour le nom de fichier, entrez les noms de fichiers physique des fichiers de base de données (.mdf, .ldf).  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")  
  
     Pour plus d’informations, consultez [Ajouter des fichiers de données ou journaux à une base de données](databases/add-data-or-log-files-to-a-database.md).  
  
5.  Conservez toutes les autres valeurs par défaut.  
  
6.  Cliquez sur OK.  
  
 Pour afficher la nouvelle base de données TestDB1 sur votre serveur SQL Server local, actualisez les bases de données dans l'Explorateur d'objets. De même, pour afficher la base de données nouvellement créée dans votre compte de stockage, connectez-vous à votre compte de stockage via SQL Server Management Studio (SSMS), comme expliqué précédemment dans cette leçon.  
  
 **Leçon suivante :**  
  
 [Leçon 5. &#40;Facultatif&#41; chiffrer votre base de données à l’aide du chiffrement transparent des données](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  
