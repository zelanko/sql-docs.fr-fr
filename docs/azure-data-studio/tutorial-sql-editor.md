---
title: 'Didacticiel : Utiliser l’éditeur Transact-SQL Azure Data Studio pour créer des objets de base de données | Microsoft Docs'
description: Ce didacticiel illustre les fonctionnalités clées dans Azure Data Studio qui simplifient l’utilisation de T-SQL.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c2a517b1efb6a86d70bd05f9a1418792c0b61098
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49355930"
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>Didacticiel : Utiliser l’éditeur Transact-SQL pour créer des objets de base de données- [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Création et exécution de requêtes, procédures stockées, scripts, etc. sont les tâches fondamentales de professionnels de la base de données. Ce didacticiel illustre les fonctionnalités clées dans l’éditeur T-SQL pour créer des objets de base de données.

Dans ce didacticiel, vous allez apprendre à utiliser [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] pour :
> [!div class="checklist"]
> * Objets de base de données de recherche
> * Modifier les données de table 
> * Utiliser des extraits de code pour écrire rapidement du T-SQL
> * Afficher les détails objet base de données à l’aide de *aperçu de définition* et *atteindre la définition*


## <a name="prerequisites"></a>Configuration requise

Ce didacticiel requiert SQL Server ou la base de données SQL Azure *TutorialDB*. Pour créer le *TutorialDB* de base de données, effectuez l’une des Démarrages rapides suivants :

- [Se connecter et interroger à l’aide de SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Se connecter et interroger à l’aide de la base de données SQL Azure [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Rapidement localiser un objet de base de données et effectuer des tâches courantes

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] fournit un widget de recherche pour trouver rapidement des objets de base de données. La liste des résultats fournit un menu contextuel pour les tâches courantes relatives à l’objet sélectionné, tel que *modifier les données* pour une table.

1. Ouvrez la barre latérale de serveurs (**Ctrl + G**), développez **bases de données**, puis sélectionnez **TutorialDB**. 

1. Ouvrez le *TutorialDB le tableau de bord* en double-cliquant sur **TutorialDB** et en sélectionnant **gérer** dans le menu contextuel :

   ![menu contextuel - gérer](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. Le tableau de bord avec le bouton droit **dbo. Les clients** (dans le widget de recherche) et sélectionnez **modifier les données**.
   
   > [!TIP]
   > Pour les bases de données avec de nombreux objets, utiliser le widget de recherche pour rapidement localiser la table, vue, etc. que vous recherchez.

   ![widget de recherche rapide](./media/tutorial-sql-editor/quick-search-widget.png)

1. Modifier le **E-mail** colonne dans la première ligne, type *orlando0@adventure-works.com*, puis appuyez sur **entrée** pour enregistrer la modification.

   ![Modifier des données](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-stored-procedures"></a>Utiliser des extraits de code T-SQL pour créer des procédures stockées

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fournit de nombreux extraits de code T-SQL intégrés pour créer rapidement des instructions.


1. Ouvrez un nouvel éditeur de requête en appuyant sur **Ctrl + N**.

2. Type **sql** dans l’éditeur, flèche vers le bas pour **sqlCreateStoredProcedure**, puis appuyez sur la *onglet* clé (ou *entrée*) pour charger la créer stockée extrait de code de procédure.

   ![liste d’extraits](./media/tutorial-sql-editor/snippet-list.png)

3. L’extrait de code de procédure stockée create comporte deux champs défini pour une modification rapide, *StoredProcedureName* et *SchemaName*. Sélectionnez *StoredProcedureName*, avec le bouton droit, puis sélectionnez **toutes les Occurrences de modification**. Tapez maintenant *getCustomer* et tous les *StoredProcedureName* modifier les entrées à *getCustomer*.

   ![Extrait de code](./media/tutorial-sql-editor/snippet.png)

5. Remplacez toutes les occurrences de *SchemaName* à *dbo*. 
6. L’extrait de code contient les paramètres de l’espace réservé et le texte qui a besoin de la mise à jour. Le *EXECUTE* instruction contient également le texte d’espace réservé, car il ne connaît pas le nombre de paramètres a la procédure. Pour ce didacticiel mise à jour de l’extrait de code par conséquent, il ressemble le code suivant :

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
    SELECT  c.CustomerId, 
    c.Name, 
    c.Location, 
    c.Email
    FROM dbo.Customers c
    WHERE c.CustomerId = @ID
    FOR JSON PATH

    GO
    -- example to execute the stored procedure we just created
    EXECUTE dbo.getCustomer 1
    GO
    ```
    
5. Pour créer la procédure stockée et lui donner une série de tests, appuyez sur **F5**.

La procédure stockée est maintenant créée et le **résultats** volet affiche le client retourné au format JSON. Pour afficher au format JSON, cliquez sur l’enregistrement retourné. 


## <a name="use-peek-definition"></a>Utiliser l’aperçu de définition 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] Fournit la possibilité d’afficher une définition d’objets à l’aide de la fonctionnalité de la définition d’aperçu. Cette section crée une seconde procédure stockée et utilise la définition de l’aperçu pour voir quels sont les colonnes dans une table pour créer rapidement le corps de la procédure stockée.

1. Ouvrez un nouvel éditeur en appuyant sur **Ctrl + N**. 

2. Type *sql* dans l’éditeur, flèche vers le bas pour *sqlCreateStoredProcedure*, puis appuyez sur la *onglet* clé (ou *entrée*) pour charger la créer stockée extrait de code de procédure.
3. Tapez dans *setCustomer* pour *StoredProcedureName* et *dbo* pour *SchemaName*

3. Remplacez le @param des espaces réservés avec la définition du paramètre suivant :

   ```sql
   @json_val nvarchar(max)
   ```

4. Remplacez le corps de la procédure stockée par le code suivant :
   ```sql
   INSERT INTO dbo.Customers
   ```

5. Dans le *insérer* ligne vous vient d’être ajouté, clic droit **dbo. Les clients** et sélectionnez **aperçu de définition**.

   ![Aperçu de définition](./media/tutorial-sql-editor/peek-definition.png)

6. La définition de table s’affiche afin que vous pouvez rapidement voir quelles colonnes figurent dans la table. Reportez-vous à la liste des colonnes facilement suivre les instructions de votre procédure stockée. Terminer la création de l’instruction INSERT que vous avez ajoutée précédemment pour terminer le corps de la procédure stockée et fermer la fenêtre Aperçu de définition :

   ```sql
   INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
    )
   ```
7. Supprimez (ou commentez) le *EXECUTE* commande en bas de la requête.
8. L’instruction entière doit ressembler le code suivant :

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
       INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
       )
   GO
   ```

8. Pour créer le *setCustomer* procédure stockée, appuyez sur **F5**.

## <a name="use-save-query-results-as-json-to-test-the-setcustomer-stored-procedure"></a>Utilisez Enregistrer les résultats de la requête au format JSON pour tester la procédure stockée de setCustomer

Le *setCustomer* procédure stockée créée dans la section précédente nécessite JSON données être passées dans le *@json_val* paramètre. Cette section montre comment obtenir un peu correctement mis en forme de JSON à passer dans le paramètre afin de pouvoir tester la procédure stockée.

1. Dans le **serveurs** avec le bouton droit de barre latérale le *dbo. Les clients* de table et cliquez sur **sélectionner les 1000 premières lignes**.

2. Sélectionnez la première ligne dans l’affichage des résultats, vérifiez que la ligne entière est sélectionnée (cliquez sur le numéro 1 dans la colonne la plus à gauche), puis sélectionnez **enregistrer en tant que JSON**.  
3. Modifier le dossier vers un emplacement que vous en souvenir afin de pouvoir supprimer le fichier plus tard (pour le bureau de l’exemple) et cliquez sur **enregistrer**. Le JSON au format de fichier s’ouvre.

   ![Enregistrer en tant que JSON](./media/tutorial-sql-editor/save-as-json.png)

4. Sélectionner les données JSON dans l’éditeur et le copier.
5. Ouvrez un nouvel éditeur en appuyant sur **Ctrl + N**.
6. Les étapes précédentes montrent comment vous pouvez obtenir facilement les données au format correct pour effectuer l’appel à la *setCustomer* procédure. Vous pouvez voir le code suivant utilise le même format JSON avec de nouvelles informations client pour que nous pouvons tester le *setCustomer* procédure. L’instruction inclut la syntaxe pour déclarer le paramètre et d’exécuter la nouvelle fonction modèle get et de définir des procédures. Vous pouvez coller les données copiées à partir de la section précédente et modifiez-le afin qu’il est identique à l’exemple suivant ou simplement Coller l’instruction suivante dans l’éditeur de requête.

   ```sql
   -- example to execute the stored procedure we just created
   declare @json nvarchar(max) =
   N'[
       {
           "CustomerId": 5,
           "Name": "Lucy",
           "Location": "Canada",
           "Email": "lucy0@adventure-works.com"
       }
   ]'

   EXECUTE dbo.setCustomer @json_val = @json
   GO

   EXECUTE dbo.getCustomer @ID = 5
   ```

7. Exécutez le script en appuyant sur **F5**. Le script insère un nouveau client et renvoie les nouvelles informations du client au format JSON. Cliquez sur le résultat pour ouvrir une vue mise en forme.

   ![résultat de test](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>Étapes suivantes
Dans ce didacticiel, vous avez appris comment :
> [!div class="checklist"]
> * Objets de schéma de recherche rapide
> * Modifier les données de table 
> * Écriture de script T-SQL à l’aide d’extraits de code
> * En savoir plus sur les détails de l’objet de base de données à l’aide d’aperçu de définition et atteindre la définition


Pour savoir comment activer la **cinq requêtes les plus lentes** widget, suivre le didacticiel suivant :

> [!div class="nextstepaction"]
> [Activer le widget d’insight exemple requêtes lentes](tutorial-qds-sql-server.md)
