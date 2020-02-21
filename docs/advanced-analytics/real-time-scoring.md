---
title: Scoring en temps réel à l’aide de sp_rxPredict
description: Générez des prédictions à l’aide de sp_rxPredict, une procédure stockée utilisée pour le scoring des entrées de données par rapport à un modèle préentraîné écrit en R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/26/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 746a9cadfca28aae3bd2781a3daf71aabb8d6e5b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727328"
---
# <a name="real-time-scoring-with-sp_rxpredict-in-sql-server-machine-learning"></a>Scoring en temps réel avec sp_rxPredict dans SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Le scoring en temps réel utilise la procédure stockée système [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) et les fonctionnalités d’extension du CLR dans SQL Server pour générer des scores ou des prédictions hautes performances dans les charges de travail de prévision. Le scoring en temps réel est indépendant du langage et s’exécute indépendamment des runtimes R ou Python. Supposons que vous disposiez d’un modèle qui a été créé et entraîné à l’aide de fonctions Microsoft, puis sérialisé au format binaire dans SQL Server. Vous pouvez alors utiliser le scoring en temps réel pour générer des résultats prédits sur de nouvelles entrées de données sur des instances SQL Server où le module complémentaire R ou Python n’est pas installé.

## <a name="how-real-time-scoring-works"></a>Fonctionnement du scoring en temps réel

Le scoring en temps réel est pris en charge sur des types de modèles spécifiques basés sur des fonctions RevoScaleR ou MicrosoftML, notamment [rxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) et [rxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Il utilise des bibliothèques C++ natives pour générer des scores en fonction de l’entrée utilisateur fournie à un modèle de machine learning stocké dans un format binaire spécial.

Le fait de pouvoir utiliser un modèle entraîné pour le scoring sans devoir appeler un runtime de langage externe permet de réduire la charge associée à plusieurs processus. Cela permet de générer beaucoup plus rapidement des prédictions dans les scénarios de scoring de production. Les données ne quittant jamais SQL Server, les résultats peuvent être générés et insérés dans une nouvelle table sans aucune traduction des données entre R et SQL.

Le scoring en temps réel est un processus qui comprend plusieurs étapes :

1. La procédure stockée qui effectue le scoring doit être activée pour chaque base de données.
2. Vous chargez le modèle préentraîné au format binaire.
3. Vous fournissez au modèle de nouvelles données d’entrée, au format tabulaire ou ligne unique, en vue de leur attribuer un score.
4. Pour générer des scores, appelez la procédure stockée [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql).

## <a name="prerequisites"></a>Conditions préalables requises

+ [Activer l’intégration du CLR dans SQL Server](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ [Activer le scoring en temps réel](#bkmk_enableRtScoring).

+ Le modèle doit être entraîné à l’avance à l’aide de l’un des algorithmes **rx** pris en charge. Pour R, le scoring en temps réel avec `sp_rxPredict` fonctionne avec les [algorithmes RevoScaleR et MicrosoftML pris en charge](#bkmk_rt_supported_algos). Pour Python, consultez les [algorithmes revoscalepy et microsoftml pris en charge](#bkmk_py_supported_algos).

+ Sérialisez le modèle avec [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) pour R et [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour Python. Ces fonctions de sérialisation ont été optimisées pour prendre en charge le scoring rapide.

+ Enregistrez le modèle dans l’instance du moteur de base de données à partir de laquelle vous souhaitez l’appeler. Cette instance ne doit pas nécessairement avoir l’extension de runtime R ou Python.

> [!Note]
> Le scoring en temps réel est actuellement optimisé pour générer rapidement des prédictions sur de petits jeux de données, ceux-ci allant de quelques lignes à des centaines de milliers de lignes. Sur les jeux de données volumineux, [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) peut être plus rapide.

<a name="bkmk_py_supported_algos"></a>

## <a name="supported-algorithms"></a>Algorithmes pris en charge

### <a name="python-algorithms-using-real-time-scoring"></a>Algorithmes Python utilisant le scoring en temps réel

+ Modèles revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) \*
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) \*
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) \*
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) \*
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) \*
  
  Les modèles signalés par \* prennent également en charge le scoring natif avec la fonction PREDICT.

+ Modèles microsoftml

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_net](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

+ Transformations fournies par microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)


<a name="bkmk_rt_supported_algos"></a>

### <a name="r-algorithms-using-real-time-scoring"></a>Algorithmes R utilisant le scoring en temps réel

+ Modèles RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) \*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  Les modèles signalés par \* prennent également en charge le scoring natif avec la fonction PREDICT.

+ Modèles MicrosoftML

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ Transformations fournies par MicrosoftML

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Types de modèles non pris en charge

Le scoring en temps réel n’utilisant pas d’interpréteur, toute fonctionnalité susceptible de nécessiter un interpréteur n’est pas prise en charge durant l’étape de scoring.  Par exemple :

  + Les modèles utilisant les algorithmes `rxGlm` ou `rxNaiveBayes` ne sont pas pris en charge.

  + Les modèles utilisant une fonction de transformation ou une formule contenant une transformation, comme <code>A ~ log(B)</code>, ne sont pas pris en charge dans le scoring en temps réel. Pour utiliser un modèle de ce type, nous vous recommandons d’effectuer la transformation sur les données d’entrée avant de passer les données au scoring en temps réel.


## <a name="example-sp_rxpredict"></a>Exemple : sp_rxPredict

Cette section décrit les étapes à effectuer pour configurer la prédiction **en temps réel** et montre comment appeler la fonction à partir de T-SQL à travers un exemple dans R.

<a name ="bkmk_enableRtScoring"></a> 

### <a name="step-1-enable-the-real-time-scoring-procedure"></a>Étape 1. Activer la procédure de scoring en temps réel

Vous devez activer cette fonctionnalité pour chaque base de données que vous souhaitez utiliser pour le scoring. L’administrateur du serveur doit exécuter l’utilitaire de ligne de commande, RegisterRExt.exe, qui est inclus dans le package RevoScaleR.

> [!NOTE]
> Pour que le scoring en temps réel fonctionne, la fonctionnalité CLR SQL doit être activée dans l’instance. De plus, la base de données doit être marquée comme étant digne de confiance. Quand vous exécutez le script, ces actions sont effectuées pour vous. Toutefois, tenez compte des implications supplémentaires en matière de sécurité avant de procéder.

1. Ouvrez une invite de commandes avec élévation de privilèges, puis accédez au dossier contenant RegisterRExt.exe. Le chemin suivant peut être utilisé dans une installation par défaut :
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Exécutez la commande suivante en indiquant le nom de votre instance et la base de données cible où vous souhaitez activer les procédures stockées étendues :

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Par exemple, pour ajouter la procédure stockée étendue à la base de données CLRPredict sur l’instance par défaut, tapez :

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Le nom de l’instance est facultatif si la base de données se trouve sur l’instance par défaut. Si vous utilisez une instance nommée, vous devez spécifier le nom de l’instance.

3. RegisterRExt.exe crée les objets suivants :

    + Assemblys approuvés.
    + `sp_rxPredict` (procédure stockée).
    + `rxpredict_users` (nouveau rôle de base de données). L’administrateur de base de données peut utiliser ce rôle pour accorder des autorisations aux utilisateurs qui utilisent la fonctionnalité de scoring en temps réel.

4. Ajoutez tous les utilisateurs qui doivent exécuter `sp_rxPredict` au nouveau rôle.

> [!NOTE]
> 
> Dans SQL Server 2017, des mesures de sécurité supplémentaires sont en place pour éviter les problèmes liés à l’intégration du CLR. Ces mesures imposent également des restrictions supplémentaires sur l’utilisation de cette procédure stockée. 

### <a name="step-2-prepare-and-save-the-model"></a>Étape 2. Préparer et enregistrer le modèle

Le format binaire exigé par sp\_rxPredict est le même que celui exigé pour utiliser la fonction PREDICT. Par conséquent, dans votre code R, incluez un appel à [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) en veillant à spécifier `realtimeScoringOnly = TRUE`, comme dans cet exemple :

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sp_rxpredict"></a>Étape 3. Appeler sp_rxPredict

Vous appelez sp\_rxPredict comme n’importe quelle autre procédure stockée. Dans la version actuelle, la procédure stockée n’accepte que deux paramètres : _\@model_ pour le modèle au format binaire et _\@inputData_ pour les données à utiliser dans le scoring (données définies en tant que requête SQL valide).

Étant donné que le format binaire est le même que celui utilisé par la fonction PREDICT, vous pouvez utiliser les modèles et la table de données de l’exemple précédent.

```sql
DECLARE @irismodel varbinary(max)
SELECT @irismodel = [native_model_object] from [ml_models]
WHERE model_name = 'iris.dtree' 
AND model_version = 'v1''

EXEC sp_rxPredict
@model = @irismodel,
@inputData = N'SELECT * FROM iris_rx_data'
```

> [!NOTE]
> 
> L’appel à sp\_rxPredict échoue si les données d’entrée pour le scoring n’incluent aucune colonne conforme aux exigences du modèle. Actuellement, seuls les types de données .NET suivants sont pris en charge : double, float, short, ushort, long, ulong et string.
> 
> Vous devrez donc peut-être exclure par filtrage les types non pris en charge dans vos données d’entrée avant de les utiliser pour le scoring en temps réel.
> 
> Pour plus d’informations sur les types SQL correspondants, consultez [Mappage de type SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) ou [Mappage des données de paramètres CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Désactiver le scoring en temps réel

Pour désactiver la fonctionnalité de scoring en temps réel, ouvrez une invite de commandes avec élévation de privilèges et exécutez la commande suivante : `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le scoring dans SQL Server, consultez le [guide pratique pour générer des prédictions dans SQL Server Machine Learning](r/how-to-do-realtime-scoring.md).
