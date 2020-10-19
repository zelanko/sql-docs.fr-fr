---
title: Se connecter et interroger avec Azure Synapse Analytics
description: Ce guide de démarrage rapide montre comment utiliser Azure Data Studio pour se connecter à un pool SQL dédié dans Azure Synapse Analytics et exécuter une requête.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.reviewer: alayu, maghan, sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
ms.custom: seodec18; seo-lt-2019
ms.date: 09/24/2018
ms.openlocfilehash: c2282220dff18a7f054cc5fd01b3670b6fd14d43
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92005491"
---
# <a name="quickstart-use-azure-data-studio-to-connect-and-query-data-using-dedicated-sql-pool-in-azure-synapse-analytics"></a>Démarrage rapide : Utiliser Azure Data Studio pour se connecter et interroger des données à l’aide d’un pool SQL dédié dans Azure Synapse Analytics

Ce guide de démarrage rapide montre comment utiliser Azure Data Studio pour se connecter et utiliser un pool SQL dédié dans Azure Synapse Analytics, puis utiliser des instructions Transact-SQL pour créer, insérer et sélectionner des données. 

## <a name="prerequisites"></a>Prérequis
Pour suivre ce guide démarrage rapide, vous avez besoin d’Azure Data Studio et d’un pool SQL dédié dans Azure Synapse Analytics.

- [Installez Azure Data Studio](./download-azure-data-studio.md?view=sql-server-ver15).

Si vous n’avez pas encore de pool SQL dédié, consultez [Créer un pool SQL dédié](/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision).

N’oubliez pas le nom du serveur et les informations d’identification de connexion !


## <a name="connect-to-your-dedicated-sql-pool"></a>Se connecter à votre pool SQL dédié

Utilisez Azure Data Studio pour établir une connexion à votre serveur Azure Synapse Analytics.

1. La première fois que vous exécutez Azure Data Studio, la page **Connexion** doit s’ouvrir. Si vous ne voyez pas la page **Connexion**, cliquez sur **Ajouter une connexion** ou sur l’icône **Nouvelle connexion** dans la barre latérale **SERVEURS** :
   
   ![Icône de nouvelle connexion](media/quickstart-sql-dw/new-connection-icon.png)

2. Cet article utilise la *connexion SQL*, mais *l'authentification Windows* est aussi prise en charge. Renseignez les champs comme suit en utilisant le nom du serveur, le nom d’utilisateur et le mot de passe de *votre* serveur Azure SQL :

   | Paramètre       | Valeur suggérée | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nom du serveur** | Nom complet du serveur | Le nom doit être semblable à : **sqldwsample.database.windows.net** |
   | **Authentification** | Connexion SQL| L’authentification SQL est utilisée dans ce didacticiel. |
   | **Nom d'utilisateur** | Compte d’administrateur de serveur | Il s’agit du compte que vous avez spécifié lorsque vous avez créé le serveur. |
   | **Mot de passe (connexion SQL)** | Mot de passe de votre compte d’administrateur de serveur | Il s’agit du mot de passe que vous avez spécifié lorsque vous avez créé le serveur. |
   | **Enregistrer le mot de passe ?** | Oui ou Non | Sélectionnez Oui si vous ne souhaitez pas entrer le mot de passe à chaque fois. |
   | **Nom de la base de données** | *laisser vide* | Nom de la base de données à laquelle se connecter. |
   | **Groupe de serveurs** | Sélectionnez <Default> | Si vous avez créé un groupe de serveurs, vous pouvez le définir sur un groupe de serveurs spécifique. | 

   ![Icône de nouvelle connexion](media/quickstart-sql-dw/new-connection-screen.png) 

3. Si votre serveur ne dispose pas d’une règle de pare-feu autorisant Azure Data Studio à se connecter, le formulaire **Créer une règle de pare-feu** s’ouvre. Remplissez le formulaire pour créer une nouvelle règle de pare-feu. Pour plus d’informations, consultez [Règles de pare-feu](/azure/sql-database/sql-database-firewall-configure).

   ![Nouvelle règle de pare-feu](media/quickstart-sql-dw/firewall.png)  

4. Une fois la connexion établie, votre serveur s'ouvre dans la barre latérale *Serveurs*.

## <a name="create-the-tutorial-dedicated-sql-pool"></a>Créer le pool SQL dédié du tutoriel
1. Dans l’explorateur d’objets, cliquez avec le bouton droit sur votre serveur et sélectionnez **Nouvelle requête**.

1. Collez l’extrait suivant dans l’éditeur de requête, puis cliquez sur **Exécuter** :

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

L’éditeur de requête est toujours connecté à la base de données *MASTER*, mais nous souhaitons créer une table dans la base de données *TutorialDB*. 

1. Remplacez le contexte de connexion par **TutorialDB** :

   ![Modifier le contexte](media/quickstart-sql-database/change-context.png)


1. Collez l’extrait suivant dans l’éditeur de requête, puis cliquez sur **Exécuter** :

   > [!NOTE]
   > Vous pouvez ajouter cela à ou remplacer la requête précédente dans l’éditeur. Notez que le fait de cliquer sur **Exécuter** exécute uniquement la requête qui est sélectionnée. Si rien n’est sélectionné, cliquez sur **Exécuter** pour exécuter toutes les requêtes dans l’éditeur.

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

1. Collez l’extrait suivant dans l’éditeur de requête, puis cliquez sur **Exécuter** :

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
1. Collez l’extrait suivant dans l’éditeur de requête, puis cliquez sur **Exécuter** :

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Les résultats de la requête sont affichés :

   ![Sélectionner les résultats](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>Nettoyer les ressources

D’autres Articles de cette collection reposent sur ce démarrage rapide. Si vous envisagez de continuer à travailler avec les démarrages rapides suivants, ne nettoyez pas les ressources créées dans ce démarrage rapide. Si vous n’envisagez pas de continuer, procédez comme suit pour supprimer les ressources créées par ce guide de démarrage rapide dans le portail Azure.
Nettoyez les ressources en supprimant les groupes de ressources dont vous n’avez plus besoin. Pour plus d’informations, consultez [Nettoyer les ressources](/azure/sql-database/sql-database-get-started-portal#clean-up-resources).


## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez réussi à vous connecter à Azure Synapse Analytics et à exécuter une requête, essayez le [tutoriel de l’éditeur de code](tutorial-sql-editor.md).