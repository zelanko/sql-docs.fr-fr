---
title: Notation native dans l’apprentissage de SQL Server | Microsoft Docs
description: Générer des prédictions à l’aide de la fonction de prédire le T-SQL, notation entrées dta par rapport à un modèle préentraîné écrites en R ou Python sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bf8f9a6362b72efddccbf5c2b0e54096c6e86aa7
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2018
ms.locfileid: "40395933"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Notation native à l’aide de la fonction de prédire le T-SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Une fois que vous avez un modèle préentraîné, vous pouvez passer les nouvelles données d’entrée à la fonction pour générer des valeurs de prédiction ou *scores*. Dans SQL Server 2017 Windows ou Linux, ou dans la base de données SQL Azure, vous pouvez utiliser la fonction PREDICT dans Transact-SQL pour prendre en charge la notation native. Elle nécessite uniquement que vous disposez d’un modèle déjà formé, que vous pouvez appeler à l’aide de T-SQL. 

+ What ' s native de notation et la notation en temps réel
+ Fonctionnement
+ Configuration requise et plates-formes prises en charge

## <a name="what-is-native-scoring-and-how-is-it-different-from-real-time-scoring"></a>Quelle est la notation native et en quoi diffère de la notation en temps réel ?

Dans SQL Server 2016, Microsoft a créé une infrastructure d’extensibilité qui permet aux scripts R doit être exécuté à partir de T-SQL. Cette infrastructure prend en charge toute opération que vous pouvez effectuer dans R, allant de fonctions simples de formation complexe modèles d’apprentissage. Toutefois, l’architecture du processus de double requiert appeler un processus R externe pour chaque appel, quel que soit la complexité de l’opération. Si vous chargez un modèle préentraîné à partir d’une table et la notation dont elle fait sur les données déjà présentes dans SQL Server, la surcharge de l’appel au processus R externe représente un coût de performances inutiles.

_Calcul de score_ est un processus en deux étapes. Tout d’abord, vous spécifiez un modèle préentraîné à charger à partir d’une table. En second lieu, passez de nouveau les données à la fonction, pour générer des valeurs de prédiction d’entrée (ou _scores_). L’entrée peut être tabulaires ou uniques des lignes. Vous pouvez choisir de générer une valeur de colonne unique qui représente une probabilité ou vous pouvez générer plusieurs valeurs, comme un intervalle de confiance, erreur ou autres complément utile à la prédiction.

Lorsque l’entrée inclut plusieurs lignes de données, il est généralement plus rapide pour insérer les valeurs de prédiction dans une table en tant que partie du processus de calcul de score.  Génération d’une seule note est plus courant dans un scénario où obtenir les valeurs d’entrée à partir d’une demande de formulaire ou d’utilisateur et retourner le score à une application cliente. Pour améliorer les performances lors de la génération de scores successives, SQL Server peut mettre en cache le modèle afin qu’il peut être rechargé en mémoire.

Pour prendre en charge rapide de notation, SQL Server Machine Learning Services (et Microsoft Machine Learning Server) fournissent des bibliothèques de score intégrés qui fonctionnent dans R ou T-SQL. Il existe des options différentes selon la version dont vous disposez.

**Calcul de score en natif**

+ La fonction PREDICT dans Transact-SQL prend en charge _notation native_ dans n’importe quelle instance de SQL Server 2017. Elle nécessite uniquement que vous disposez d’un modèle déjà formé, que vous pouvez appeler à l’aide de T-SQL. Notation native à l’aide de T-SQL offre ces avantages :

    + Aucune configuration supplémentaire n’est nécessaire.
    + Le runtime R n’est pas appelé. Il est inutile d’installer R.

**Calcul de score en temps réel**

+ **sp_rxPredict** est une procédure stockée pour notation en temps réel qui peut être utilisé pour génère les scores à partir de n’importe quel type de modèle pris en charge, sans appeler le runtime R.

  Cette procédure stockée est également disponible dans SQL Server 2016, si vous mettez à niveau les composants R à l’aide du programme d’installation autonome de Microsoft R Server. sp_rxPredict est également pris en charge dans SQL Server 2017. Par conséquent, vous pouvez utiliser cette fonction lors de la génération de scores avec un type de modèle non pris en charge par la fonction PREDICT.

+ La fonction rxPredict peut être utilisée pour calculer les scores rapide dans du code R.

Pour l’ensemble de ces méthodes, vous devez utiliser un modèle qui a été formé à l’aide d’un des algorithmes RevoScaleR ou MicrosoftML pris en charge.

Pour obtenir un exemple de calcul de score en temps réel en action, consultez [fin à la fin prêt pertes sèches sur prédiction créé à l’aide de Azure HDInsight Clusters Spark et SQL Server 2016 R services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="how-native-scoring-works"></a>Comment native notation fonctionne

Notation native utilise les bibliothèques C++ natives à partir de Microsoft qui peut lire le modèle à partir d’un format binaire spécial et générer des scores. Car un modèle peut être publié et utilisé pour calculer les scores sans avoir à appeler l’interpréteur R, la surcharge de plusieurs des interactions de processus est réduite. Par conséquent, notation native prend en charge les performances de prédiction beaucoup plus rapides dans les scénarios de production d’entreprise.

Pour générer des scores à l’aide de cette bibliothèque, vous appelez la fonction de score et passez les entrées requises suivantes :

+ Un modèle compatible. Consultez le [exigences](#Requirements) section pour plus d’informations.
+ Données d’entrée, généralement définies comme une requête SQL

La fonction renvoie des prédictions pour les données d’entrée, ainsi que toutes les colonnes de données source que vous souhaitez passer.

Pour obtenir des exemples de code, ainsi que des instructions sur la façon de préparer les modèles dans le format binaire requis, consultez cet article :

+ [Comment exécuter une notation en temps réel](r/how-to-do-realtime-scoring.md)

Pour une solution complète qui inclut la notation native, consultez ces exemples à partir de l’équipe de développement SQL Server :

+ Déployer votre script ML : [à l’aide d’un modèle Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Déployer votre script ML : [à l’aide d’un modèle R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)

## <a name="requirements"></a>Spécifications

Plateformes prises en charge sont les suivantes :

+ SQL Server 2017 Machine Learning Services (inclut Microsoft R Server 9.1.0).)
    
    Notation native à l’aide de PREDICT nécessite SQL Server 2017.
    Elle fonctionne sur n’importe quelle version de SQL Server 2017, y compris Linux.

    Vous pouvez également effectuer une notation à l’aide de sp_rxPredict en temps réel. Pour utiliser cette procédure stockée nécessite que vous activiez [intégration du CLR de SQL Server](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ SQL Server 2016

   En temps réel à l’aide de la notation sp_rxPredict est possible avec SQL Server 2016 et peut également être exécuté sur Microsoft R Server. Cette option nécessite SQLCLR doit être activé et que vous installez la mise à niveau de Microsoft R Server.
   Pour plus d’informations, consultez [de score en temps réel](Real-time-scoring.md)

### <a name="model-preparation"></a>Préparation du modèle

+ Le modèle doit être formé à l’avance à l’aide d’une des prises en charge **rx** algorithmes. Pour plus d’informations, consultez [pris en charge les algorithmes](#bkmk_native_supported_algos).
+ Le modèle doit être enregistré à l’aide de la nouvelle fonction de sérialisation fournie dans Microsoft R Server 9.1.0). La fonction de sérialisation est optimisée pour prendre en charge rapide de notation.

### <a name="bkmk_native_supported_algos"></a> Algorithmes qui prennent en charge la notation native

+ Modèles de RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Si vous avez besoin d’utiliser des modèles à partir de MicrosoftML, utilisez la notation en temps réel avec sp_rxPredict.

### <a name="restrictions"></a>Restrictions

Les types de modèles suivants ne sont pas prises en charge :

+ Modèles contenant d’autres types de transformations de R non pris en charge
+ Modèles à l’aide de la `rxGlm` ou `rxNaiveBayes` algorithmes dans RevoScaleR
+ Modèles PMML
+ Modèles créés à l’aide d’autres bibliothèques R à partir de CRAN ou d’autres référentiels
+ Modèles contenant toutes les transformations de R

## <a name="see-also"></a>Voir aussi

[Notation dans l’apprentissage de SQL Server en temps réel ](real-time-scoring.md)