---
Title: 'Tutorial: Connect and Query SQL Server using SQL Server Management Studio'
description: Tutoriel pour la connexion à SQL Server à l’aide de SQL Server Management Studio et l’exécution de requêtes T-SQL de base.
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
ms.openlocfilehash: 7b389c5b58dc0afde077f70e2fd8bec7c6cac4d0
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2018
---
# <a name="tutorial-connect-and-query-sql-server-using-sql-server-management-studio"></a>Tutoriel : Se connecter à SQL Server et l’interroger à l’aide de SQL Server Management Studio
Ce tutoriel vous apprend à utiliser SSMS (SQL Server Management Studio) pour vous connecter à votre instance de SQL Server, puis exécuter quelques commandes T-SQL (Transact-SQL) de base. Cet article explique comment effectuer les opérations suivantes :
    - [Se connecter à un serveur SQL Server](#connect-to-a-sql-server)
    - [Créer une base de données (**TutorialDB**)](#create-a-database)
    - [Créer une table (**Customers**) dans votre nouvelle base de données](#create-a-table)
    - [Insérer des lignes dans votre nouvelle table **Customers**](#insert-rows)
    - [Interroger la table **Customers** et afficher les résultats](#view-query-results)
    - [Utiliser la table de fenêtre de requête pour vérifier les propriétés de votre connexion](#verify-your-query-window-connection-properties)
    - [Changer le serveur auquel votre fenêtre de requête est connectée](#change-server-connection-within-query-window)


## <a name="prerequisites"></a>Prerequisites
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio et de l’accès à un serveur SQL Server. 

- Installez [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).

Si vous n’avez pas accès à un serveur SQL Server, sélectionnez votre plateforme parmi les liens suivants (pensez à mémoriser votre compte de connexion et votre mot de passe SQL si vous choisissez l’authentification SQL) :
- [Windows : Téléchargez SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS : Téléchargez SQL Server 2017 sur Docker](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker)


## <a name="connect-to-a-sql-server"></a>Se connecter à un serveur SQL Server

1. Démarrez SSMS (SQL Server Management Studio).
1. La première fois que vous exécutez SSMS, la boîte de dialogue **Se connecter au serveur** s’ouvre. 
      - Si la boîte de dialogue **Se connecter au serveur** ne s’ouvre pas, vous pouvez l’ouvrir manuellement dans **l’Explorateur d’objets** > **Se connecter** (ou l’icône située à côté) > **Moteur de base de données**.

        ![Se connecter dans l’Explorateur d’objets](media/connect-query-sql-server/connectobjexp.png)

1. Dans la boîte de dialogue **Se connecter au serveur**, indiquez les options de connexion : 

    - **Type de serveur** : moteur de base de données (en général, il est sélectionné par défaut)
    - **Authentification** : l’authentification Windows (cet article utilise l’authentification Windows, mais le compte de connexion SQL est pris en charge et vous demande un nom d’utilisateur / mot de passe si vous le sélectionnez)

      ![Connexion](media/connect-query-sql-server/connection.png)

        Vous pouvez également modifier des options de connexion supplémentaires (par exemple, la base de données à laquelle vous vous connectez, la valeur de délai d’attente de connexion et le protocole réseau) en cliquant sur le bouton **Options**. Dans le cadre de cet article, tous les éléments conservent les valeurs par défaut. 

1. Une fois que les champs ont été renseignés, cliquez sur **Se connecter**. 

1. Vous pouvez vérifier que votre connexion au serveur SQL Server a réussi en examinant les objets de **l’Explorateur d’objets** : 

   ![Connexion réussie](media/connect-query-sql-server/successfulconnection.png)


## <a name="create-a-database"></a>Créer une base de données
La procédure suivante crée une base de données nommée TutorialDB. 

1. Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur votre serveur et sélectionnez **Nouvelle requête** :

   ![Nouvelle requête](media/connect-query-sql-server/newquery.png)
   
1. Collez l’extrait de code T-SQL suivant dans la fenêtre de requête : 
   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO
   ```
2. Pour exécuter la requête, cliquez sur **Exécuter** (ou appuyez sur la touche F5 de votre clavier). 

   ![Exécuter la requête](media/connect-query-sql-server/execute.png)
  
 
Une fois la requête terminée, la nouvelle base de données **TutorialDB** s’affiche dans la liste des bases de données de **l’Explorateur d’objets**. Si elle n’est pas visible, cliquez avec le bouton droit sur le nœud Bases de données et sélectionnez **Actualiser**.  


## <a name="create-a-table"></a>Créer une table
La procédure suivante va maintenant créer une table dans la base de données **TutorialDB** nouvellement créée. Toutefois, l’éditeur de requête est toujours dans le contexte de la base de données *master* et vous voulez créer une table dans la base de données *TutorialDB*. 

1. Remplacez le contexte de connexion de votre requête de base de données master par **TutorialDB** en sélectionnant la base de données dans la liste déroulante des bases de données. 

   ![Changer la base de données](media/connect-query-sql-server/changedb.png)

1. Collez l’extrait de code T-SQL suivant dans la fenêtre de requête, sélectionnez-le et cliquez sur **Exécuter** (ou appuyez sur la touche F5 de votre clavier) : 
    - Vous pouvez remplacer le texte existant dans la fenêtre de requête ou l’ajouter à la fin. Si vous souhaitez exécuter tous les éléments dans la fenêtre de requête, cliquez sur **Exécuter**. Si vous souhaitez exécuter une partie du texte, sélectionnez-la et cliquez sur **Exécuter**.  
  
   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```
Une fois la requête terminée, la nouvelle table **Customers** s’affiche dans la liste des tables de **l’Explorateur d’objets**. Si la table n’est pas visible, cliquez avec le bouton droit sur le nœud **TutorialDB > Tables** dans **l’Explorateur d’objets** et sélectionnez **Actualiser**.

## <a name="insert-rows"></a>Insérer des lignes
L’étape suivante insère des lignes dans la table **Customers** qui a été créée précédemment. 

Collez l’extrait de code T-SQL suivant dans la fenêtre de requête, puis cliquez sur **Exécuter** : 


   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```

## <a name="view-query-results"></a>Afficher les résultats de requête
Les résultats d’une requête sont visibles en dessous de la fenêtre du texte de requête. Les étapes ci-dessous vous permettent d’interroger la table **Customers** et d’afficher les lignes qui ont été précédemment insérées.  

1. Collez l’extrait de code T-SQL suivant dans la fenêtre de requête, puis cliquez sur **Exécuter** : 

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```
1. Les résultats de la requête sont affichés sous la zone dans laquelle le texte a été entré : 

   ![Résultats de requête](media/connect-query-sql-server/queryresults.png)


1.  Vous pouvez modifier le mode de présentation des résultats en sélectionnant l’une des options suivantes :

     ![résultats](media/connect-query-sql-server/results.png)

    - Par défaut, les résultats s’affichent en **mode grille**, ce qui correspond au bouton central et affiche les résultats dans une table. 
    - Le premier bouton affiche les résultats en **mode texte**, comme illustré dans l’image de la section suivante.
    - Le troisième bouton vous permet d’enregistrer les résultats dans un fichier, un fichier se terminant par *.rpt par défaut.

## <a name="verify-your-query-window-connection-properties"></a>Vérifier les propriétés de votre connexion dans la fenêtre de requête
Des informations sur les propriétés de connexion figurent sous les résultats de votre requête. 
- Après avoir exécuté la requête citée plus haut dans l’étape précédente, passez en revue les propriétés de connexion au bas de la fenêtre de requête.
    - Vous pouvez identifier le serveur et la base de données auxquels vous êtes connecté ainsi que l’utilisateur sous le nom duquel vous êtes connecté.
    - Vous pouvez également voir la durée de la requête et le nombre de lignes retournées par la requête exécutée précédemment.
    
    ![Propriétés de connexion](media/connect-query-sql-server/connectionproperties.png)  
    Dans cette image, les résultats sont affichés en **mode texte**.  

## <a name="change-server-connection-within-query-window"></a>Changer la connexion serveur dans la fenêtre de requête
Vous pouvez changer le serveur auquel la fenêtre de requête actuelle est connectée en suivant les étapes ci-dessous.
1. Cliquez avec le bouton droit dans la fenêtre de requête > Connexion > Modifier la connexion.
2. La boîte de dialogue **Se connecter au serveur** s’ouvre à nouveau, ce qui vous permet de modifier le serveur auquel votre requête est connectée. 
 
   ![Modifier la connexion](media/connect-query-sql-server/changeconnection.png)
   - Notez que cela ne modifie pas le serveur auquel votre **Explorateur d’objets** est connecté, simplement la fenêtre de requête actuelle. 



