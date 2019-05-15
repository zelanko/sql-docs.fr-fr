---
title: 'Démarrage rapide : Se connecter et interroger une base de données SQL Azure'
titleSuffix: Azure Data Studio
description: Ce démarrage rapide montre comment utiliser Azure Data Studio pour vous connecter à une base de données SQL et exécuter une requête
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: a961cd08baab13b87241492df4adef52d5846daf
ms.sourcegitcommit: 553ecea0427e4d2118ea1ee810f4a73275b40741
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65620360"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>Démarrage rapide : Utilisez [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour vous connecter et interroger la base de données SQL Azure

Dans ce démarrage rapide, vous allez utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour vous connecter à un serveur de base de données SQL Azure. Vous allez ensuite exécuter des instructions Transact-SQL (T-SQL) pour créer et interroger la base de données TutorialDB, qui est utilisé dans d’autres [!INCLUDE[name-sos](../includes/name-sos-short.md)] didacticiels.

## <a name="prerequisites"></a>Prérequis

Pour effectuer ce démarrage rapide, vous devez [!INCLUDE[name-sos](../includes/name-sos-short.md)]et un serveur de base de données SQL Azure.

- [Installer [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)

Si vous n’avez pas un serveur SQL Azure, effectuez l’une des Démarrages rapides suivants de la base de données SQL Azure. N’oubliez pas le nom complet du serveur et connectez-vous aux informations d’identification pour les étapes ultérieures :

- [Créer une base de données - portail](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [Créer de base de données - CLI](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [Créer une base de données - PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Se connecter à votre serveur de base de données SQL Azure

Utilisez [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour établir une connexion à votre serveur de base de données SQL Azure.

1. La première fois que vous exécutez [!INCLUDE[name-sos](../includes/name-sos-short.md)] le **Bienvenue** page doit s’ouvrir. Si vous ne voyez pas le **Bienvenue** page, sélectionnez **aide** > **Bienvenue**. Sélectionnez **nouvelle connexion** pour ouvrir le **connexion** volet :
   
   ![Nouvelle icône de connexion](media/quickstart-sql-database/new-connection-icon.png)

2. Cet article utilise l’authentification dans SQL, mais prend également en charge l’authentification Windows. Renseignez les champs suivants à l’aide du nom du serveur, le nom d’utilisateur et le mot de passe pour votre serveur SQL Azure :

   | Paramètre       | Valeur suggérée |  Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nom du serveur** | Nom complet du serveur | Quelque chose comme : **nomserveur.basededonnées.Windows.NET**. |
   | **Authentification** | Connexion SQL| Ce didacticiel utilise l’authentification SQL. |
   | **Nom d'utilisateur** | Le nom du compte utilisateur de serveur admin | Le nom d’utilisateur du compte utilisé pour créer le serveur. |
   | **Mot de passe (connexion SQL)** | Le mot de passe du compte administrateur serveur | Le mot de passe du compte utilisé pour créer le serveur. |
   | **Enregistrer le mot de passe ?** | Oui ou Non | Sélectionnez **Oui** si vous ne souhaitez pas entrer le mot de passe chaque fois. |
   | **Nom de la base de données** | *Laisser vide* | Vous vous connectez uniquement au serveur ici. |
   | **Groupe de serveurs** | Sélectionnez <Default> | Vous pouvez définir ce champ à un groupe de serveurs spécifiques que vous avez créé. | 

   ![Nouvelle icône de connexion](media/quickstart-sql-database/new-connection-screen.png)  

3. Sélectionnez **Se connecter**.

4. Si votre serveur n’a pas une règle de pare-feu autorisant Azure Data Studio pour vous connecter, le **créer une nouvelle règle de pare-feu** s’ouvre. Remplissez le formulaire pour créer une nouvelle règle de pare-feu. Pour plus d’informations, consultez [règles de pare-feu](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Nouvelle règle de pare-feu](media/quickstart-sql-database/firewall.png)  

Une fois connecté, votre serveur s’ouvre dans le **serveurs** encadré.

## <a name="create-the-tutorial-database"></a>Créer la base de données de didacticiel

Les sections suivantes créent la base de données TutorialDB utilisé dans d’autres [!INCLUDE[name-sos](../includes/name-sos-short.md)] didacticiels.

1. Avec le bouton droit sur votre serveur SQL Azure dans le **serveurs** barre latérale et sélectionnez **nouvelle requête**.

1. Collez cette SQL dans l’éditeur de requête.

   ```sql
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO

   ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
   GO
   ```

1. Dans la barre d’outils, sélectionnez **exécuter**. Les notifications s’affichent dans le **MESSAGES** volet affichant la progression de la requête.

## <a name="create-a-table"></a>Créer une table

L’éditeur de requête est connecté à la **master** base de données, mais nous voulons créer une table dans le **TutorialDB** base de données. 

1. Se connecter à la **TutorialDB** base de données.

   ![Changer de contexte](media/quickstart-sql-database/change-context2.png)



1. Créer un `Customers` table. 

   Remplacez la requête précédente dans l’éditeur de requête avec celle-ci, puis sélectionnez **exécuter**.

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


## <a name="insert-rows-into-the-table"></a>Insérer des lignes dans la table

Remplacez la requête précédente par celle-ci et sélectionnez **exécuter**.

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

## <a name="view-the-result"></a>Afficher le résultat

Remplacez la requête précédente par celle-ci et sélectionnez **exécuter**.

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

Affichent les résultats de la requête :

   ![Sélectionnez les résultats](media/quickstart-sql-database/select-results2.png)


## <a name="clean-up-resources"></a>Nettoyer les ressources

Les articles de démarrage rapide suivants reposent sur les ressources créées ici. Si vous prévoyez de travailler via ces articles, être ne pas voulez-vous vraiment supprimer ces ressources. Sinon, dans le portail Azure, vous devez supprimer les ressources que vous n’avez plus besoin. Pour plus d’informations, consultez [nettoyer les ressources](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez correctement connecté à une base de données SQL Azure et l’exécuter une requête, essayez le [didacticiel de l’éditeur de Code](tutorial-sql-editor.md).
