---
title: Notation en temps réel à l’aide de la procédure stockée sp_rxPredict
description: Générer des prédictions à l’aide de sp_rxPredict, notation des entrées de données par rapport à un modèle pré-formé écrit en R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 2e9c9353acdc0a2641203788c8e4883a9accb021
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345680"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>Notation en temps réel avec sp_rxPredict dans SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

La notation en temps réel utilise la procédure stockée système [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) et les fonctionnalités d’extension CLR dans SQL Server pour les prédictions hautes performances ou les scores dans les charges de travail de prévision. La notation en temps réel est indépendante du langage et s’exécute sans dépendances sur les temps d’exécution R ou python. En supposant qu’un modèle a été créé et formé à l’aide des fonctions Microsoft, puis sérialisé au format binaire dans SQL Server, vous pouvez utiliser le score en temps réel pour générer des résultats prédits sur de nouvelles entrées de données sur des instances de SQL Server qui n’ont pas le module complémentaire R ou python ordinateur.

## <a name="how-real-time-scoring-works"></a>Fonctionnement de la notation en temps réel

La notation en temps réel est prise en charge dans SQL Server 2017 et SQL Server 2016, sur des types de modèles spécifiques basés sur des fonctions RevoScaleR ou MicrosoftML comme [rxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)[rxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Il utilise des C++ bibliothèques natives pour générer des scores en fonction de l’entrée utilisateur fournie à un modèle de machine learning stocké dans un format binaire spécial.

Étant donné qu’un modèle formé peut être utilisé pour le calcul de score sans avoir à appeler un Runtime de langage externe, la charge de traitement de plusieurs processus est réduite. Cela prend en charge des performances de prédiction beaucoup plus rapides pour les scénarios de calcul de score de production. Étant donné que les données ne quittent jamais SQL Server, les résultats peuvent être générés et insérés dans une nouvelle table sans aucune traduction de données entre R et SQL.

La notation en temps réel est un processus à plusieurs étapes:

1. La procédure stockée qui effectue un calcul de score doit être activée pour chaque base de données.
2. Vous chargez le modèle pré-formé au format binaire.
3. Vous fournissez de nouvelles données d’entrée à noter, qu’il s’agisse de lignes tabulaires ou uniques, en tant qu’entrée dans le modèle.
4. Pour générer des scores, appelez la procédure stockée [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) .

## <a name="prerequisites"></a>Prérequis

+ [Activez SQL Server l’intégration du CLR](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ [Activez la notation en temps réel](#bkmk_enableRtScoring).

+ Le modèle doit être formé à l’avance à l’aide de l’un des algorithmes **RX** pris en charge. Pour R, la notation en temps réel `sp_rxPredict` avec fonctionne avec les [algorithmes pris en charge par RevoScaleR et MicrosoftML](#bkmk_rt_supported_algos). Pour Python, consultez [algorithmes pris en charge par revoscalepy et microsoftml](#bkmk_py_supported_algos)

+ Sérialisez le modèle à l’aide de [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) pour R et [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour Python. Ces fonctions de sérialisation ont été optimisées pour prendre en charge la notation rapide.

+ Enregistrez le modèle dans l’instance du moteur de base de données à partir de laquelle vous souhaitez l’appeler. Cette instance ne doit pas obligatoirement avoir l’extension de Runtime R ou python.

> [!Note]
> La notation en temps réel est actuellement optimisée pour des prédictions rapides sur des jeux de données plus petits, allant de quelques lignes à des centaines de milliers de lignes. Sur les jeux de données volumineux, l’utilisation de [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) peut être plus rapide.

<a name="bkmk_py_supported_algos"></a>

## <a name="supported-algorithms"></a>Algorithmes pris en charge

### <a name="python-algorithms-using-real-time-scoring"></a>Algorithmes python utilisant le score en temps réel

+ modèles revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) \*
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) \*
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) \*
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) \*
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) \*
  
  Les modèles marqués \* avec prennent également en charge la notation native avec la fonction Predict.

+ modèles microsoftml

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

### <a name="r-algorithms-using-real-time-scoring"></a>Algorithmes R utilisant le score en temps réel

+ Modèles RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)\*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  Les modèles marqués \* avec prennent également en charge la notation native avec la fonction Predict.

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

La notation en temps réel n’utilise pas d’interpréteur; par conséquent, toute fonctionnalité qui peut nécessiter un interpréteur n’est pas prise en charge pendant l’étape de notation.  Il peut s’agir des éléments suivants:

  + Les modèles utilisant `rxGlm` les `rxNaiveBayes` algorithmes ou ne sont pas pris en charge.

  + Les modèles qui utilisent une fonction de transformation ou une formule contenant une <code>A ~ log(B)</code> transformation, tels que, ne sont pas pris en charge dans le calcul de score en temps réel. Pour utiliser un modèle de ce type, nous vous recommandons d’effectuer la transformation sur les données d’entrée avant de passer les données à la notation en temps réel.


## <a name="example-sprxpredict"></a>Exemple: sp_rxPredict

Cette section décrit les étapes requises pour configurer la prédiction **en temps réel** et fournit un exemple dans R sur la façon d’appeler la fonction à partir de T-SQL.

<a name ="bkmk_enableRtScoring"></a> 

### <a name="step-1-enable-the-real-time-scoring-procedure"></a>Étape 1. Activer la procédure de notation en temps réel

Vous devez activer cette fonctionnalité pour chaque base de données que vous souhaitez utiliser pour la notation. L’administrateur du serveur doit exécuter l’utilitaire de ligne de commande, RegisterRExt. exe, qui est inclus dans le package RevoScaleR.

> [!NOTE]
> Pour que le calcul des scores en temps réel fonctionne, la fonctionnalité CLR SQL doit être activée dans l’instance de. en outre, la base de données doit être marquée comme digne de confiance. Lorsque vous exécutez le script, ces actions sont effectuées pour vous. Toutefois, tenez compte des implications de sécurité supplémentaires.

1. Ouvrez une invite de commandes avec élévation de privilèges, puis accédez au dossier où se trouve RegisterRExt. exe. Le chemin d’accès suivant peut être utilisé dans une installation par défaut:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Exécutez la commande suivante, en remplaçant le nom de votre instance et la base de données cible dans laquelle vous souhaitez activer les procédures stockées étendues:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Par exemple, pour ajouter la procédure stockée étendue à la base de données CLRPredict sur l’instance par défaut, tapez:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Le nom de l’instance est facultatif si la base de données se trouve sur l’instance par défaut. Si vous utilisez une instance nommée, vous devez spécifier le nom de l’instance.

3. RegisterRExt. exe crée les objets suivants:

    + Assemblys approuvés
    + Procédure stockée`sp_rxPredict`
    + Nouveau rôle de base de `rxpredict_users`données,. L’administrateur de base de données peut utiliser ce rôle pour accorder des autorisations aux utilisateurs qui utilisent la fonctionnalité de notation en temps réel.

4. Ajoutez tous les utilisateurs qui doivent s' `sp_rxPredict` exécuter sur le nouveau rôle.

> [!NOTE]
> 
> Dans SQL Server 2017, des mesures de sécurité supplémentaires sont en place pour éviter les problèmes liés à l’intégration du CLR. Ces mesures imposent également des restrictions supplémentaires sur l’utilisation de cette procédure stockée. 

### <a name="step-2-prepare-and-save-the-model"></a>Étape 2. Préparer et enregistrer le modèle

Le format binaire requis par SP\_rxPredict est le même que celui requis pour utiliser la fonction Predict. Par conséquent, dans votre code R, incluez un appel à [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)et veillez à `realtimeScoringOnly = TRUE`spécifier, comme dans cet exemple:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Étape 3. Appeler sp_rxPredict

Vous appelez SP\_rxPredict comme vous le feriez pour toute autre procédure stockée. Dans la version actuelle, la procédure stockée ne prend que deux paramètres:  _\@Model_ pour le modèle au format binaire, et  _\@inputData_ pour les données à utiliser dans le calcul de score, défini en tant que requête SQL valide.

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
> L’appel à SP\_rxPredict échoue si les données d’entrée pour le score n’incluent pas les colonnes qui correspondent aux exigences du modèle. Actuellement, seuls les types de données .NET suivants sont pris en charge: double, float, Short, ushort, long, ULONG et String.
> 
> Par conséquent, vous devrez peut-être filtrer les types non pris en charge dans vos données d’entrée avant de les utiliser pour une notation en temps réel.
> 
> Pour plus d’informations sur les types SQL correspondants, consultez [mappage de type SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) ou [mappage de données de paramètres CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Désactiver la notation en temps réel

Pour désactiver la fonctionnalité de notation en temps réel, ouvrez une invite de commandes avec élévation de privilèges et exécutez la commande suivante:`RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le calcul des scores dans SQL Server, consultez [Comment générer des prédictions dans SQL Server machine learning](r/how-to-do-realtime-scoring.md).
