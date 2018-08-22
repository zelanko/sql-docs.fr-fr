---
title: Calcul de score en temps réel dans l’apprentissage de SQL Server | Microsoft Docs
description: Générer des prédictions à l’aide de sp_rxPredict, notation entrées dta par rapport à un modèle préentraîné écrites en R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d5a3d0318f925918ef98ae18744e4287d6b81108
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2018
ms.locfileid: "40394296"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>Notation avec sp_rxPredict dans l’apprentissage de SQL Server en temps réel
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment score dans fonctionne quasiment en temps réel pour les données relationnelles SQL Server, à l’aide d’apprentissage modélise écrite dans R. 

> [!Note]
> Notation native est une implémentation spéciale de notation en temps réel qui utilise la fonction native prédire de T-SQL pour calculer les scores très rapide. Pour plus d’informations et de disponibilité, consultez [notation Native](sql-native-scoring.md).

## <a name="how-real-time-scoring-works"></a>La notation en temps réel fonctionne

Calcul de score en temps réel est prise en charge dans SQL Server 2017 et SQL Server 2016, sur les types de modèle spécifique basées sur les fonctions RevoScaleR ou MicrosoftML tels que [rxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) ou [rxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Il utilise les bibliothèques C++ natives pour générer des scores, basées sur l’entrée d’utilisateur fournie à un modèle stocké dans un format binaire spécial d’apprentissage.

Car un modèle formé peut être utilisé pour calculer les scores sans avoir à appeler un runtime de langage externe, la surcharge de plusieurs processus est réduite. Cela prend en charge les performances de prédiction beaucoup plus rapides pour la notation des scénarios de production. Étant donné que les données ne quittent jamais SQL Server, résultats peuvent être générés et insérés dans une table sans aucune traduction de données entre R et SQL.

Calcul de score en temps réel est un processus en plusieurs étapes :

1. La procédure stockée qui effectue le calcul de score doit être activée sur une base par base de données.
2. Vous chargez le modèle préformé au format binaire.
3. Vous fournissez de nouvelles données d’entrée, les lignes tabulaires ou uniques, en tant qu’entrée dans le modèle.
4. Pour générer des scores, appelez la procédure stockée de sp_rxPredict.

## <a name="get-started"></a>Bien démarrer

Pour plus d’exemples de code et des instructions, consultez [comment effectuer la notation native ou la notation en temps réel](r/how-to-do-realtime-scoring.md).

Pour obtenir un exemple de comment rxPredict peut être utilisé pour calculer les scores, consultez [fin à la fin prêt pertes sèches sur prédiction créé à l’aide de Azure HDInsight Clusters Spark et SQL Server 2016 R services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> Si vous travaillez exclusivement dans le code R, vous pouvez également utiliser le [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) fonction pour calculer les scores rapide.

## <a name="requirements"></a>Spécifications

Calcul de score en temps réel est prise en charge sur ces plateformes :

+ SQL Server 2017 Machine Learning Services
+ SQL Server R Services 2016, avec une mise à niveau des composants R vers 9.1.0). ou version ultérieure

Sur SQL Server, vous devez activer la fonctionnalité de calcul de score en temps réel à l’avance ajouter les bibliothèques basé sur CLR pour SQL Server.

Pour plus d’informations concernant la notation en temps réel dans un environnement distribué basé sur Microsoft R Server, reportez-vous à la [publishService](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice) fonction disponible dans le [package mrsDeploy](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package), qui prend en charge publication de modèles de notation en temps réel sous forme de nouveau un service web s’exécutant sur R Server.

### <a name="restrictions"></a>Restrictions

+ Le modèle doit être formé à l’avance à l’aide d’une des prises en charge **rx** algorithmes. Pour plus d’informations, consultez [pris en charge les algorithmes](#bkmk_rt_supported_algos). Notation en temps réel avec `sp_rxPredict` prend en charge des algorithmes RevoScaleR et MicrosoftML.

+ Le modèle doit être enregistré à l’aide des nouvelles fonctions de sérialisation : [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) pour R, et [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour Python. Ces fonctions de sérialisation ont été optimisées pour prendre en charge rapide de notation.

+ Calcul de score en temps réel n’utilise pas un interpréteur ; Par conséquent, toutes les fonctionnalités qui peuvent nécessiter un interpréteur ne sont pas pris en charge lors de l’étape de calcul de score.  Il peut s’agir :

  + Modèles à l’aide de la `rxGlm` ou `rxNaiveBayes` algorithmes ne sont pas actuellement pris en charge

  + Modèles de RevoScaleR qui utilisent une fonction de transformation de R, ou une formule qui contient une transformation, tel que <code>A ~ log(B)</code> ne sont pas pris en charge dans les scores en temps réel. Pour utiliser un modèle de ce type, nous vous recommandons d’effectuer la transformation sur le pour entrer des données avant de transmettre les données de notation en temps réel.

+ Calcul de score en temps réel est actuellement optimisé pour des prédictions rapides sur les petits jeux de données, allant de quelques lignes à des centaines de milliers de lignes. Jeux de données volumineuses, à l’aide de [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) peut être plus rapide.

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-real-time-scoring"></a><a name="bkmk_rt_supported_algos">Algorithmes qui prennent en charge la notation en temps réel

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

Calcul de score en temps réel n’est pas pris en charge pour les transformations de R différente de celles répertoriées explicitement dans la section précédente. 

Pour les développeurs habitués à travailler avec RevoScaleR et d’autres bibliothèques propres à Microsoft R, les fonctions non prises en charge incluent `rxGlm` ou `rxNaiveBayes` algorithmes dans RevoScaleR, les modèles PMML et d’autres modèles créés à l’aide d’autres bibliothèques R à partir de CRAN ou autres référentiels.

### <a name="known-issues"></a>Problèmes connus

+ `sp_rxPredict` Retourne un message incorrect quand une valeur NULL est passée en tant que le modèle : « System.Data.SqlTypes.SqlNullValueException:Data dans Null ».

## <a name="next-steps"></a>Étapes suivantes

[Comment effectuer la notation en temps réel](r/how-to-do-realtime-scoring.md)
