---
title: Jeu de données IRIS démonstration de didacticiels Python et R dans SQL Server | Microsoft Docs
Description: Create a database containing the Iris dataset and a table for storing models. This dataset is used in exercises showing how to wrap R language or Python code in a SQL Server stored procedure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2fbe5915f7b135882bbbefbb83b572d2cd640837
ms.sourcegitcommit: 12779bddd056a203d466d83c4a510a97348fe9d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216679"
---
#  <a name="iris-demo-data-for-python-and-r-tutorials-in-sql-server"></a>Données de démonstration d’iris de didacticiels Python et R dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans cet exercice, créez une base de données SQL Server pour stocker des données à partir de la [jeu de données Iris fleur](https://en.wikipedia.org/wiki/Iris_flower_data_set) et modèles basés sur les mêmes données. Données IRIS sont incluses dans les distributions de R et Python installées par SQL Server et sont utilisées dans les didacticiels de machine learning pour SQL Server. 

Pour effectuer cet exercice, vous devez disposer [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) ou un autre outil qui peut exécuter des requêtes T-SQL.

Didacticiels et guides de démarrage rapide à l’aide de ce jeu de données sont les suivantes :

+  [Utiliser un modèle Python dans SQL Server pour l’apprentissage et notation](train-score-using-python-in-tsql.md)

## <a name="create-the-database"></a>Créer la base de données

1. Démarrez SQL Server Management Studio et ouvrez une nouvelle **requête** fenêtre.  

2. Créer une base de données pour ce projet et de modifier le contexte de votre **requête** fenêtre à utiliser la nouvelle base de données.

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

    > [!TIP] 
    > Si vous ne connaissez pas SQL Server, ou que vous travaillez sur un serveur que vous possédez, une erreur courante consiste à se connecter et commencer à travailler sans remarquer que vous êtes dans le **master** base de données. Pour être sûr que vous utilisez la base de données, spécifiez toujours le contexte à l’aide de la `USE <database name>` instruction (par exemple, `use irissql`).

3. Ajouter des tables vides : un pour stocker les données et un pour stocker les modèles formés. Le **iris_models** table est utilisée pour stocker les modèles sérialisés générés dans d’autres exercices.

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
    > Si vous débutez avec T-SQL, il est judicieux de mémoriser la `DROP...IF` instruction. Lorsque vous essayez de créer une table, et il en existe déjà, SQL Server retourne une erreur : « Il existe déjà un objet nommé « iris_data » dans la base de données. » Pour éviter de telles erreurs consiste à supprimer des tables existantes ou autres objets dans le cadre de votre code.

4. Exécutez le code suivant pour créer la table utilisée pour stocker le modèle formé. Pour enregistrer les modèles Python (ou R) dans SQL Server, il doivent être sérialisés et stockés dans une colonne de type **varbinary (max)**. 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    En plus du contenu du modèle, en règle générale, vous également ajouter des colonnes pour les autres métadonnées utiles, telles que le nom du modèle, la date, qu'il a été formé, l’algorithme de source et les paramètres, les données sources et ainsi de suite. Pour l’instant nous plus de simplicité et utilisez le nom du modèle.

## <a name="populate-the-table"></a>Remplissez la table

Vous pouvez obtenir des données Iris intégré à partir de R ou Python. Vous pouvez utiliser Python ou R pour charger les données dans une trame de données et puis l’insérer dans une table dans la base de données. Déplacement des données d’apprentissage à partir d’une session externe dans une table SQL Server est un processus en plusieurs étapes :

+ Concevoir une procédure stockée qui obtient les données souhaitées.
+ Exécutez la procédure stockée pour accéder aux données.
+ Construisez une instruction INSERT pour spécifier où les données récupérées doivent être enregistrées.

1. Sur les systèmes avec l’intégration de Python, créez la procédure stockée suivante qui utilise le code Python pour charger les données.

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

    Lorsque vous exécutez ce code, vous devez obtenir le message « Commandes sont bien déroulée. » Cela signifie est que la procédure stockée a été créée en fonction de vos spécifications.

2. Vous pouvez également sur les systèmes avec intégration de R, vous devez créer une procédure qui utilise à la place de R.

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

3. Pour réellement remplir la table, exécutez la procédure stockée et spécifier la table où les données doivent être écrites. Lors de l’exécution, la procédure stockée s’exécute le code Python ou R, qui charge le jeu de données Iris intégré et puis insère les données dans le **iris_data** table.

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Si vous débutez avec T-SQL, n’oubliez pas que l’instruction INSERT ajoute uniquement les nouvelles données ; Il ne vérifier les données existantes, ou supprimer et recréer la table. Pour éviter d’obtenir plusieurs copies des mêmes données dans une table, vous pouvez exécuter cette instruction tout d’abord : `TRUNCATE TABLE iris_data`. Le code T-SQL [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) instruction supprime les données existantes, mais conserve la structure de la table intact.

    > [!TIP]
    > Pour modifier la procédure stockée plus tard, vous n’avez pas besoin supprimer et recréer. Utilisez le [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql) instruction. 


## <a name="query-the-data"></a>Interroger les données

Comme une étape de validation, exécutez une requête pour confirmer que le téléchargement de données.

1. Dans l’Explorateur d’objets, des bases de données, cliquez sur le **irissql** de base de données et démarrer une nouvelle requête.

2. Exécutez des requêtes simples :

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>Étapes suivantes

Dans la leçon suivante, vous créer un modèle d’apprentissage automatique et enregistrez-le dans une table et ensuite utiliser le modèle pour générer les résultats prédits.

+ [Utiliser un modèle Python dans SQL Server pour l’apprentissage et notation](train-score-using-python-in-tsql.md)
