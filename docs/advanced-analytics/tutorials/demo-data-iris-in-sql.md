---
title: Jeu de données de démonstration Iris pour les didacticiels Python et R
Description: Créer une base de données contenant le jeu de données Iris et une table pour le stockage des modèles. Ce jeu de données est utilisé dans les exercices qui montrent comment encapsuler le code R ou python dans une procédure stockée SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 9e5fb470e9045060e6cf2423470c2e4e1ee14f30
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469648"
---
#  <a name="iris-demo-data-for-python-and-r-tutorials-in-sql-server"></a>Données de démonstration Iris pour les didacticiels Python et R dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans cet exercice, créez une base de données SQL Server pour stocker des données à partir du jeu de données de la [fleur Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) et des modèles basés sur les mêmes données. Les données de l’iris sont incluses dans les distributions R et Python installées par SQL Server, et sont utilisées dans les didacticiels de Machine Learning pour SQL Server. 

Pour effectuer cet exercice, vous devez disposer d' [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) ou d’un autre outil capable d’exécuter des requêtes T-SQL.

Les didacticiels et les guides de démarrage rapide utilisant ce jeu de données sont les suivants:

+  [Démarrage rapide : Créer, former et utiliser un modèle Python avec des procédures stockées dans SQL Server](quickstart-python-train-score-in-tsql.md)

## <a name="create-the-database"></a>Créer la base de données

1. Démarrez SQL Server Management Studio, puis ouvrez une nouvelle fenêtre de **requête** .  

2. Créez une nouvelle base de données pour ce projet, puis modifiez le contexte de votre fenêtre de **requête** pour utiliser la nouvelle base de données.

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

    > [!TIP] 
    > Si vous ne connaissez pas SQL Server ou que vous travaillez sur un serveur que vous possédez, une erreur courante consiste à vous connecter et à commencer à travailler sans remarquer que vous êtes dans la base de données **Master** . Pour vous assurer que vous utilisez la base de données correcte, spécifiez toujours le contexte `USE <database name>` à l’aide de l' `use irissql`instruction (par exemple,).

3. Ajoutez des tables vides: l’une pour stocker les données et l’autre pour stocker les modèles formés. La table **iris_models** est utilisée pour stocker les modèles sérialisés générés dans d’autres exercices.

    Le code suivant crée la table pour les données d’apprentissage.

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
    > Si vous débutez avec T-SQL, il est payant de mémoriser `DROP...IF` l’instruction. Lorsque vous essayez de créer une table et qu’une table existe déjà, SQL Server retourne une erreur: «Il existe déjà un objet nommé «iris_data» dans la base de données». Pour éviter de telles erreurs, vous pouvez supprimer des tables ou d’autres objets existants dans le cadre de votre code.

4. Exécutez le code suivant pour créer la table utilisée pour le stockage du modèle formé. Pour enregistrer des modèles Python (ou R) dans SQL Server, ils doivent être sérialisés et stockés dans une colonne de type **varbinary (max)** . 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    En plus du contenu du modèle, en général, vous ajoutez également des colonnes pour d’autres métadonnées utiles, telles que le nom du modèle, la date à laquelle il a été formé, l’algorithme source, les paramètres, les données sources, etc. Pour l’instant, nous allons simplifier et utiliser simplement le nom du modèle.

## <a name="populate-the-table"></a>Remplir la table

Vous pouvez obtenir des données d’IRIS intégrées à partir de R ou de Python. Vous pouvez utiliser python ou R pour charger les données dans une trame de données, puis les insérer dans une table de la base de données. Le déplacement des données d’apprentissage d’une session externe dans une table de SQL Server est un processus à étapes:

+ Concevez une procédure stockée qui obtient les données souhaitées.
+ Exécutez la procédure stockée pour récupérer les données.
+ Construisez une instruction INSERT pour spécifier l’emplacement où les données récupérées doivent être enregistrées.

1. Sur les systèmes avec intégration Python, créez la procédure stockée suivante qui utilise le code Python pour charger les données.

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

    Lorsque vous exécutez ce code, vous devez recevoir le message «commandes terminées avec succès». Cela signifie que la procédure stockée a été créée en fonction de vos spécifications.

2. En guise d’alternative, sur les systèmes dotés de l’intégration R, créez une procédure qui utilise R à la place.

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

3. Pour remplir réellement la table, exécutez la procédure stockée et spécifiez la table dans laquelle les données doivent être écrites. Quand elle est exécutée, la procédure stockée exécute le code python ou R, qui charge le jeu de données Iris intégré, puis insère les données dans la table **iris_data** .

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Si vous débutez avec T-SQL, sachez que l’instruction INSERT ajoute uniquement de nouvelles données; il ne recherche pas les données existantes, ou supprime et régénère la table. Pour éviter d’obtenir plusieurs copies des mêmes données dans une table, vous pouvez exécuter l’instruction en premier `TRUNCATE TABLE iris_data`:. L’instruction T-SQL [truncate table](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) supprime les données existantes, mais conserve la structure de la table intacte.

    > [!TIP]
    > Pour modifier la procédure stockée ultérieurement, vous n’avez pas besoin de la supprimer et de la recréer. Utilisez l’instruction [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql) . 


## <a name="query-the-data"></a>Interroger les données

En guise d’étape de validation, exécutez une requête pour confirmer que les données ont été téléchargées.

1. Dans l’Explorateur d’objets, sous bases de données, cliquez avec le bouton droit sur la base de données **irissql** et démarrez une nouvelle requête.

2. Exécuter des requêtes simples:

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>Étapes suivantes

Dans le démarrage rapide suivant, vous allez créer un modèle de Machine Learning et l’enregistrer dans une table, puis utiliser le modèle pour générer des résultats prédits.

+ [Démarrage rapide : Créer, former et utiliser un modèle Python avec des procédures stockées dans SQL Server](quickstart-python-train-score-in-tsql.md)
