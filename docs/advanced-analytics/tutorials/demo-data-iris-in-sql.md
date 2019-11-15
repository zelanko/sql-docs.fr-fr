---
title: Jeu de données de démonstration Iris pour les tutoriels
Description: Créez une base de données contenant le jeu de données Iris ainsi qu’une table pour stocker des modèles. Ce jeu de données est utilisé dans des exercices qui montrent comment encapsuler le langage R ou du code Python dans une procédure stockée SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e580a4d3b8d0e294573cf19c0194cc9b8a103518
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727098"
---
#  <a name="iris-demo-data-for-python-and-r-tutorials-in-sql-server"></a>Données de démonstration Iris pour les tutoriels Python et R dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans cet exercice, vous allez créer une base de données SQL Server pour stocker les données du [jeu de données des fleurs Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) et des modèles basés sur les mêmes données. Les données Iris sont incluses dans les distributions R et Python installées par SQL Server, et sont utilisées dans les tutoriels de Machine Learning pour SQL Server. 

Pour effectuer cet exercice, vous devez avoir [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) ou un autre outil capable d’exécuter des requêtes T-SQL.

Voici les tutoriels et les démarrages rapides qui utilisant ce jeu de données :

+  [Démarrage rapide : Créer, entraîner et utiliser un modèle Python avec des procédures stockées dans SQL Server](quickstart-python-train-score-in-tsql.md)

## <a name="create-the-database"></a>Créer la base de données

1. Démarrez SQL Server Management Studio, puis ouvrez une nouvelle fenêtre **Requête**.  

2. Créez une base de données pour ce projet, puis changez le contexte de votre fenêtre **Requête** de façon à utiliser la nouvelle base de données.

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

    > [!TIP] 
    > Si vous débutez avec SQL Server ou que vous travaillez sur un serveur qui vous appartient, l’erreur serait de vous connecter et de commencer à travailler sans faire attention que vous êtes dans la base de données **MASTER**. Pour vérifiez que vous utilisez la bonne base de données, précisez toujours le contexte à l’aide de l’instruction `USE <database name>` (par exemple, `use irissql`).

3. Ajoutez des tables vides : une pour stocker les données et une autre pour stocker les modèles entraînés. La table **iris_models** sert à stocker les modèles sérialisés générés dans les autres exercices.

    Le code suivant crée la table pour les données d’entraînement.

    ```sql
    DROP TABLE IF EXISTS iris_data;
    GO
    CREATE TABLE iris_data (
      id INT NOT NULL IDENTITY PRIMARY KEY
      , "Sepal.Length" FLOAT NOT NULL, "Sepal.Width" FLOAT NOT NULL
      , "Petal.Length" FLOAT NOT NULL, "Petal.Width" FLOAT NOT NULL
      , "Species" VARCHAR(100) NOT NULL, "SpeciesId" INT NOT NULL
    );
    ```

    > [!TIP] 
    > Si vous débutez avec T-SQL, vous avez tout intérêt à mémoriser l’instruction `DROP...IF`. Quand vous essayez de créer une table et qu’il en existe déjà une, SQL Server retourne une erreur : « Il existe déjà un objet nommé « iris_data » dans la base de données. » Pour éviter de telles erreurs, vous pouvez supprimer des tables ou d’autres objets existants dans votre code.

4. Exécutez le code suivant pour créer la table qui va stocker le modèle entraîné. Pour enregistrer des modèles Python (ou R) dans SQL Server, ils doivent être sérialisés et stockés dans une colonne de type **varbinary(max)** . 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    Outre le contenu du modèle, il est courant d’ajouter aussi des colonnes pour d’autres métadonnées utiles, comme le nom du modèle, la date à laquelle il a été entraîné, l’algorithme et les paramètres sources, les données sources, etc. Dans un souci de simplicité, nous allons pour l’instant utiliser uniquement le nom du modèle.

## <a name="populate-the-table"></a>Remplir la table

Vous pouvez obtenir les données Iris intégrées à partir de R ou de Python. Vous pouvez utiliser Python ou R pour charger les données dans une trame de données, puis insérer celle-ci dans une table de la base de données. Le déplacement de données d’entraînement d’une session externe vers une table SQL Server est un processus multiétape :

+ Concevez une procédure stockée qui obtient les données qui vous intéressent.
+ Exécutez la procédure stockée pour récupérer réellement les données.
+ Construisez une instruction INSERT pour spécifier l’emplacement d’enregistrement des données récupérées.

1. Sur les systèmes dotés de l’intégration Python, créez la procédure stockée ci-dessous qui utilise du code Python pour charger les données.

    ```sql
    CREATE PROCEDURE get_iris_dataset
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    from sklearn import datasets
    iris = datasets.load_iris()
    iris_data = pandas.DataFrame(iris.data)
    iris_data["Species"] = pandas.Categorical.from_codes(iris.target, iris.target_names)
    iris_data["SpeciesId"] = iris.target
    ', 
    @input_data_1 = N'', 
    @output_data_1_name = N'iris_data'
    WITH RESULT SETS (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100) not null, "SpeciesId" int not null));
    END;
    GO
    ```

    Quand vous exécutez ce code, vous obtenez normalement le message suivant : « Commandes réussies. » Cela signifie que la procédure stockée a été créée selon vos spécifications.

2. Autre possibilité : sur les systèmes dotés de l’intégration R, créez une procédure qui utilise R à la place.

    ```sql
    CREATE PROCEDURE get_iris_dataset
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'R', 
    @script = N'
    library(RevoScaleR)
    data(iris)
    iris$SpeciesID <- c(unclass(iris$Species))
    iris_data <- iris
    ', 
    @input_data_1 = N'', 
    @output_data_1_name = N'iris_data'
    WITH RESULT SETS (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100) not null, "SpeciesId" int not null));
    END;
    GO
    ```

3. Pour remplir réellement la table, exécutez la procédure stockée et spécifiez la table dans laquelle les données doivent être écrites. Quand elle est exécutée, la procédure stockée exécute le code Python ou R, qui charge le jeu de données Iris intégré, puis insère les données dans la table **iris_data**.

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Si vous débutez avec T-SQL, sachez que l’instruction INSERT ajoute uniquement de nouvelles données ; elle ne recherche pas de données existantes ni ne supprime et regénère la table. Pour éviter d’avoir plusieurs copies des mêmes données dans une table, vous pouvez d’abord exécuter cette l’instruction : `TRUNCATE TABLE iris_data`. L’instruction T-SQL [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) supprime les données existantes, mais conserve la structure de la table intacte.

    > [!TIP]
    > Si, par la suite, vous devez modifier la procédure stockée, vous n’avez pas besoin de la supprimer et de la recréer. Utilisez l’instruction [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql). 


## <a name="query-the-data"></a>Interroger les données

En guise d’étape de validation, exécutez une requête pour vérifier que les données ont bien été chargées.

1. Dans l’Explorateur d’objets, sous Bases de données, cliquez avec le bouton droit sur la base de données **irissql**, puis démarrez une nouvelle requête.

2. Exécutez quelques requêtes simples :

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>Étapes suivantes

Dans le démarrage rapide suivant, vous allez créer un modèle de Machine Learning et l’enregistrer dans une table. Vous vous en servirez ensuite pour générer des résultats prédits.

+ [Démarrage rapide : Créer, entraîner et utiliser un modèle Python avec des procédures stockées dans SQL Server](quickstart-python-train-score-in-tsql.md)
