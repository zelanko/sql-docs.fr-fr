---
title: Démarrage rapide pour les modèles Python pour l’apprentissage et les prédictions à l’aide de procédures stockées
description: Incorporez du code python dans SQL Server procédures stockées pour créer, former et utiliser un modèle Python avec le jeu de données Iris classique. Enregistrer un modèle formé dans SQL Server, puis l’utiliser pour générer des résultats prédits.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: c2c36c5aa81da098064885fd5b006d78494cd962
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345765"
---
# <a name="quickstart-create-train-and-use-a-python-model-with-stored-procedures-in-sql-server"></a>Démarrage rapide : Créer, former et utiliser un modèle Python avec des procédures stockées dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce guide de démarrage rapide à l’aide de Python, vous allez créer et exécuter deux procédures stockées. La première utilise le jeu de données de la fleur Iris classique et génère un modèle Naïve Bayes pour prédire une espèce iris en fonction des caractéristiques de la fleur. La deuxième procédure concerne la notation. Elle appelle le modèle généré dans la première procédure pour générer un ensemble de prédictions. En plaçant le code dans une procédure stockée, les opérations sont contenues, réutilisables et pouvant être appelées par d’autres procédures stockées et applications clientes. 

En suivant ce guide de démarrage rapide, vous allez apprendre à:

> [!div class="checklist"]
> * Comment incorporer du code python dans une procédure stockée
> * Comment passer des entrées à votre code via des entrées sur la procédure stockée
> * Comment les procédures stockées sont utilisées pour rendre les modèles opérationnels

## <a name="prerequisites"></a>Prérequis

Un démarrage rapide précédent, [Vérifiez que Python existe dans SQL Server](quickstart-python-verify.md), fournit des informations et des liens pour configurer l’environnement python requis pour ce guide de démarrage rapide.

Les exemples de données utilisés dans cet exercice sont la base de données [**irissql**](demo-data-iris-in-sql.md) .

## <a name="create-a-stored-procedure-that-generates-models"></a>Créer une procédure stockée qui génère des modèles

Un modèle courant dans le développement de SQL Server consiste à organiser les opérations programmables en procédures stockées distinctes. Dans cette étape, vous allez créer une procédure stockée qui génère un modèle pour prédire les résultats. 

1. Ouvrez une nouvelle fenêtre de requête dans Management Studio, connectée à la base de données **irissql** . 

    ```sql
    USE irissql
    GO
    ```

2. Copiez dans le code suivant pour créer une nouvelle procédure stockée. 

   Une fois exécutée, cette procédure appelle [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) pour démarrer une session Python. 
   
   Les entrées nécessaires à votre code python sont transmises en tant que paramètres d’entrée sur cette procédure stockée. La sortie sera un modèle formé, basé sur la bibliothèque python **scikit-Learn** pour l’algorithme machine learning. 

   Ce code utilise [**Pickle**](https://docs.python.org/2/library/pickle.html) pour sérialiser le modèle. Le modèle est formé à l’aide des données des colonnes de 0 à 4 de la table **iris_data** . 
   
   Les paramètres que vous voyez dans la deuxième partie de la procédure articulent les entrées de données et les sorties de modèle. Autant que possible, vous souhaitez que le code Python qui s’exécute dans une procédure stockée ait clairement défini les entrées et les sorties qui mappent aux entrées de procédure stockée et aux sorties passées au moment de l’exécution. 

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python',
    @script = N'
    import pickle
    from sklearn.naive_bayes import GaussianNB
    GNB = GaussianNB()
    trained_model = pickle.dumps(GNB.fit(iris_data[[0,1,2,3]], iris_data[[4]].values.ravel()))
    '
    , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@trained_model varbinary(max) OUTPUT'
    , @trained_model = @trained_model OUTPUT;
    END;
    GO
    ```

3. Vérifiez que la procédure stockée existe. 

   Si le script T-SQL de l’étape précédente s’est exécuté sans erreur, une nouvelle procédure stockée appelée **generate_iris_model** est créée et ajoutée à la base de données **irissql** . Vous pouvez trouver des procédures stockées dans l' **Explorateur d’objets**de Management Studio, sous Programmabilité.

## <a name="execute-the-procedure-to-create-and-train-models"></a>Exécuter la procédure pour créer et former des modèles

Dans cette étape, exécutez la procédure pour exécuter le code incorporé, en créant un modèle formé et sérialisé en tant que sortie. Les modèles qui sont stockés pour être réutilisés dans SQL Server sont sérialisés en tant que flux d’octets et stockés dans une colonne VARBINARY (MAX) dans une table de base de données. Une fois le modèle créé, formé, sérialisé et enregistré dans une base de données, il peut être appelé par d’autres procédures ou par la fonction [T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) de prédiction dans les charges de travail de notation.

1. Copiez le code suivant pour exécuter la procédure. L’instruction spécifique pour l’exécution d’une procédure stockée se trouve `EXEC` sur la cinquième ligne.

   Ce script particulier supprime un modèle existant portant le même nom («Naive Bayes») afin de libérer de l’espace pour les nouveaux modèles créés en réexécutant la même procédure. Sans la suppression du modèle, une erreur se produit indiquant que l’objet existe déjà. Le modèle est stocké dans une table appelée **iris_models**, approvisionnée lorsque vous avez créé la base de données **irissql** .

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes'
    EXEC generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

2. Vérifier que le modèle a été inséré une autre façon de retourner une liste de modèles est

    ```sql
    SELECT * FROM dbo.iris_models
    ```

    **Résultats**

    | nom_modèle  | model |
    |---|-----------------|
    | Naive Bayes | 0x800363736B6C6561726E2E6E616976655F62617965730A... | 

## <a name="create-and-execute-a-stored-procedure-for-generating-predictions"></a>Créer et exécuter une procédure stockée pour générer des prédictions

Maintenant que vous avez créé, formé et enregistré un modèle, passez à l’étape suivante: création d’une procédure stockée qui génère des prédictions. Pour ce faire, appelez sp_execute_external_script pour démarrer Python, puis transmettez le script Python qui charge un modèle sérialisé que vous avez créé au cours de l’exercice précédent, puis attribue au score les entrées de données.

1. Exécutez le code suivant pour créer la procédure stockée qui effectue le calcul de score. Au moment de l’exécution, cette procédure chargera un modèle binaire, utilisera des colonnes `[1,2,3,4]` comme entrées et spécifiera des colonnes `[0,5,6]` comme sortie.

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

2. Exécutez la procédure stockée en attribuant le nom de modèle «Naive Bayes» afin que la procédure sache quel modèle utiliser. 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    Lorsque vous exécutez la procédure stockée, elle retourne un Data. Frame Python. Cette ligne de T-SQL spécifie le schéma pour les résultats retournés: `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`. Vous pouvez insérer les résultats dans une nouvelle table ou les renvoyer à une application.

    ![Jeu de résultats de la procédure stockée en cours d’exécution](media/train-score-using-python-NB-model-results.png)

    Les résultats sont des prédictions 150 sur les espèces utilisant des caractéristiques florales comme entrées. Pour la majorité des observations, l’espèce prédite correspond à l’espèce réelle.

    Cet exemple a été simplifié à l’aide du jeu de données python Iris pour la formation et le score. Une approche plus courante consisterait à exécuter une requête SQL pour obtenir les nouvelles données et à les transmettre en Python `InputDataSet`en tant que. 

## <a name="conclusion"></a>Conclusion

Dans cet exercice, vous avez appris à créer des procédures stockées dédiées à différentes tâches, où chaque procédure stockée utilisait la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour démarrer un processus Python. Les entrées du processus Python sont passées au script sp_execute_external en tant que paramètres. Le script Python lui-même et les variables de données d’une base de données SQL Server sont passés en tant qu’entrées.

En règle générale, vous devez uniquement prévoir l’utilisation de SSMS avec du code python soigné, ou un code python simple qui retourne une sortie basée sur des lignes. En tant qu’outil, SSMS prend en charge les langages de requête comme T-SQL et retourne les ensembles de lignes aplatis. Si votre code génère une sortie visuelle comme un nuage ou un histogramme, vous avez besoin d’un outil ou d’une application d’utilisateur final qui peut restituer l’image.

Pour certains développeurs Python qui sont utilisés pour écrire des scripts de gestion de tous les scripts inclusifs d’une série d’opérations, l’Organisation des tâches dans des procédures distinctes peut sembler inutile. Mais la formation et le score ont des cas d’utilisation différents. En les séparant, vous pouvez placer chaque tâche sur différentes autorisations de planification et d’étendue pour fonctionner.

De même, vous pouvez également tirer parti des fonctionnalités de réapprovisionnement de SQL Server, telles que le traitement parallèle, la gouvernance des ressources, ou en écrivant votre script pour utiliser des algorithmes dans [revoscalepy](../python/ref-py-revoscalepy.md) ou [microsoftml](../python/ref-py-microsoftml.md) qui prennent en charge la diffusion en continu et l’exécution en parallèle. En séparant la formation et le score, vous pouvez cibler des optimisations pour des charges de travail spécifiques.

L’un des derniers avantages est que les processus peuvent être modifiés à l’aide de paramètres. Dans cet exercice, le code Python qui a créé le modèle (nommé «Naive Bayes» dans cet exemple) a été passé comme entrée à une deuxième procédure stockée qui appelle le modèle dans un processus de notation. Cet exercice n’utilise qu’un seul modèle, mais vous pouvez imaginer comment le paramétrage du modèle dans une tâche de notation rendrait ce script plus utile.

## <a name="next-steps"></a>Étapes suivantes

Si SQL Developer est nouveau dans Python, passez en revue les étapes et les outils permettant d’utiliser le code python localement, avec la possibilité de déplacer l’exécution des sessions locales vers une instance de SQL Server distante.

> [!div class="nextstepaction"]
> [Configurez une station de travail cliente python](../python/setup-python-client-tools-sql.md).

