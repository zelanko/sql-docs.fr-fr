---
title: 'Démarrage rapide : Se connecter à et interroger SQL Server'
titleSuffix: Azure Data Studio
description: Ce guide de démarrage rapide montre comment utiliser Azure Data Studio pour se connecter à SQL Server et exécuter une requête
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
ms.openlocfilehash: 4117d8c16e96252f792e14d282d285527008874f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959393"
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>Démarrage rapide : Se connecter à et interroger SQL Server avec [!INCLUDE[name-sos](../includes/name-sos-short.md)]
Ce guide de démarrage rapide montre comment utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour se connecter à SQL Server, puis utiliser des instructions Transact-SQL (T-SQL) pour créer la base de données *TutorialDB* utilisée dans les didacticiels [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="prerequisites"></a>Conditions préalables requises

Pour effectuer ce guide de démarrage rapide, vous aurez besoin de [!INCLUDE[name-sos](../includes/name-sos-short.md)] et de l’accès à une instance de SQL Server.

- [Installez [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md).

Si vous n’avez pas accès à un serveur SQL Server, sélectionnez votre plateforme parmi les liens suivants (pensez à mémoriser votre compte de connexion et votre mot de passe SQL) :
- [Windows : Téléchargez SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)
- [macOS : Téléchargez SQL Server 2017 sur Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)
- [Linux : Téléchargez SQL Server 2017 Developer Edition](https://docs.microsoft.com/sql/linux/sql-server-linux-overview#install). Vous devez uniquement suivre les étapes pour *Créer et interroger des données*.


## <a name="connect-to-a-sql-server"></a>Se connecter à un serveur SQL Server

   
1. Démarrez **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** .
1. La première fois que vous exécutez [!INCLUDE[name-sos](../includes/name-sos-short.md)], la **page d’accueil** doit s’ouvrir. Si vous ne voyez pas la **page d’accueil**, sélectionnez **Aide** > **Bienvenue**. Sélectionnez **Nouvelle connexion** pour ouvrir le volet **Connexion** :
   
   ![Icône de nouvelle connexion](media/quickstart-sql-server/new-connection-icon.png)

1. Cet article utilise la *connexion SQL*, mais *l'authentification Windows* est prise en charge. Renseignez les champs comme suit :
 
    - **Nom du serveur** : localhost
    - **Type d'authentification :** Connexion SQL  
    - **Nom d'utilisateur :** Nom d’utilisateur pour SQL Server  
    - **Mot de passe :** Mot de passe pour SQL Server  
    - **Nom de la base de données :** laissez ce champ vide 
    - **Groupe de serveurs :** \<Par défaut\>  

   ![Écran de nouvelle connexion](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>création d'une base de données ;

La procédure suivante crée une base de données nommée **TutorialDB** :

1. Cliquez avec le bouton droit sur votre serveur, **localhost**, puis sélectionnez **Nouvelle requête**.
1. Collez l’extrait suivant dans la fenêtre de requête : 

   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
      CREATE DATABASE [TutorialDB];
   GO
   IF SERVERPROPERTY('ProductVersion') > '12'
       ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON;
   GO
   ```
1. Pour exécuter la requête, cliquez sur **Exécuter**.

Une fois la requête terminée, la nouvelle table **TutorialDB** s’affiche dans la liste des tables. Si elle n’est pas visible, cliquez avec le bouton droit sur le nœud **Bases de données** et sélectionnez **Actualiser**.


## <a name="create-a-table"></a>Créer une table

L’éditeur de requête est toujours connecté à la base de données *MASTER*, mais nous souhaitons créer une table dans la base de données *TutorialDB*. 

1. Remplacez le contexte de connexion par **TutorialDB** :

   ![Modifier le contexte](media/quickstart-sql-server/change-context.png)



1. Collez l’extrait suivant dans la fenêtre de requête, puis cliquez sur **Exécuter** :

   > [!NOTE]
   > Vous pouvez ajouter cela à ou remplacer la requête précédente dans l’éditeur. Notez que le fait de cliquer sur **Exécuter** exécute uniquement la requête qui est sélectionnée. Si rien n’est sélectionné, cliquez sur **Exécuter** pour exécuter toutes les requêtes dans l’éditeur.

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
      DROP TABLE dbo.Customers;
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
       CustomerId  int NOT NULL PRIMARY KEY, -- primary key column
       Name        nvarchar(50) NOT NULL,
       Location    nvarchar(50) NOT NULL,
       Email       nvarchar(50) NOT NULL
   );
   GO
   ```

Une fois la requête terminée, la nouvelle table **Customers** s’affiche dans la liste des tables. Vous devrez peut-être cliquer avec le bouton droit sur le nœud **TutorialDB > Tables** et sélectionner **Actualiser**.

## <a name="insert-rows"></a>Insérer des lignes

- Collez l’extrait suivant dans la fenêtre de requête, puis cliquez sur **Exécuter** :

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId], [Name], [Location], [Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```



## <a name="view-the-data-returned-by-a-query"></a>Voir les données retournées par une requête
1. Collez l’extrait suivant dans la fenêtre de requête, puis cliquez sur **Exécuter** :

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Les résultats de la requête sont affichés :

   ![Sélectionner les résultats](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous avez réussi à vous connecter à SQL Server et à exécuter une requête, essayez le [Didacticiel de l’éditeur de code](tutorial-sql-editor.md).


