---
title: "Didacticiel : Utiliser l’éditeur SQL opérations Studio (version préliminaire) Transact-SQL pour créer des objets de base de données | Documents Microsoft"
description: "Ce didacticiel présente les principales fonctionnalités qui simplifient l’utilisation de T-SQL dans Studio des opérations SQL (version préliminaire)."
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b2754a998963be5a25d00aa58dcb9b4105bb8f37
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>Didacticiel : Utiliser l’éditeur Transact-SQL pour créer des objets de base de données-[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Création et exécution de requêtes, procédures stockées, scripts, etc. sont les principales tâches de professionnels de la base de données. Ce didacticiel illustre les fonctionnalités clés dans l’éditeur T-SQL pour créer des objets de base de données.

Dans ce didacticiel, vous apprenez à utiliser [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] pour :
> [!div class="checklist"]
> * Objets de base de données de recherche
> * Modifier les données de la table 
> * Utiliser des extraits de code pour écrire rapidement T-SQL
> * Détails des objets de base de données à l’aide de *aperçu de définition* et *atteindre la définition*


## <a name="prerequisites"></a>Prerequisites

Ce didacticiel nécessite SQL Server ou la base de données SQL Azure *TutorialDB*. Pour créer le *TutorialDB* de base de données, effectuez l’une des Démarrages rapides suivants :

- [Se connecter et interroger à l’aide de SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Se connecter et interroger à l’aide de la base de données SQL Azure[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Rapidement localiser un objet de base de données et effectuer une tâche courante

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]fournit un widget de recherche pour trouver rapidement les objets de base de données. La liste des résultats fournit un menu contextuel pour les tâches courantes relatives à l’objet sélectionné, tel que *modifier les données* pour une table.

1. Ouvrez la barre latérale de serveurs (**Ctrl + G**), développez **bases de données**, puis sélectionnez **TutorialDB**. 

1. Ouvrez le *TutorialDB le tableau de bord* en sélectionnant **gérer** dans le menu contextuel.

   ![menu contextuel - gérer](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. Recherchez le *clients* table en tapant *nalisée* dans le widget de recherche.
1. Avec le bouton droit **dbo. Clients** et sélectionnez **modifier les données**.

   ![widget de la recherche rapide](./media/tutorial-sql-editor/quick-search-widget.png)

1. Modifier la **messagerie** colonne dans la première ligne, type  *orlando0@adventure-works.com* et appuyez sur **entrée** pour enregistrer les modifications.

   ![modifier des données](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-a-stored-procedure"></a>Utiliser des extraits de code T-SQL pour créer une procédure stockée

### <a name="use-snippets-in-includename-sos-shortincludesname-sos-shortmd"></a>Utiliser des extraits de code dans[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]

1. Ouvrez un nouvel éditeur de requête en appuyant sur **Ctrl + N**.

2. Type **sql** dans l’éditeur, la flèche vers le bas pour **sqlCreateStoredProcedure**, puis appuyez sur la *onglet* clé de chargement du nouvel extrait de la procédure stockée.

   ![liste de l’extrait de code](./media/tutorial-sql-editor/snippet-list.png)

3. Type *getCustomer* et tous les *StoredProcedureName* pour modifier les entrées *getCustomer*. 

   ![Extrait de code](./media/tutorial-sql-editor/snippet.png)

4. Remplacez le reste de la procédure stockée T-SQL ci-dessous :

    ```sql
    -- Create a new stored procedure called 'getCustomer' in schema 'dbo'
    -- Drop the stored procedure if it already exists
    IF EXISTS (
    SELECT *
    FROM INFORMATION_SCHEMA.ROUTINES
    WHERE SPECIFIC_SCHEMA = N'dbo'
    AND SPECIFIC_NAME = N'getCustomer'
    )
    DROP PROCEDURE dbo.getCustomer
    GO
    -- Create the stored procedure in the specified schema
    CREATE PROCEDURE dbo.getCustomer
    @ID int
    -- add more stored procedure parameters here
    AS
    -- body of the stored procedure
    SELECT  c.CustomerID, 
    c.Name, 
    c.Location, 
    c.Email
    FROM dbo.Customers c
    WHERE c.CustomerID = @ID
    FOR JSON PATH

    GO
    -- example to execute the stored procedure we just created
    EXECUTE dbo.getCustomer 1
    GO
    ```
    
5. Pour créer la procédure stockée et lui donner une série de tests, appuyez sur **F5**.

## <a name="use-peek-definition-and-go-to-definition"></a>Utilisez Aperçu de définition et d’atteindre la définition 

1. Ouvrez un nouvel éditeur en appuyant sur **Ctrl + N**. 

2. Tapez et sélectionnez **sqlCreateStoredProcedure** à partir de la liste de suggestions d’extrait de code. Tapez dans **setCustomer** pour **StoredProcedureName** et **dbo** pour **SchemaName**

3. Remplacez le @param lignes avec la définition des paramètres suivants :

   ```sql
       @json_val nvarchar(max)
   ```

4. Remplacez le corps de la procédure stockée avec les éléments suivants :
   ```sql
   -- body of the stored procedure
   INSERT INTO dbo.Customers
   ```

5. Avec le bouton droit **dbo. Clients** et sélectionnez **aperçu de définition**.

   ![Aperçu de définition](./media/tutorial-sql-editor/peek-definition.png)

6. La définition de table permet de compléter l’instruction insert suivante :

   ```sql
   INSERT INTO dbo.Customers (CustomerID, Name, Location, Email)
       SELECT CustomerID, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerID int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
   ```
7. L’instruction finale doit être :

   ```sql
   -- Create a new stored procedure called 'setCustomer' in schema 'dbo'
   -- Drop the stored procedure if it already exists
   IF EXISTS (
   SELECT *
       FROM INFORMATION_SCHEMA.ROUTINES
       WHERE SPECIFIC_SCHEMA = N'dbo'
       AND SPECIFIC_NAME = N'setCustomer'
   )
   DROP PROCEDURE dbo.setCustomer
   GO
   -- Create the stored procedure in the specified schema
   CREATE PROCEDURE dbo.setCustomer
       @json_val nvarchar(max) 
   AS
       -- body of the stored procedure
       INSERT INTO dbo.Customers (CustomerID, Name, Location, Email)
       SELECT CustomerID, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerID int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
       )
   GO
   ```

8. Pour exécuter le script, appuyez sur **F5**.

## <a name="use-save-query-results-as-json-to-test-our-stored-procedure"></a>Utilisez Enregistrer les résultats de la requête au format JSON pour tester la procédure stockée

1. **Sélectionnez 1000 lignes du haut** à partir de la *dbo. Clients* table.

2. Sélectionnez la première ligne dans l’affichage des résultats et cliquez sur **enregistrer en tant que JSON**.  
3. Cliquez sur **enregistrer**, et il s’ouvre à la ligne en surbrillance au format JSON.

   ![Enregistrer en tant que JSON](./media/tutorial-sql-editor/save-as-json.png)

4. Sélectionnez les données JSON et copiez-la.

5. Ouvrez une nouvelle requête pour *TutorialDB* et exécuter le script de test suivantes à l’aide des données JSON en tant que modèle à partir de l’étape précédente. Modifier les valeurs de *CustomerID*, *nom*, *emplacement*, et *E-mail*.

   ```sql
   -- example to execute the stored procedure we just created
   declare @json nvarchar(max) =
   N'[
       {
           "CustomerID": 5,
           "Name": "Lucy",
           "Location": "Canada",
           "Email": "lucy0@adventure-works.com"
       }
   ]'

   EXECUTE dbo.setCustomer @json_val = @json
   GO

   EXECUTE dbo.getCustomer @ID = 5
   ```

7. Exécutez le script en appuyant sur **F5**. Le script insère un nouveau client et retourne les nouvelles informations du client au format JSON. Cliquez sur le résultat pour ouvrir une vue mise en forme.

   ![Résultat de test](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>Étapes suivantes
Dans ce didacticiel, vous avez appris comment :
> [!div class="checklist"]
> * Objets de schéma de recherche rapide
> * Modifier les données de la table 
> * L’écriture de script T-SQL à l’aide d’extraits de code
> * En savoir plus sur les détails de l’objet de base de données à l’aide d’aperçu de définition et d’atteindre la définition


Pour savoir comment activer la **cinq premières requêtes** exemple insight, effectuer le didacticiel suivant :

> [!div class="nextstepaction"]
> [Activer le widget d’insight exemple requêtes lentes](tutorial-qds-sql-server.md)
