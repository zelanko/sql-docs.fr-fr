---
title: Se connecter à et interroger Azure Data Warehouse
titleSuffix: Azure Data Studio
description: Ce guide de démarrage rapide montre comment utiliser Azure Data Studio pour se connecter à Azure SQL Data Warehouse et exécuter une requête
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
ms.custom: seodec18; seo-lt-2019
ms.date: 09/24/2018
ms.openlocfilehash: f07d13bc9110b5b9ec96aa17169687f471aeb197
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74957106"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>Démarrage rapide : Utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour vous connecter et interroger des données dans Azure SQL Data Warehouse

Ce guide de démarrage rapide montre comment utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour se connecter à Azure SQL Data Warehouse, puis utiliser des instructions Transact-SQL pour créer, insérer et sélectionner des données. 

## <a name="prerequisites"></a>Conditions préalables requises
Pour suivre ce guide de démarrage rapide, vous aurez besoin de [!INCLUDE[name-sos](../includes/name-sos-short.md)] et d’une instance Azure SQL Data Warehouse.

- [Installez [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md).

Si vous ne disposez pas déjà d’un entrepôt de données SQL, consultez [Créer un entrepôt de données SQL](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision).

N’oubliez pas le nom du serveur et les informations d’identification de connexion !


## <a name="connect-to-your-data-warehouse"></a>Connexion à votre entrepôt de données

Utilisez [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour établir une connexion à votre serveur Azure SQL Data Warehouse.

1. La première fois que vous exécutez [!INCLUDE[name-sos](../includes/name-sos-short.md)], la page **Connexion** doit s’ouvrir. Si vous ne voyez pas la page **Connexion**, cliquez sur **Ajouter une connexion** ou sur l’icône **Nouvelle connexion** dans la barre latérale **SERVEURS** :
   
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

3. Si votre serveur ne dispose pas d’une règle de pare-feu autorisant Azure Data Studio à se connecter, le formulaire **Créer une règle de pare-feu** s’ouvre. Remplissez le formulaire pour créer une nouvelle règle de pare-feu. Pour plus d’informations, consultez [Règles de pare-feu](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Nouvelle règle de pare-feu](media/quickstart-sql-dw/firewall.png)  

4. Une fois la connexion établie, votre serveur s'ouvre dans la barre latérale *Serveurs*.

## <a name="create-the-tutorial-data-warehouse"></a>Créer l’entrepôt de données du didacticiel
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
Nettoyez les ressources en supprimant les groupes de ressources dont vous n’avez plus besoin. Pour plus d’informations, consultez [Nettoyer les ressources](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).


## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez réussi à vous connecter à un entrepôt de données Azure SQL et à exécuter une requête, essayez le [Didacticiel de l’éditeur de code](tutorial-sql-editor.md).
