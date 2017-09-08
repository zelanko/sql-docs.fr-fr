---
title: Calcul de score native | Documents Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e1cb06223e5274c1fa439eb9f7d82a005e93a47d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---

# <a name="native-scoring"></a>Calcul de score en natif

Cette rubrique décrit les fonctionnalités de SQL Server 2017 permettant de calculer les scores sur les modèles d’apprentissage automatique en temps quasi réel.

+ Qu’est natif et calculer les scores en temps réel de calcul de score
+ Fonctionnement
+ Configuration requise et plates-formes prises en charge

## <a name="what-is-native-scoring-and-how-is-it-different-from-realtime-scoring"></a>Qu’est le score natif et comment il est différent de calculer les scores en temps réel ?

Dans SQL Server 2016, Microsoft a créé une infrastructure d’extensibilité qui permet aux scripts R doit être exécuté à partir de T-SQL. Cette structure prend en charge toute opération que vous pouvez effectuer dans R, allant de simples fonctions à formation complexes d’apprentissage des modèles. Toutefois, l’architecture de double-process qui associe R avec SQL Server signifie que les processus R externes doivent être appelées pour chaque appel, quelle que soit la complexité de l’opération. Si vous chargez un modèle dont l’apprentissage d’une table et score s’y rapportant sur les données déjà présentes dans SQL Server, la charge de l’appel du processus de R externe représente un coût de performances inutiles.

_Calcul de score_ est un processus en deux étapes : un modèle dont l’apprentissage est chargé à partir d’une table et de nouvelles données d’entrée, les lignes tabulaires ou uniques, sont passées au modèle, ce qui génère les nouvelles valeurs (ou _scores_). La sortie peut être une valeur de colonne unique qui représente une probabilité ou de plusieurs valeurs, y compris un intervalle de confiance, une erreur ou autres complément utile pour la prédiction.

Lors de l’évaluation de plusieurs lignes de données, les nouvelles valeurs sont généralement insérées dans une table dans le cadre de la procédure de calcul de score.  Toutefois, vous pouvez également récupérer un score unique en temps réel. Lors de l’évaluation des entrées successives, le modèle peut être mis en cache afin qu’il peut être rechargé en mémoire rapide.

Pour prendre en charge rapide de calcul de score, Machine Learning Services SQL Server (et serveur de Microsoft Machine Learning) fournissent des bibliothèques de calcul de score intégrées qui fonctionnent dans R ou T-SQL. Il existe différentes options, selon la version que vous avez.

**Calcul de score en natif**

+ La fonction PREDICT dans Transact-SQL peut être utilisée pour _score native_ à partir de n’importe quelle instance de SQL Server 2017. Il nécessite uniquement que vous disposez d’un modèle déjà formé et enregistré dans une table ou peut être appelé via T-SQL. Il s’agit d’un type de calcul de score en temps réel qui utilise les fonctions T-SQL natives ; Aucune configuration supplémentaire n’est requise.

   Le runtime R n’est pas appelé et ne doit-elle pas être installés.

**Calculer les scores en temps réel**

+ **sp_rxPredict** est une procédure stockée pour en temps réel de calcul de score qui peut être utilisé pour générer des scores à partir de n’importe quel type de modèle pris en charge, sans appeler le runtime R.

  Cette option permet de calculer les scores en temps réel est également disponible dans SQL Server 2016, si vous mettez à niveau les composants de R à l’aide du programme d’installation autonome de Microsoft R Server. sp_rxPredict est également pris en charge dans SQL Server 2017 et peut être une bonne option si le score sur un type de modèle non pris en charge par la fonction de prédiction.

+ La fonction rxPredict peut être utilisée pour calculer les scores rapide dans du code R.

Pour l’ensemble de ces méthodes, vous devez utiliser un modèle qui a été formé à l’aide d’un des algorithmes de RevoScaleR ou MicrosoftML pris en charge.

Pour obtenir un exemple d’en temps réel de calcul de score en action, consultez [fin à la fin prêt ChargeOff prédiction créé à l’aide de Azure HDInsight Spark Clusters et le Service de SQL Server 2016 R](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="how-native-scoring-works"></a>Comment native notation fonctionne

Calcul de score natif utilise des bibliothèques natives C++ à partir de Microsoft, qui peut lire le modèle à partir d’un format binaire spécial et générer des scores. Car un modèle peut être publié et utilisé pour calculer les scores sans avoir à appeler l’interpréteur R, la surcharge de plusieurs interactions entre les processus est réduite. Il prend en charge les performances de prédiction beaucoup plus rapides dans les scénarios de production d’entreprise.

Pour générer des scores à l’aide de cette bibliothèque, vous appelez la fonction de calcul de score et passez les entrées requises suivantes :

+ Un modèle compatible. Consultez le [exigences](#Requirements) pour plus d’informations.
+ Données d’entrée, généralement définies comme une requête SQL

La fonction renvoie des prédictions pour les données d’entrée, ainsi que toutes les colonnes de données source que vous souhaitez passer.

Pour obtenir des exemples de code, ainsi que des instructions sur la façon de préparer les modèles dans le format binaire requis, consultez cet article :

+ [Comment effectuer le calcul de score en temps réel](r/how-to-do-realtime-scoring.md)

## <a name="requirements"></a>Spécifications

Plateformes prises en charge sont les suivantes :

+ Services SQL Server 2017 Machine Learning (y compris Microsoft R Server 9.1.0)
    
    Calculer les scores natif à l’aide de prédire nécessite SQL Server 2017.
    Il fonctionne sur n’importe quelle version de SQL Server 2017, y compris Linux.

    Vous pouvez également effectuer en temps réel de calcul de score à l’aide de sp_rxPredict, ce qui requiert l’activation de CLR SQL.

+ SQL Server 2016

   Et en temps réel à l’aide de calcul de score sp_rxPredict est possible avec SQL Server 2016, peut également être exécuté sur Microsoft R Server. Cette option requiert SQLCLR doit être activée et que vous installez la mise à niveau de Microsoft R Server.
   Pour plus d’informations, consultez [calculer les scores en temps réel](Real-time-scoring.md)

### <a name="model-preparation"></a>Préparation du modèle

+ Le modèle doit être formé à l’avance à l’aide d’une des prises en charge **rx** algorithmes. Pour plus d’informations, consultez [algorithmes pris en charge](#bkmk_native_supported_algos).
+ Le modèle doit être enregistré à l’aide de la nouvelle fonction de sérialisation fournie dans Microsoft R Server 9.1.0. La fonction de sérialisation est optimisée pour prendre en charge la notation rapide.

### <a name="bkmk_native_supported_algos"></a>Algorithmes qui prennent en charge la notation natif

+ Modèles de RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxdForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Si vous avez besoin d’utiliser des modèles à partir de MicrosoftML, utilisez en temps réel avec sp_rxPredict de calcul de score.

### <a name="restrictions"></a>Restrictions

Les types de modèles suivants ne sont pas prises en charge :

+ Modèles contenant des autres types de transformations de R non pris en charge
+ Modèles à l’aide de la `rxGlm` ou `rxNaiveBayes` algorithmes dans RevoScaleR
+ Modèles PMML
+ Modèles créés à l’aide d’autres bibliothèques R à partir de CRAN ou autres référentiels
+ Modèles contenant n’importe quel autre type de transformation de R

