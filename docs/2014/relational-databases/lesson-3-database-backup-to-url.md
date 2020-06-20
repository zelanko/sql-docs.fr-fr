---
title: 'Leçon 4 : créer une base de données dans le stockage Azure | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3e95616b2b001dff4b2d375800fe4bbaf315a214
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025121"
---
# <a name="lesson-4-create-a-database-in-azure-storage"></a>Leçon 4 : Créer une base de données dans Stockage Azure
  Dans cette leçon, vous allez apprendre à créer une base de données à l’aide de la fonctionnalité fichiers de données SQL Server dans Azure. Notez que vous devez avoir terminé les leçons 1, 2 et 3 avant d'effectuer les tâches de cette leçon. La leçon 3 est une étape très importante, car vous devez stocker les informations relatives à votre conteneur de stockage Azure, ainsi que le nom de la stratégie et la clé SAS qui lui sont associés dans le magasin d’informations d’identification SQL Server avant la leçon 4.  
  
 Pour chaque conteneur de stockage utilisé par un fichier de données ou un fichier journal, vous devez créer des informations d'identification SQL Server dont le nom correspond au chemin d'accès du conteneur. Ensuite, vous pouvez créer une nouvelle base de données dans le stockage Azure.  
  
 Cette leçon suppose que vous avez déjà effectué les étapes suivantes :  
  
-   Vous avez un compte de stockage Azure.  
  
-   Vous avez créé un conteneur sous votre compte de stockage Azure.  
  
-   Vous avez créé une stratégie sur un conteneur avec des droits en lecture, écriture et création de liste. Vous avez également généré une clé SAS.  
  
-   Vous avez créé des informations d'identification SQL Server sur l'ordinateur source.  
  
 Pour créer une base de données dans Azure à l’aide de la fonctionnalité fichiers de données SQL Server dans stockage Azure, procédez comme suit :  
  
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
  
6.  De même, pour afficher la base de données nouvellement créée dans votre compte de stockage, connectez-vous à votre compte de stockage via SQL Server Management Studio (SSMS). Pour plus d’informations sur la façon de se connecter à un stockage Azure à l’aide de SQL Server Management Studio, procédez comme suit :  
  
    1.  Tout d'abord, obtenez les informations sur le compte de stockage. Connectez-vous au Portail de gestion. Cliquez ensuite sur **stockage** et choisissez votre compte de stockage. Quand un compte de stockage est sélectionné, cliquez sur **gérer les clés d’accès** au bas de la page. Cela permet d'ouvrir une fenêtre de dialogue similaire :  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")  
  
    2.  Copiez les valeurs **nom du compte de stockage** et clé d' **accès primaire** dans la fenêtre de dialogue **connexion au stockage Azure** dans SSMS. Cliquez ensuite sur **Connecter**. Les informations sur les conteneurs du compte de stockage s'affichent dans SSMS, comme illustré dans la capture d'écran suivante :  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")  
  
 La capture d’écran suivante illustre la nouvelle base de données créée à la fois dans l’environnement de stockage local et Azure.  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")  
  
 **Remarque :** S’il existe des références actives aux fichiers de données dans un conteneur, toute tentative de suppression des informations d’identification de SQL Server associées échoue. De même, s'il existe déjà un bail sur un fichier de base de données spécifique d'un objet blob et que vous voulez le supprimer, vous devez d'abord résilier le bail sur l'objet blob. Pour rompre le bail, vous pouvez utiliser un [objet blob de bail](https://msdn.microsoft.com/library/azure/ee691972.aspx).  
  
 Grâce à cette nouvelle fonctionnalité, configurez SQL Server afin que les instructions CREATE DATABASE créent par défaut une base de données activée pour le cloud. En d’autres termes, vous pouvez définir des emplacements de données et de journaux par défaut dans les propriétés de SQL Server Management Studio instance de serveur. ainsi, chaque fois que vous créez une base de données, tous les fichiers de base de données (. mdf,. ldf) sont créés en tant qu’objets BLOB de pages dans le stockage Azure.  
  
 Pour créer une base de données dans Azure Storage à l’aide de SQL Server Management Studio interface utilisateur, procédez comme suit :  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du moteur de base de données SQL Server et développez-la.  
  
2.  Cliquez avec le bouton droit sur Bases de données, puis cliquez sur Nouvelle base de données.  
  
3.  Dans la boîte de dialogue Nouvelle base de données, tapez un nom de base de données.  
  
4.  Modifiez les valeurs par défaut des données primaires et des fichiers journaux de transactions, dans la grille Fichiers de la base de données, cliquez sur la cellule appropriée, puis entrez la nouvelle valeur. Spécifiez également le chemin d'accès de l'emplacement du fichier. Pour le chemin d'accès, tapez le chemin d'accès de l'URL du conteneur de stockage, notamment `https://teststorageaccnt.blob.core.windows.net/testcontainer/`. Pour le nom de fichier, entrez les noms de fichiers physique des fichiers de base de données (.mdf, .ldf).  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")  
  
     Pour plus d’informations, consultez [Ajouter des fichiers de données ou journaux à une base de données](databases/add-data-or-log-files-to-a-database.md).  
  
5.  Conservez toutes les autres valeurs par défaut.  
  
6.  Cliquez sur OK.  
  
 Pour afficher la nouvelle base de données TestDB1 sur votre serveur SQL Server local, actualisez les bases de données dans l'Explorateur d'objets. De même, pour afficher la base de données nouvellement créée dans votre compte de stockage, connectez-vous à votre compte de stockage via SQL Server Management Studio (SSMS), comme expliqué précédemment dans cette leçon.  
  
 **Leçon suivante :**  
  
 [Leçon 5. &#40;facultatif&#41; chiffrer votre base de données à l’aide de TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  
