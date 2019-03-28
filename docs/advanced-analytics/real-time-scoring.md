---
title: Notation à l’aide de la procédure sp_rxPredict stockée - Services de SQL Server Machine Learning en temps réel
description: Générer des prédictions à l’aide de sp_rxPredict, score des entrées de données par rapport à un modèle préentraîné écrites en R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: a7e55ac47fdb28a18c8a41b3535e67fc8886cfea
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509626"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>Notation avec sp_rxPredict dans l’apprentissage de SQL Server en temps réel
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Notation utilise en temps réel la [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) système procédure stockée et les fonctionnalités d’extension CLR dans SQL Server pour des prédictions de hautes performances ou les scores dans la prévision de charges de travail. Notation en temps réel est indépendant du langage et s’exécute sans dépendances sur R ou Python exécutions. En supposant qu’un modèle créé et formé à l’aide des fonctions de Microsoft et ensuite sérialisé vers un format binaire dans SQL Server, vous pouvez utiliser la notation en temps réel pour générer les résultats prédits sur de nouvelles entrées de données sur les instances de SQL Server qui n’ont pas le module complémentaire R ou Python installé.

## <a name="how-real-time-scoring-works"></a>La notation en temps réel fonctionne

Calcul de score en temps réel est prise en charge dans SQL Server 2017 et SQL Server 2016, sur les types de modèle spécifique basées sur les fonctions RevoScaleR ou MicrosoftML tels que [rxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)[rxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Il utilise les bibliothèques C++ natives pour générer des scores, basées sur l’entrée d’utilisateur fournie à un modèle stocké dans un format binaire spécial d’apprentissage.

Car un modèle formé peut être utilisé pour calculer les scores sans avoir à appeler un runtime de langage externe, la surcharge de plusieurs processus est réduite. Cela prend en charge les performances de prédiction beaucoup plus rapides pour la notation des scénarios de production. Étant donné que les données ne quittent jamais SQL Server, résultats peuvent être générés et insérés dans une table sans aucune traduction de données entre R et SQL.

Calcul de score en temps réel est un processus en plusieurs étapes :

1. La procédure stockée qui effectue le calcul de score doit être activée sur une base par base de données.
2. Vous chargez le modèle préformé au format binaire.
3. Vous fournir de nouvelles données d’entrée à noter, lignes tabulaires ou uniques, en tant qu’entrée dans le modèle.
4. Pour générer des scores, appelez le [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql) procédure stockée.

> [!TIP]
> Pour obtenir un exemple de calcul de score en temps réel en action, consultez [fin à la fin prêt pertes sèches sur prédiction créé à l’aide de Azure HDInsight Clusters Spark et SQL Server 2016 R services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="prerequisites"></a>Prérequis

+ [Activer l’intégration de CLR SQL Server](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ [Activer la notation en temps réel](#bkmk_enableRtScoring).

+ Le modèle doit être formé à l’avance à l’aide d’une des prises en charge **rx** algorithmes. Pour R, en temps réel de notation avec `sp_rxPredict` fonctionne avec [RevoScaleR et MicrosoftML pris en charge les algorithmes](#bkmk_rt_supported_algos). Pour Python, consultez [revoscalepy et microsoftml les algorithmes pris en charge](#bkmk_py_supported_algos)

+ Sérialiser le modèle à l’aide [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) pour R, et [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour Python. Ces fonctions de sérialisation ont été optimisées pour prendre en charge rapide de notation.

+ Enregistrer le modèle à l’instance du moteur de base de données à partir duquel vous souhaitez appeler. Cette instance n’est pas nécessaire pour que l’extension de runtime R ou Python.

> [!Note]
> Calcul de score en temps réel est actuellement optimisé pour des prédictions rapides sur les petits jeux de données, allant de quelques lignes à des centaines de milliers de lignes. Jeux de données volumineuses, à l’aide de [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) peut être plus rapide.

<a name="bkmk_py_supported_algos"></a>

## <a name="supported-algorithms"></a>Algorithmes pris en charge

### <a name="python-algorithms-using-real-time-scoring"></a>Algorithmes de Python à l’aide de la notation en temps réel

+ modèles de revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) \*
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) \*
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) \*
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) \*
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) \*
  
  Modèles marquée avec \* prennent également en charge la notation native avec la fonction PREDICT.

+ modèles de microsoftml

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

### <a name="r-algorithms-using-real-time-scoring"></a>Algorithmes de R à l’aide de la notation en temps réel

+ Modèles de RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) \*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  Modèles marquée avec \* prennent également en charge la notation native avec la fonction PREDICT.

+ Modèles de MicrosoftML

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

Calcul de score en temps réel n’utilise pas un interpréteur ; Par conséquent, toutes les fonctionnalités qui peuvent nécessiter un interpréteur ne sont pas pris en charge lors de l’étape de calcul de score.  Il peut s’agir :

  + Modèles à l’aide de la `rxGlm` ou `rxNaiveBayes` algorithmes ne sont pas pris en charge.

  + À l’aide d’une fonction de transformation ou d’une formule qui contient une transformation, tels que les modèles <code>A ~ log(B)</code> ne sont pas pris en charge dans les scores en temps réel. Pour utiliser un modèle de ce type, nous vous recommandons d’effectuer la transformation sur les données d’entrée avant de transmettre les données de notation en temps réel.


## <a name="example-sprxpredict"></a>Exemple : sp_rxPredict

Cette section décrit les étapes requises pour configurer **en temps réel** prédiction et fournit un exemple dans R de l’appel de la fonction à partir de T-SQL.

<a name ="bkmk_enableRtScoring"></a> 

### <a name="step-1-enable-the-real-time-scoring-procedure"></a>Étape 1. Activer la procédure de calcul de score en temps réel

Vous devez activer cette fonctionnalité pour chaque base de données que vous souhaitez utiliser pour calculer les scores. L’administrateur du serveur doit exécuter l’utilitaire de ligne de commande, RegisterRExt.exe, qui est inclus dans le package RevoScaleR.

> [!NOTE]
> Pour calculer les scores en temps réel pour fonctionner, les fonctionnalités SQL CLR doit être activés dans l’instance ; en outre, la base de données doit être marquée comme digne de confiance. Lorsque vous exécutez le script, ces actions sont effectuées pour vous. Toutefois, prendre en compte les implications de sécurité supplémentaires avant de faire cela !

1. Ouvrez une invite de commandes avec élévation de privilèges et accédez au dossier où se trouve RegisterRExt.exe. Le chemin d’accès suivant peut être utilisé dans une installation par défaut :
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Exécutez la commande suivante, en remplaçant le nom de votre instance et de la base de données cible dans lequel vous souhaitez activer les procédures stockées étendues :

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Par exemple, pour ajouter la procédure stockée étendue à la base de données CLRPredict sur l’instance par défaut, tapez :

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Le nom d’instance est facultatif si la base de données se trouve sur l’instance par défaut. Si vous utilisez une instance nommée, vous devez spécifier le nom d’instance.

3. RegisterRExt.exe crée les objets suivants :

    + Assemblys de confiance
    + La procédure stockée `sp_rxPredict`
    + Un nouveau rôle de base de données, `rxpredict_users`. L’administrateur de base de données peut utiliser ce rôle pour accorder l’autorisation aux utilisateurs qui utilisent la fonctionnalité de calcul de score en temps réel.

4. Ajouter des utilisateurs qui doivent exécuter `sp_rxPredict` au nouveau rôle.

> [!NOTE]
> 
> Dans SQL Server 2017, les mesures de sécurité supplémentaires sont en place pour éviter les problèmes avec l’intégration du CLR. Ces mesures imposent des restrictions supplémentaires sur l’utilisation de cette procédure stockée également. 

### <a name="step-2-prepare-and-save-the-model"></a>Étape 2. Préparer et enregistrer le modèle

Le format binaire requis par sp\_rxPredict est le même que le format requis pour utiliser la fonction PREDICT. Par conséquent, dans votre code R, incluez un appel à [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)et veillez à spécifier `realtimeScoringOnly = TRUE`, comme dans cet exemple :

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Étape 3. Appel sp_rxPredict

Vous appelez sp\_rxPredict en tant que vous le feriez pour n’importe quel autre procédure stockée. Dans la version actuelle, la procédure stockée accepte uniquement deux paramètres :  _\@modèle_ pour le modèle au format binaire, et  _\@inputData_ pour les données à utiliser dans le calcul de score, défini en tant que une requête SQL valide.

Étant donné que le format binaire est le même que celui utilisé par la fonction PREDICT, vous pouvez utiliser la table de données et des modèles à partir de l’exemple précédent.

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
> L’appel à sp\_rxPredict échoue si les données d’entrée pour calculer les scores n’incluant pas les colonnes qui correspondent à la configuration requise du modèle. Actuellement, seuls les types de données de .NET suivants sont pris en charge : double, float, short, ushort, long, ulong et chaîne.
> 
> Par conséquent, vous devrez peut-être filtrer les types non pris en charge dans vos données d’entrée avant de l’utiliser pour calculer les scores en temps réel.
> 
> Pour plus d’informations sur les types SQL correspondants, consultez [le mappage de Type SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) ou [mappage des données de paramètre CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Désactiver le calcul de score en temps réel

Pour désactiver les fonctionnalités de calcul de score en temps réel, ouvrez une invite de commandes avec élévation de privilèges et exécutez la commande suivante : `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir un exemple de comment rxPredict peut être utilisé pour calculer les scores, consultez [fin à la fin prêt pertes sèches sur prédiction créé à l’aide de Azure HDInsight Clusters Spark et SQL Server 2016 R services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/).

Pour plus d’informations sur la notation dans SQL Server, consultez [comment générer des prédictions dans l’apprentissage de SQL Server](r/how-to-do-realtime-scoring.md).
