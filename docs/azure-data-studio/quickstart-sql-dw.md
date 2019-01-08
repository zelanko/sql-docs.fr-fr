---
title: 'Démarrage rapide : Se connecter et interroger un entrepôt de données SQL Azure'
titleSuffix: Azure Data Studio
description: Ce démarrage rapide montre comment utiliser Azure Data Studio pour vous connecter à un entrepôt de données SQL Azure et exécuter une requête
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 72e7e0e83757b52ba7fba6a24cc91499ca4863b1
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030753"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>Démarrage rapide : Utilisez [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour vous connecter et interroger des données dans Azure SQL Data Warehouse

Ce démarrage rapide montre comment utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour vous connecter à Azure SQL data warehouse, puis utiliser les instructions Transact-SQL pour créer, insérer et sélectionner des données. 

## <a name="prerequisites"></a>Configuration requise
Pour effectuer ce démarrage rapide, vous devez [!INCLUDE[name-sos](../includes/name-sos-short.md)]et un entrepôt de données SQL Azure.

- [Installer [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Si vous ne disposez pas d’un entrepôt de données SQL, consultez [créer un entrepôt de données SQL](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision).

N’oubliez pas le nom du serveur et les informations d’identification de connexion !


## <a name="connect-to-your-data-warehouse"></a>Se connecter à votre entrepôt de données

Utilisez [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour établir une connexion à votre serveur Azure SQL Data Warehouse.

1. La première fois que vous exécutez [!INCLUDE[name-sos](../includes/name-sos-short.md)] le **connexion** page doit s’ouvrir. Si vous ne voyez pas le **connexion** , cliquez sur **ajouter une connexion**, ou le **nouvelle connexion** icône dans le **serveurs** encadré :
   
   ![Nouvelle icône de connexion](media/quickstart-sql-dw/new-connection-icon.png)

2. Cet article utilise *connexion SQL*, mais *l’authentification Windows* est également pris en charge. Renseignez les champs comme suit à l’aide du nom du serveur, le nom d’utilisateur et le mot de passe *votre* serveur SQL Azure :

   | Paramètre       | Valeur suggérée |  Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nom du serveur** | Nom complet du serveur | Le nom doit être quelque chose comme ceci : **sqldwsample.database.windows.net** |
   | **Authentification** | Connexion SQL| L’authentification SQL est utilisée dans ce didacticiel. |
   | **Nom d'utilisateur** | Compte Administrateur du serveur | Il s’agit du compte que vous avez spécifié quand vous avez créé le serveur. |
   | **Mot de passe (connexion SQL)** | Mot de passe de votre compte d’administrateur de serveur | Il s’agit du mot de passe que vous avez spécifié quand vous avez créé le serveur. |
   | **Enregistrer le mot de passe** | Oui ou Non | Sélectionnez Oui si vous ne souhaitez pas entrer le mot de passe chaque fois. |
   | **Nom de la base de données** | *Laisser vide* | Nom de la base de données avec laquelle établir une connexion. |
   | **Groupe de serveurs** | Sélectionnez <Default> | Si vous avez créé un groupe de serveurs, vous pouvez définir pour un groupe de serveurs spécifiques. | 

   ![Nouvelle icône de connexion](media/quickstart-sql-dw/new-connection-screen.png) 

3. Si votre serveur n’a pas une règle de pare-feu autorisant Azure Data Studio pour vous connecter, le **créer une nouvelle règle de pare-feu** s’ouvre. Remplissez le formulaire pour créer une nouvelle règle de pare-feu. Pour plus d’informations, consultez [règles de pare-feu](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Nouvelle règle de pare-feu](media/quickstart-sql-dw/firewall.png)  

4. Une fois connecté sur votre serveur s’ouvre dans le *serveurs* encadré.

## <a name="create-the-tutorial-data-warehouse"></a>Créer l’entrepôt de données du didacticiel
1. Cliquez avec le bouton droit sur votre serveur, dans l’Explorateur d’objets et sélectionnez **nouvelle requête.**

1. Collez l’extrait de code suivant dans l’éditeur de requête et cliquez sur **exécuter**:

   ```sql
    IF NOT EXISTS (
       SELECT name
       FROM sys.databases
       WHERE name = N'TutorialDB'
    )
    CREATE DATABASE [TutorialDB] (EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');
    GO  
    
    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
   ```


## <a name="create-a-table"></a>Créer une table

L’éditeur de requête est toujours connecté à la *master* base de données, mais nous voulons créer une table dans le *TutorialDB* base de données. 

1. Modifier le contexte de connexion au **TutorialDB**:

   ![Changer de contexte](media/quickstart-sql-database/change-context.png)


1. Collez l’extrait de code suivant dans l’éditeur de requête et cliquez sur **exécuter**:

   > [!NOTE]
   > Vous pouvez l’ajouter à ou remplacer la requête précédente dans l’éditeur. Notez qu’un clic sur **exécuter** exécute uniquement la requête sélectionnée. Si rien n’est sélectionné, un clic sur **exécuter** exécute toutes les requêtes dans l’éditeur.

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT     NOT NULL,
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows"></a>Insérer des lignes

1. Collez l’extrait de code suivant dans l’éditeur de requête et cliquez sur **exécuter**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```


## <a name="view-the-result"></a>Afficher le résultat
1. Collez l’extrait de code suivant dans l’éditeur de requête et cliquez sur **exécuter**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Les résultats de la requête sont affichés :

   ![Sélectionnez les résultats](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>Nettoyer les ressources

Autres articles de cette collection reposent sur ce démarrage rapide. Si vous envisagez de continuer à utiliser d’autres Démarrages rapides, ne nettoyez pas les ressources créées dans ce démarrage rapide. Si vous ne souhaitez pas continuer, procédez comme suit pour supprimer les ressources créées par ce démarrage rapide dans le portail Azure.
Nettoyer les ressources en supprimant les groupes de ressources que vous n’avez plus besoin. Pour plus d’informations, consultez [nettoyer les ressources](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).


## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous êtes connecté à un entrepôt de données SQL Azure et que vous avez exécuté une requête, essayez le [didacticiel de l’éditeur de Code](tutorial-sql-editor.md).
