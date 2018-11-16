---
title: Modèles de Python dans SQL Server pour la formation et des prédictions à l’aide de procédures stockées | Microsoft Docs
description: Incorporer le code Python dans les procédures stockées SQL Server pour créer, former et utiliser un modèle Python avec le jeu de données Iris classique. Enregistrer un modèle formé dans SQL Server, puis l’utiliser pour générer les résultats prédits.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/23/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 17b51d695a923b6db1661e6e15605a1f05d08178
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51293155"
---
# <a name="create-train-and-use-a-python-model-with-stored-procedures-in-sql-server"></a>Créer, former et utiliser un modèle Python avec des procédures stockées dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet exercice montre l’intégration de Python avec SQL Server lorsque vous ajoutez le [Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) fonctionnalité à une instance du moteur de base de données. Dans ce cas, vous pouvez encapsuler le code Python à l’intérieur d’un [procédure stockée](../../relational-databases/stored-procedures/stored-procedures-database-engine.md) pour faire fonctionner votre script pour les charges de travail de production. La possibilité d’incorporer le code dans une procédure stockée a des avantages tangibles dans comment concevoir, tester et gérer des tâches d’apprentissage et de science des données. Elle rend votre script et les modèles accessible à toute application pouvant se connecter à SQL Server.

Dans cet exercice Python, vous créer et exécuter deux procédures stockées. Le premier utilise le jeu de données Iris fleur classique et génère un modèle de Naïve Bayes pour prédire une espèce Iris en fonction des caractéristiques de la fleur. La deuxième procédure est pour calculer les scores. Il appelle le modèle généré dans la première procédure pour un ensemble de prédictions de sortie. En plaçant le code dans une procédure stockée, les opérations sont relation contenant-contenu, réutilisables et pouvant être appelées par d’autres procédures stockées et les applications clientes. 

En suivant ce didacticiel, vous allez apprendre :

> [!div class="checklist"]
> * Guide pratique pour incorporer le code Python dans une procédure stockée
> * Comment passer des entrées dans votre code via des entrées sur la procédure stockée
> * Comment les procédures stockées sont utilisées pour configurer les modèles

## <a name="prerequisites"></a>Prérequis

Exemples de données utilisés dans cet exercice est la [ **irissql** ](demo-data-iris-in-sql.md) base de données.

Vous devez également un éditeur T-SQL, tel que [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017).

## <a name="create-a-stored-procedure-that-generates-models"></a>Créer une procédure stockée qui génère des modèles

Il est courant dans le développement de SQL Server pour organiser les opérations programmables dans les procédures stockées distinctes. Dans cette étape, vous allez créer une procédure stockée qui génère un modèle pour prévoir les résultats. 

1. Ouvrez une nouvelle fenêtre de requête dans Management Studio, connecté à la **irissql** base de données. 

    ```sql
    USE irissql
    GO
    ```

2. Copier dans le code suivant pour créer une nouvelle procédure stockée. 

   Lors de l’exécution, cette procédure appelle [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) pour démarrer une session de Python. 
   
   Les entrées requises par votre code Python sont passées comme paramètres d’entrée sur cette procédure stockée. Sortie correspond à un modèle formé, selon les Python **scikit-Découvrez** bibliothèque pour l’algorithme d’apprentissage automatique. 

   Ce code utilise [ **pickle** ](https://docs.python.org/2/library/pickle.html) pour sérialiser le modèle. Le modèle sera formé à l’aide de données à partir de colonnes entre 0 et 4 à partir de la **iris_data** table. 
   
   Les paramètres que vous voyez dans la deuxième partie de la procédure formulez des entrées de données et sorties de modèle. Autant que possible, vous souhaitez que le code Python en cours d’exécution dans une procédure stockée pour avoir défini clairement les entrées et sorties qui correspondent aux entrées de la procédure stockée et les sorties passées au moment de l’exécution. 

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python',
    @script = N'
    import pickle
    from sklearn.naive_bayes import GaussianNB
    GNB = GaussianNB()
    trained_model = pickle.dumps(GNB.fit(iris_data[[0,1,2,3]], iris_data[[4]]))
    '
    , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@trained_model varbinary(max) OUTPUT'
    , @trained_model = @trained_model OUTPUT;
    END;
    GO
    ```

3. Vérifiez que la procédure stockée existe. 

   Si le script T-SQL à partir de l’étape précédente s’est exécuté sans erreur, une nouvelle procédure stockée appelée **generate_iris_model** est créé et ajouté à la **irissql** base de données. Vous trouverez des procédures stockées dans Management Studio **Explorateur d’objets**, sous **programmabilité**.

## <a name="execute-the-procedure-to-create-and-train-models"></a>Exécutez la procédure pour créer et former des modèles

Dans cette étape, exécutez la procédure pour exécuter le code incorporé, création d’un modèle formé et sérialisé en tant que sortie. Modèles qui sont stockés pour une réutilisation dans SQL Server sont sérialisées comme un flux d’octets et stockés dans une colonne varbinary (max) dans une table de base de données. Une fois que le modèle est créé, formé, sérialisé et enregistré dans une base de données, elle peut être appelée par d’autres procédures ou par le [T-SQL prédire](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) fonction dans les scores de charges de travail.

1. Copiez le code suivant pour exécuter la procédure. L’instruction spécifique pour l’exécution d’une procédure stockée est `EXEC` sur la cinquième ligne.

   Ce script supprime un modèle existant portant le même nom (« Naive Bayes ») pour faire place aux nouveaux créée en exécutant de nouveau la même procédure. Sans la suppression du modèle, une erreur se produit indiquant que l’objet existe déjà. Le modèle est stocké dans une table appelée **iris_models**, mis en service lorsque vous avez créé le **irissql** base de données.

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes '
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

2. Afficher les résultats dans la zone de sortie. Le script inclut une instruction SELECT montrant que le modèle existe. Une autre méthode pour retourner une liste de modèles est `SELECT * FROM iris_models` dans **irissql**.

    **Résultats**

    |   | (aucun nom de colonne |
    |---|-----------------|
    | 1 | Naive Bayes     | 


## <a name="create-and-execute-a-stored-procedure-for-generating-predictions"></a>Créer et exécuter une procédure stockée pour générer des prédictions

Maintenant que vous avez créé, formé et enregistré un modèle, passez à l’étape suivante : création d’une procédure stockée qui génère des prédictions. Vous effectuerez cela en appelant sp_execute_external_script pour démarrer Python, puis passer dans le script Python qui charge un modèle sérialisé votre créé dans l’exercice précédent, puis lui donne des entrées de données dont calculer le score.

1. Exécutez le code suivant pour créer la procédure stockée qui effectue le calcul de score. Au moment de l’exécution, cette procédure sera charger un modèle binaire, utilisez les colonnes `[1,2,3,4]` comme entrées et spécifier les colonnes `[0,5,6]` en tant que sortie.

    ```sql
    CREATE PROCEDURE predict_species (@model varchar(100))
    AS
    BEGIN
    DECLARE @nb_model varbinary(max) = (SELECT model FROM iris_models WHERE model_name = @model);
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    import pickle
    irismodel = pickle.loads(nb_model)
    species_pred = irismodel.predict(iris_data[[1,2,3,4]])
    iris_data["PredictedSpecies"] = species_pred
    OutputDataSet = iris_data[[0,5,6]] 
    print(OutputDataSet)
    '
    , @input_data_1 = N'select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@nb_model varbinary(max)'
    , @nb_model = @nb_model
    WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));
    END;
    GO
    ```

2. Exécutez la procédure stockée, en donnant le nom de modèle « Naive Bayes » afin que la procédure sache quel modèle utiliser. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    Lorsque vous exécutez la procédure stockée, elle retourne une trame de données Python. Cette ligne de T-SQL spécifie le schéma pour les résultats retournés : `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`. Vous pouvez insérer les résultats dans une nouvelle table, ou les renvoyer à une application.

    ![Jeu de résultats d’exécution de procédure stockée](media/train-score-using-python-NB-model-results.png)

    Les résultats sont des 150 prédictions sur espèces à l’aide des caractéristiques de fleurs en tant qu’entrées. Pour la majorité des observations, l’espèce prédite correspond à l’espèce réelle.

    Cet exemple a été effectué simple à l’aide du jeu de données iris Python pour l’apprentissage et le calcul de score. Une approche plus classique serait impliquent l’exécution d’une requête SQL pour obtenir les nouvelles données et passez dans Python comme `InputDataSet`. 

## <a name="conclusion"></a>Conclusion

Dans cet exercice, vous avez appris à créer des procédures stockées dédiés aux différentes tâches, où chaque procédure stockée utilisé la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour démarrer un processus Python. Entrées dans le processus de Python sont transmies au script de sp_execute_external en tant que paramètres. Le script Python proprement dit et les variables de données dans une base de données SQL Server sont passés en tant qu’entrées.

En règle générale, vous devez prévoir uniquement à l’aide de SSMS avec le code Python poli ou le code Python simple qui retourne une sortie basée sur la ligne. En tant qu’outil, SSMS prend en charge des langages de requête similaire à T-SQL et retourne les ensembles de lignes aplatis. Si votre code génère une sortie visual comme un nuage de points ou d’un histogramme, vous avez besoin d’une application outil ou par l’utilisateur final qui peut afficher l’image.

Pour certains développeurs Python qui sont habitués à écrire de script complet, une plage d’opérations de gestion des, organisation des tâches dans des procédures distinctes peut sembler inutile. Mais d’apprentissage et de notation différents cas d’usage. En les séparant, vous pouvez placer chaque tâche sur planification différente et les autorisations de portée pour l’opération.

De même, vous pouvez également exploiter les ressources ou des fonctionnalités de SQL Server, telles que le traitement parallèle, la gouvernance des ressources, en écrivant votre script pour utiliser les algorithmes dans [revoscalepy](../python/what-is-revoscalepy.md) ou [MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) qui prend en charge la diffusion en continu et en parallèle. En séparant l’apprentissage et l’évaluation, vous pouvez cibler les optimisations pour les charges de travail spécifiques.

Un avantage final est que les processus peuvent être modifiées à l’aide de paramètres. Dans cet exercice, le code Python qui a créé le modèle (nommé « Naive Bayes » dans cet exemple) a été passé en tant qu’entrée à une procédure stockée deuxième appeler le modèle dans un processus de calcul de score. Cet exercice utilise uniquement un seul modèle, mais vous pouvez l’imaginer comment paramétrer le modèle dans une tâche de calcul de score rendrait ce script plus utile.

## <a name="next-steps"></a>Étapes suivantes

Si vous êtes développeur SQL Python, passez en revue les étapes et les outils permettant de travailler avec le code Python localement, avec la possibilité de décalage de l’exécution à partir de sessions locales vers une instance distante de SQL Server.

> [!div class="nextstepaction"]
> [Configurer une station de travail du client Python](../python/setup-python-client-tools-sql.md).

