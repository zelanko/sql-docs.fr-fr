---
title: 'Démarrage rapide : Se connecter et interroger PostgreSQL'
titleSuffix: Azure Data Studio
description: Ce démarrage rapide montre comment utiliser Azure Data Studio pour vous connecter à PostgreSQL et exécuter une requête
ms.custom: seodec18
ms.date: 03/19/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: rachel-msft
ms.author: raagyema
manager: jroth
ms.openlocfilehash: be8683ae563e4e0676f53203cb40386cf8aa4840
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66778329"
---
# <a name="quickstart-connect-and-query-postgresql-using-includename-sosincludesname-sos-shortmd"></a>Démarrage rapide : Se connecter et interroger à l’aide de PostgreSQL [!INCLUDE[name-sos](../includes/name-sos-short.md)]
Ce démarrage rapide montre comment utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour vous connecter à Postgres et utiliser des instructions SQL pour créer la base de données *tutorialdb* et l’interroger.

## <a name="prerequisites"></a>Prérequis

Pour effectuer ce démarrage rapide, vous devez [!INCLUDE[name-sos](../includes/name-sos-short.md)], l’extension de PostgreSQL pour [ ! INCLURE[nom-sos](../includes/name-sos-short.md)et l’accès à un serveur PostgreSQL.

- [Installer [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).
- [Installer l’extension de PostgreSQL pour Azure Data Studio](postgres-extension.md).
- [Installer PostgreSQL](https://www.postgresql.org/download/). (Vous pouvez également créer une base de données Postgres dans le cloud à l’aide [postgres az des](https://docs.microsoft.com/azure/postgresql/quickstart-create-server-up-azure-cli)). 

## <a name="connect-to-postgresql"></a>Se connecter à PostgreSQL

1. Démarrer **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** .

2. La première fois que vous démarrez [!INCLUDE[name-sos](../includes/name-sos-short.md)] le **connexion** boîte de dialogue s’ouvre. Si le **connexion** boîte de dialogue ne s’ouvre, cliquez sur le **nouvelle connexion** icône dans le **serveurs** page :

   ![Nouvelle icône de connexion](media/quickstart-postgresql/new-connection-icon.png)

3. Dans le formulaire qui s’affiche, accédez à **type de connexion** et sélectionnez **PostgreSQL** à partir de la liste déroulante.


4. Renseignez les champs restants à l’aide du nom du serveur, le nom d’utilisateur et le mot de passe pour votre serveur PostgreSQL. 

   ![Nouvel écran de connexion](media/quickstart-postgresql/new-connection-screen.png)  

   | Paramètre       | Exemple de valeur | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nom du serveur** | localhost | Nom complet du serveur |
   | **Nom d'utilisateur** | Postgres | Le nom d’utilisateur pour la connexion. |
   | **Mot de passe (connexion SQL)** | *password* | Le mot de passe pour le compte que vous vous connectez à l’aide. |
   | **Mot de passe** | *Vérifier* | Cochez cette case si vous ne souhaitez pas entrer le mot de passe chaque fois que vous vous connectez. |
   | **Nom de la base de données** | \<Default\> | Renseignez ceci si vous souhaitez que la connexion pour spécifier une base de données. |
   | **Groupe de serveurs** | \<Default\> | Cette option vous permet d’affecter cette connexion à un groupe de serveurs spécifiques que vous créez. | 
   | **Nom (facultatif)** | *Laisser vide* | Cette option vous permet de spécifier un nom convivial pour votre serveur. | 

5. Sélectionnez **Se connecter**. 

Une fois connecté, votre serveur s’ouvre dans le **serveurs** encadré.


## <a name="create-a-database"></a>création d'une base de données ;

Les étapes suivantes créent une base de données nommée **tutorialdb**:

1. Avec le bouton droit sur votre serveur PostgreSQL dans le **serveurs** barre latérale et sélectionnez **nouvelle requête**.

2. Collez cette instruction SQL dans l’éditeur de requête qui s’ouvre.

   ```sql
   CREATE DATABASE tutorialdb;
   ```

3. À partir de la barre d’outils, sélectionnez **exécuter** pour exécuter la requête. Les notifications s’affichent dans le **MESSAGES** volet pour afficher la progression de la requête.

>[!TIP]
> Vous pouvez utiliser **F5** sur votre clavier pour exécuter l’instruction au lieu d’utiliser **exécuter**.

Une fois la requête terminée, cliquez sur **bases de données** et sélectionnez **Actualiser** pour voir **tutorialdb** dans la liste sous le **bases de données** nœud .


## <a name="create-a-table"></a>Créer une table

 Les étapes suivantes créent une table dans le **tutorialdb**:

1. Modifier le contexte de connexion au **tutorialdb** à l’aide de la liste déroulante dans l’éditeur de requête. 

   ![Changer de contexte](media/quickstart-postgresql/change-context.png)

2. Collez l’instruction SQL suivante dans l’éditeur de requête et cliquez sur **exécuter**. 

   > [!NOTE]
   > Vous pouvez l’ajouter ou remplacer la requête existante dans l’éditeur. En cliquant sur **exécuter** exécute uniquement la requête qui est mis en surbrillance. Si rien n’est mis en surbrillance, en cliquant sur **exécuter** exécute toutes les requêtes dans l’éditeur.

   ```sql
   -- Drop the table if it already exists
   DROP TABLE IF EXISTS customers;
   -- Create a new table called 'customers'
   CREATE TABLE customers(
       customer_id SERIAL PRIMARY KEY,
       name VARCHAR (50) NOT NULL,
       location VARCHAR (50) NOT NULL,
       email VARCHAR (50) NOT NULL
   );
   ```

## <a name="insert-rows"></a>Insérer des lignes

Collez l’extrait de code suivant dans la fenêtre de requête et cliquez sur **exécuter**:

   ```sql
   -- Insert rows into table 'customers'
   INSERT INTO customers
       (customer_id, name, location, email)
    VALUES
      ( 1, 'Orlando', 'Australia', ''),
      ( 2, 'Keith', 'India', 'keith0@adventure-works.com'),
      ( 3, 'Donna', 'Germany', 'donna0@adventure-works.com'),
      ( 4, 'Janet', 'United States','janet1@adventure-works.com');
   ```

## <a name="query-the-data"></a>Interroger les données

1. Collez l’extrait de code suivant dans l’éditeur de requête et cliquez sur **exécuter**:
   
   ```sql
   -- Select rows from table 'customers'
   SELECT * FROM customers; 
   ```

2. Les résultats de la requête sont affichés :

   ![Afficher les résultats](media/quickstart-postgresql/view-results.png)

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur la [scénarios disponibles pour Postgres dans Azure Data Studio](postgres-extension.md). 