---
title: Créer et évaluer un modèle prédictif dans python
titleSuffix: SQL Server Machine Learning Services
description: Créez un modèle prédictif simple dans Python à l’aide de SQL Server Machine Learning Services, puis prédictionez un résultat à l’aide de nouvelles données.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/14/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cb564d7dc8564b31a90a09f53aedaba953519f76
ms.sourcegitcommit: c7a202af70fd16467a498688d59637d7d0b3d1f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72313666"
---
# <a name="quickstart-create-and-score-a-predictive-model-in-python-with-sql-server-machine-learning-services"></a>Démarrage rapide : Créer et évaluer un modèle prédictif dans Python avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous allez créer et effectuer l’apprentissage d’un modèle prédictif à l’aide de Python, enregistrer le modèle dans une table de votre instance de SQL Server, puis utiliser le modèle pour prédire des valeurs à partir de nouvelles données à l’aide d' [SQL Server machine learning services](../what-is-sql-server-machine-learning.md).

Vous allez créer et exécuter deux procédures stockées qui s’exécutent dans SQL. La première utilise le jeu de données de la fleur Iris classique et génère un modèle Naïve Bayes pour prédire une espèce iris en fonction des caractéristiques de la fleur. La deuxième procédure concerne la notation : elle appelle le modèle généré dans la première procédure pour générer un ensemble de prédictions en fonction de nouvelles données. En plaçant le code dans une procédure stockée, les opérations sont contenues, réutilisables et pouvant être appelées par d’autres procédures stockées et applications clientes.

En suivant ce guide de démarrage rapide, vous apprendrez à :

> [!div class="checklist"]
> - Comment incorporer du code python dans une procédure stockée
> - Comment passer des entrées à votre code via des entrées sur la procédure stockée
> - Comment les procédures stockées sont utilisées pour rendre les modèles opérationnels

## <a name="prerequisites"></a>Prérequis

- Ce guide de démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) avec le langage Python installé.

- Vous avez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts Python. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

- L’exemple de données utilisé dans cet exercice est l’exemple de données IRIS. Suivez les instructions des [données de démonstration Iris](demo-data-iris-in-sql.md) pour créer l’exemple de base de données **irissql**.

## <a name="create-a-stored-procedure-that-generates-models"></a>Créer une procédure stockée qui génère des modèles

Dans cette étape, vous allez créer une procédure stockée qui génère un modèle pour prédire les résultats.

1. Ouvrez une nouvelle fenêtre de requête dans SSMS connectée à la base de données **irissql** . 

    ```sql
    USE irissql
    GO
    ```

1. Copiez dans le code suivant pour créer une nouvelle procédure stockée.

   Une fois exécutée, cette procédure appelle [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour démarrer une session Python. 
   
   Les entrées nécessaires à votre code python sont transmises en tant que paramètres d’entrée sur cette procédure stockée. La sortie sera un modèle formé, basé sur la bibliothèque python **scikit-Learn** pour l’algorithme machine learning. 

   Ce code utilise [**Pickle**](https://docs.python.org/2/library/pickle.html) pour sérialiser le modèle. Le modèle est formé à l’aide des données des colonnes de 0 à 4 de la table **iris_data** . 
   
   Les paramètres que vous voyez dans la deuxième partie de la procédure articulent les entrées de données et les sorties de modèle. Autant que possible, vous souhaitez que le code Python qui s’exécute dans une procédure stockée ait clairement défini les entrées et les sorties qui mappent aux entrées de procédure stockée et aux sorties passées au moment de l’exécution.

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

   Si le script T-SQL de l’étape précédente s’est exécuté sans erreur, une nouvelle procédure stockée appelée **generate_iris_model** est créée et ajoutée à la base de données **irissql** . Vous pouvez trouver des procédures stockées dans l' **Explorateur d’objets**SSMS, sous **programmabilité**.

## <a name="execute-the-procedure-to-create-and-train-models"></a>Exécuter la procédure pour créer et former des modèles

Dans cette étape, vous exécutez la procédure pour exécuter le code incorporé, en créant un modèle formé et sérialisé en tant que sortie. 

Les modèles qui sont stockés pour être réutilisés dans SQL Server sont sérialisés en tant que flux d’octets et stockés dans une colonne VARBINARY (MAX) dans une table de base de données. Une fois le modèle créé, formé, sérialisé et enregistré dans une base de données, il peut être appelé par d’autres procédures ou par la fonction [T-SQL de prédiction](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) dans les charges de travail de notation.

1. Exécutez le script suivant pour exécuter la procédure. L’instruction spécifique pour l’exécution d’une procédure stockée est `EXECUTE` sur la quatrième ligne.

   Ce script particulier supprime un modèle existant portant le même nom (« Naive Bayes ») afin de libérer de l’espace pour les nouveaux modèles créés en réexécutant la même procédure. Sans la suppression du modèle, une erreur se produit indiquant que l’objet existe déjà. Le modèle est stocké dans une table appelée **iris_models**, approvisionnée lorsque vous avez créé la base de données **irissql** .

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

    | nom_modèle  | model |
    |---|-----------------|
    | Naive Bayes | 0x800363736B6C6561726E2E6E616976655F62617965730A... | 

## <a name="create-and-execute-a-stored-procedure-for-generating-predictions"></a>Créer et exécuter une procédure stockée pour générer des prédictions

Maintenant que vous avez créé, formé et enregistré un modèle, passez à l’étape suivante : création d’une procédure stockée qui génère des prédictions. Pour ce faire, appelez `sp_execute_external_script` pour exécuter un script Python qui charge le modèle sérialisé et lui donne de nouvelles entrées de données à noter.

1. Exécutez le code suivant pour créer la procédure stockée qui effectue le calcul de score. Au moment de l’exécution, cette procédure chargera un modèle binaire, utilisera les colonnes `[1,2,3,4]` comme entrées et spécifiera les colonnes `[0,5,6]` comme sortie.

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

2. Exécutez la procédure stockée en attribuant le nom de modèle « Naive Bayes » afin que la procédure sache quel modèle utiliser.

   ```sql
   EXECUTE predict_species 'Naive Bayes';
   GO
   ```

   Lorsque vous exécutez la procédure stockée, elle retourne un Data. Frame Python. Cette ligne de T-SQL spécifie le schéma pour les résultats retournés : `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`. Vous pouvez insérer les résultats dans une nouvelle table ou les renvoyer à une application.

   ![Jeu de résultats de la procédure stockée en cours d’exécution](media/train-score-using-python-NB-model-results.png)

   Les résultats sont des prédictions 150 sur les espèces utilisant des caractéristiques florales comme entrées. Pour la majorité des observations, l’espèce prédite correspond à l’espèce réelle.

   Cet exemple a été simplifié à l’aide du jeu de données python Iris pour la formation et le score. Une approche plus courante consisterait à exécuter une requête SQL pour obtenir les nouvelles données et à les transmettre en Python en tant que `InputDataSet`.

## <a name="conclusion"></a>Conclusion

Dans cet exercice, vous avez appris à créer des procédures stockées dédiées à différentes tâches, où chaque procédure stockée utilisait la procédure stockée système `sp_execute_external_script` pour démarrer un processus Python. Les entrées du processus Python sont passées à `sp_execute_external` en tant que paramètres. Le script Python lui-même et les variables de données d’une base de données SQL Server sont passés en tant qu’entrées.

En règle générale, vous devez uniquement prévoir l’utilisation de SSMS avec du code python soigné, ou un code python simple qui retourne une sortie basée sur des lignes. En tant qu’outil, SSMS prend en charge les langages de requête comme T-SQL et retourne les ensembles de lignes aplatis. Si votre code génère une sortie visuelle comme un nuage ou un histogramme, vous avez besoin d’un outil ou d’une application d’utilisateur final qui peut restituer l’image.

Pour certains développeurs Python qui sont utilisés pour écrire des scripts de gestion de tous les scripts inclusifs d’une série d’opérations, l’Organisation des tâches dans des procédures distinctes peut sembler inutile. Mais la formation et le score ont des cas d’utilisation différents. En les séparant, vous pouvez placer chaque tâche sur une planification et des autorisations d’étendue différentes pour chaque opération.

De même, vous pouvez également tirer parti des fonctionnalités de réapprovisionnement de SQL Server, telles que le traitement parallèle, la gouvernance des ressources, ou en écrivant votre script pour utiliser des algorithmes dans [microsoftml](../python/ref-py-microsoftml.md) qui prend en charge la diffusion en continu et l’exécution en parallèle. En séparant la formation et le score, vous pouvez cibler des optimisations pour des charges de travail spécifiques.

L’un des derniers avantages est que les processus peuvent être modifiés à l’aide de paramètres. Dans cet exercice, le code Python qui a créé le modèle (nommé « Naive Bayes » dans cet exemple) a été passé comme entrée à une deuxième procédure stockée qui appelle le modèle dans un processus de notation. Cet exercice n’utilise qu’un seul modèle, mais vous pouvez imaginer comment le paramétrage du modèle dans une tâche de notation rendrait ce script plus utile.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server Machine Learning Services, consultez :

- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
