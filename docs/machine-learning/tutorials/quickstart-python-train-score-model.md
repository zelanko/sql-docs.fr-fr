---
title: 'Démarrage rapide : Effectuer l’apprentissage d’un modèle avec Python'
description: Dans ce guide de démarrage rapide, vous allez créer et former un modèle prédictif à l’aide de Python. Vous allez enregistrer le modèle dans une table de votre instance de SQL Server, puis utiliser le modèle pour prédire des valeurs à partir de nouvelles données avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/28/2020
ms.topic: quickstart
author: cawrites
ms.author: chadam
ms.reviewer: garye
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 929491de1eb99835133d04d396023b84680af9f4
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606861"
---
# <a name="quickstart-create-and-score-a-predictive-model-in-python-with-sql-server-machine-learning-services"></a>Démarrage rapide : Créer et évaluer un modèle prédictif en Python avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Dans ce guide de démarrage rapide, vous allez créer et former un modèle prédictif à l’aide de Python. Vous allez enregistrer le modèle dans une table de votre instance de SQL Server, puis utiliser le modèle pour prédire des valeurs à partir de nouvelles données à l’aide de [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) ou sur des [clusters Big Data](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Dans ce guide de démarrage rapide, vous allez créer et former un modèle prédictif à l’aide de Python. Vous allez enregistrer le modèle dans une table de votre instance de SQL Server, puis utiliser le modèle pour prédire des valeurs à partir de nouvelles données avec [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md).
::: moniker-end

Vous allez créer et exécuter deux procédures stockées qui s’exécutent dans SQL. La première utilise le jeu de données classique des iris et génère un modèle bayésien naïf pour prédire une espèce d’iris en fonction des caractéristiques de la fleur. La deuxième procédure concerne le scoring : elle appelle le modèle généré dans la première procédure pour générer un ensemble de prédictions basées sur de nouvelles données. En plaçant le code Python dans une procédure stockée SQL, les opérations sont contenues dans SQL et sont réutilisables. Elles peuvent alors être appelées par d’autres procédures stockées et applications clientes.

En suivant ce guide de démarrage rapide, vous apprendrez :

> [!div class="checklist"]
> - Comment incorporer du code Python dans une procédure stockée
> - Comment transmettre des entrées dans votre code via des entrées sur la procédure stockée
> - Comment les procédures stockées sont utilisées pour rendre les modèles opérationnels

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
- SQL Server Machine Learning Services. Pour savoir comment installer Machine Learning Services, consultez le [Guide d’installation Windows](../install/sql-machine-learning-services-windows-install.md) ou le [Guide d’installation Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json). Vous pouvez également [activer Machine Learning Services sur des clusters Big Data SQL Server](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
- SQL Server Machine Learning Services. Pour savoir comment installer Machine Learning Services, consultez le [Guide d’installation Windows](../install/sql-machine-learning-services-windows-install.md). 
::: moniker-end

- Un outil pour exécuter les requêtes SQL qui contiennent des scripts R. Ce guide de démarrage rapide utilise [Azure Data Studio](../../azure-data-studio/what-is.md).


- L’échantillon de données utilisé dans cet exercice est l’échantillon Iris. Suivez les instructions de la page [Données de démonstration Iris](demo-data-iris-in-sql.md) pour créer la base de données exemple **irissql**.

## <a name="create-a-stored-procedure-that-generates-models"></a>Créer une procédure stockée qui génère des modèles

À cette étape, vous allez créer une procédure stockée qui génère un modèle pour prédire les résultats.

1. Ouvrez Azure Data Studio, connectez-vous à votre instance de SQL Server et ouvrez une nouvelle fenêtre de requête.

1. Connectez-vous à la base de données irissql.

    ```sql
    USE irissql
    GO
    ```

1. Copiez-y le code suivant pour créer une nouvelle procédure stockée.

   Lorsqu’elle est exécutée, cette procédure appelle [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour démarrer une session Python. 
   
   Les entrées nécessaires à votre code Python sont transmises en tant que paramètres d’entrée sur cette procédure stockée. La sortie sera un modèle entraîné, basé sur la bibliothèque Python **scikit-learn** pour l’algorithme de Machine Learning. 

   Ce code utilise [**pickle**](https://docs.python.org/2/library/pickle.html) pour sérialiser le modèle. L’apprentissage du modèle se fera à l’aide des données des colonnes 0 à 4 de la table **iris_data**. 
   
   Les paramètres que vous voyez dans la deuxième partie de la procédure articulent les entrées de données et les sorties du modèle. Ce qui vous intéresse, c’est d’avoir le code Python qui s’exécute dans une procédure stockée avec des entrées et des sorties bien définies qui correspondent aux entrées des procédures stockées et aux sorties transmises au moment de l’exécution.

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model VARBINARY(max) OUTPUT)
    AS
    BEGIN
        EXECUTE sp_execute_external_script @language = N'Python'
            , @script = N'
    import pickle
    from sklearn.naive_bayes import GaussianNB
    GNB = GaussianNB()
    trained_model = pickle.dumps(GNB.fit(iris_data[["Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width"]], iris_data[["SpeciesId"]].values.ravel()))
    '
            , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
            , @input_data_1_name = N'iris_data'
            , @params = N'@trained_model varbinary(max) OUTPUT'
            , @trained_model = @trained_model OUTPUT;
    END;
    GO
    ```

1. Vérifiez que la procédure stockée existe. 

   Si le script T-SQL de l’étape précédente s’est exécuté sans erreur, une nouvelle procédure stockée appelée **generate_iris_model** est créée et ajoutée à la base de données **irissql**. Vous trouverez des procédures stockées dans **l’Explorateur d’objets** Azure Data Studio, sous **Programmabilité**.

## <a name="execute-the-procedure-to-create-and-train-models"></a>Exécuter la procédure pour créer des modèles et effectuer leur apprentissage

À cette étape, vous allez exécuter la procédure pour exécuter le code incorporé, en créant un modèle formé et sérialisé en tant que sortie. 

Les modèles qui sont stockés pour être réutilisés dans SQL Server sont sérialisés en tant que flux d’octets et stockés dans une colonne VARBINARY (MAX) dans une table de base de données. Une fois que le modèle est créé, entraîné, sérialisé et enregistré dans une base de données, il peut être appelé par d’autres procédures ou par la fonction [PREDICT T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) dans les charges de travail de scoring.

1. Exécutez le script suivant pour exécuter la procédure. L’instruction spécifique pour exécuter une procédure stockée est `EXECUTE` sur la quatrième ligne.

   Ce script particulier supprime un modèle existant portant le même nom (« Naive Bayes ») afin de libérer de l’espace pour les nouveaux modèles créés en réexécutant la même procédure. Si vous ne supprimez pas le modèle, une erreur se produit indiquant que l’objet existe déjà. Le modèle est stocké dans une table nommée **iris_models**, approvisionnée lorsque vous avez créé la base de données **irissql**.

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes'
    EXECUTE generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

1. Vérifiez que le modèle a été inséré.

    ```sql
    SELECT * FROM dbo.iris_models
    ```

    **Résultats**

    | model_name  | model |
    |---|-----------------|
    | Naive Bayes | 0x800363736B6C6561726E2E6E616976655F62617965730A... | 

## <a name="create-and-execute-a-stored-procedure-for-generating-predictions"></a>Créer et exécuter une procédure stockée pour générer des prédictions

Maintenant que vous avez créé, entraîné et enregistré un modèle, passez à l’étape suivante, à savoir, la création d’une procédure stockée qui génère des prédictions. Pour ce faire, appelez `sp_execute_external_script` pour exécuter un script Python qui charge le modèle sérialisé et lui attribue de nouvelles entrées de données à évaluer.

1. Exécutez le code suivant pour créer la procédure stockée qui effectue le scoring. Au moment de l’exécution, cette procédure charge un modèle binaire, utilise les colonnes `[1,2,3,4]` comme entrées et définit les colonnes `[0,5,6]` comme sortie.

   ```sql
   CREATE PROCEDURE predict_species (@model VARCHAR(100))
   AS
   BEGIN
       DECLARE @nb_model VARBINARY(max) = (
               SELECT model
               FROM iris_models
               WHERE model_name = @model
               );
   
       EXECUTE sp_execute_external_script @language = N'Python'
           , @script = N'
   import pickle
   irismodel = pickle.loads(nb_model)
   species_pred = irismodel.predict(iris_data[["Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width"]])
   iris_data["PredictedSpecies"] = species_pred
   OutputDataSet = iris_data[["id","SpeciesId","PredictedSpecies"]] 
   print(OutputDataSet)
   '
           , @input_data_1 = N'select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
           , @input_data_1_name = N'iris_data'
           , @params = N'@nb_model varbinary(max)'
           , @nb_model = @nb_model
       WITH RESULT SETS((
                   "id" INT
                 , "SpeciesId" INT
                 , "SpeciesId.Predicted" INT
                   ));
   END;
   GO
   ```

2. Exécutez la procédure stockée en attribuant le nom de modèle « Naive Bayes » afin que la procédure sache quel modèle utiliser.

   ```sql
   EXECUTE predict_species 'Naive Bayes';
   GO
   ```

   Lorsque vous exécutez la procédure stockée, elle retourne un data.frame Python. Cette ligne de T-SQL spécifie le schéma pour les résultats retournés : `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`. Vous pouvez insérer les résultats dans une nouvelle table ou les retourner à une application.

   ![Jeu de résultats issu de l’exécution de la procédure stockée](media/train-score-using-python-NB-model-results.png)

   Les résultats correspondent à 150 prédictions sur les espèces de fleurs en utilisant des caractéristiques florales en entrée. Pour la majorité des observations, l’espèce prédite correspond à l’espèce réelle.

   Cet exemple a été simplifié, car il n’utilise que le jeu de données Iris de Python pour l’apprentissage et le scoring. L’approche classique consisterait à exécuter une requête SQL pour obtenir les nouvelles données, puis à les transmettre dans Python en tant que `InputDataSet`.

## <a name="conclusion"></a>Conclusion

Dans cet exercice, vous avez appris à créer des procédures stockées dédiées à différentes tâches, où chaque procédure stockée a utilisé la procédure stockée du système `sp_execute_external_script` pour démarrer un processus Python. Les entrées du processus Python sont transmises à `sp_execute_external` en tant que paramètres. Le script Python lui-même ainsi que les variables de données d’une base de données SQL Server sont transmis en tant qu’entrées.

Il est recommandé de n’utiliser Azure Data Studio qu’avec un code Python optimisé, ou un code Python simple qui retourne une sortie sous forme de lignes. En tant qu’outil, Azure Data Studio prend en charge les langages de requête comme T-SQL et retourne des ensembles de lignes aplatis. Si votre code génère une sortie graphique comme un nuage de points ou un histogramme, vous devez utiliser un outil ou une application d’utilisateur final distincts pour restituer l’image en dehors de la procédure stockée.

Pour certains développeurs Python qui sont habitués à écrire des scripts de gestion complets qui gèrent une plage d’opérations, l’organisation des tâches dans des procédures distinctes peut sembler inutile. Mais l’apprentissage et le scoring ont des cas d’usage différents. En les séparant, vous pouvez placer chaque tâche sur une planification différente et octroyer des autorisations différentes à chaque opération.

De même, vous pouvez également exploiter les fonctionnalités d’allocation des ressources de SQL Server, comme le traitement parallèle, la gouvernance des ressources, ou écrire votre script de manière à utiliser des algorithmes dans [microsoftml](../python/ref-py-microsoftml.md) qui prend en charge la diffusion en continu et l’exécution en parallèle. En séparant l’apprentissage et le scoring, vous pouvez optimiser certaines charges de travail spécifiques.

Au final, l’un des avantages est que les processus peuvent être modifiés à l’aide de paramètres. Dans cet exercice, le code Python qui a créé le modèle (nommé « Naive Bayes » dans cet exemple) a été transmis comme entrée à une deuxième procédure stockée qui appelle le modèle dans un processus de scoring. Cet exercice n’utilise qu’un seul modèle, mais il n’est pas difficile d’imaginer comment le paramétrage de ce modèle dans une tâche de scoring pourrait rendre ce script plus utile.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les tutoriels pour Python avec le Machine Learning SQL, consultez :

- [Didacticiels Python](python-tutorials.md)
