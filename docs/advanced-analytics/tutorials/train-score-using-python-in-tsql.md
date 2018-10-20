---
title: Utiliser un modèle Python dans SQL Server pour la formation et des prédictions | Microsoft Docs
description: Créer et former un modèle à l’aide de Python et le jeu de données Iris classique. Enregistrer le modèle dans SQL Server, puis l’utiliser pour générer les résultats prédits.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 839bcecdeaf7b5e2a7ea1297fe941353bffed20e
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461835"
---
# <a name="use-a-python-model-in-sql-server-for-training-and-scoring"></a>Utiliser un modèle Python dans SQL Server pour l’apprentissage et notation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans cet exercice Python, découvrez un modèle courant pour la création, formation et à l’aide d’un modèle dans SQL Server. Cet exercice crée deux procédures stockées. Le premier d'entre eux génère un modèle de Naïve Bayes pour prédire une espèce Iris en fonction des caractéristiques de la fleur. La deuxième procédure est pour calculer les scores. Il appelle le modèle généré dans la première procédure pour un ensemble de prédictions de sortie. En parcourant cet exercice, vous allez apprendre les techniques de base sont fondamentaux pour l’exécution de code Python sur une instance du moteur de base de données SQL Server.

Exemples de données utilisés dans cet exercice est la [jeu de données Iris](demo-data-iris-in-sql.md) dans le **irissql** base de données.

## <a name="create-a-model-using-a-sproc"></a>Créer un modèle à l’aide d’une procédure stockée

1. Ouvrez une nouvelle fenêtre de requête dans Management Studio, connecté à la **irissql** base de données. 

    ```sql
    USE irissql
    GO
    ```

2. Exécutez le code suivant dans une nouvelle fenêtre de requête pour créer la procédure stockée qui génère et effectue l’apprentissage d’un modèle. Modèles qui sont stockés pour une réutilisation dans SQL Server sont sérialisées comme un flux d’octets et stockés dans une colonne varbinary (max) dans une table de base de données. Une fois créé, le modèle formé, sérialisé et enregistrés dans une base de données, elle peut être appelée par d’autres procédures ou par la fonction de prédire le T-SQL dans les scores de charges de travail.

   Ce code utilise pickle pour sérialiser le modèle et le scikit pour fournir l’algorithme Naïve Bayes. Le modèle sera formé à l’aide de données à partir de colonnes entre 0 et 4 à partir de la **iris_data** table. Les paramètres que vous voyez dans la deuxième partie de la procédure formulez des entrées de données et sorties de modèle. 

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

3. Vérifiez que la procédure stockée existe. Si le script T-SQL à partir de l’étape précédente s’est exécuté sans erreur, une nouvelle procédure stockée appelée **generate_iris_model** est créé et ajouté à la **irissql** base de données. Vous trouverez des procédures stockées dans Management Studio **Explorateur d’objets**, sous **programmabilité**.

## <a name="execute-the-sproc-to-create-and-train-models"></a>Exécuter la procédure stockée pour créer et former des modèles

1. Une fois la procédure stockée est créée, exécutez le code suivant ci-dessous pour l’exécuter. L’instruction spécifique pour l’exécution d’une procédure stockée est `EXEC` sur la cinquième ligne.

   Ce script supprime un modèle existant portant le même nom (« Naive Bayes ») pour faire place aux nouveaux créée en exécutant de nouveau la même procédure. Sans la suppression du modèle, une erreur se produit indiquant que l’objet existe déjà. 

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


## <a name="create-and-execute-a-sproc-for-generating-predictions"></a>Créer et exécuter une procédure stockée pour générer des prédictions

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

Dans cet exercice, vous avez appris à créer des procédures stockées pour différentes tâches, où chaque procédure stockée utilisé la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour démarrer un processus Python. Entrées dans le processus de Python sont transmies au script de sp_execute_external en tant que paramètres. Le script Python proprement dit et les variables de données dans une base de données SQL Server sont passés en tant qu’entrées.

Si vous êtes habitué à utiliser dans Python, vous pouvez être habitué pour le chargement des données, créer des synthèses et des graphiques, puis apprentissage d’un modèle et générer des scores toutes dans les mêmes 250 lignes de code. Cet article diffère des approches usuelles en organisant des opérations dans des procédures distinctes. Cette pratique est utile à plusieurs niveaux.

L’un des avantages sont que vous pouvez séparer les processus en étapes reproductibles qui peuvent être modifiés à l’aide de paramètres. Autant que possible, vous souhaitez que le code Python que vous exécutez dans une procédure stockée pour ont eux-mêmes clairement défini des entrées et sorties qui correspondent à la procédure stockée entrées et sorties qui peuvent être passées au moment de l’exécution. Dans cet exercice, le code Python qui crée un modèle (nommé « Naive Bayes » dans cet exemple) est transmis en tant qu’entrée à une seconde procédure stockée qui appelle le modèle dans un processus de calcul de score.

Un deuxième avantage est que la formation et de notation des processus peut être optimisée en tirant parti des fonctionnalités de SQL Server, telles que le traitement parallèle, la gouvernance des ressources, ou à l’aide des algorithmes dans [revoscalepy](../python/what-is-revoscalepy.md) ou [MicrosoftML ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) qui prennent en charge la diffusion en continu et d’exécution en parallèle. En séparant l’apprentissage et l’évaluation, vous pouvez cibler les optimisations pour les charges de travail spécifiques.

## <a name="next-steps"></a>Étapes suivantes

Les didacticiels précédents se concentre sur l’exécution locale. Toutefois, vous pouvez également exécuter le code Python à partir d’une station de travail cliente, à l’aide de SQL Server comme contexte de calcul à distance. Pour plus d’informations sur la configuration d’une station de travail cliente qui se connecte à SQL Server, consultez [configurer les outils de client Python](../python/setup-python-client-tools-sql.md).

+ [Créer un modèle de revoscalepy à partir d’un client Python](use-python-revoscalepy-to-create-model.md)
