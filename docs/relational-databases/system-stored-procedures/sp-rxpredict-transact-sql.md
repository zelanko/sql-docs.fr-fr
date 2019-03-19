---
title: sp_rxPredict | Microsoft Docs
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: HeidiSteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: 50e25162f88c42c0728f951702d304975fb7091b
ms.sourcegitcommit: 11ab8a241a6d884b113b3cf475b2b9ed61ff00e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161596"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Génère une valeur prédite pour une entrée donnée consistant en un modèle stocké dans un format binaire dans une base de données SQL Server machine learning.

Fournit des modèles R et Python machine learning dans quasiment en temps réel de notation. `sp_rxPredict` est une procédure stockée fournie comme un wrapper pour le `rxPredict` fonction R au [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) et [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)et le [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) fonction Python dans [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Il est écrit en C++ et est spécialement optimisée pour les opérations de calcul de score.

Bien que le modèle doit être créé à l’aide de R ou Python, une fois qu’il est sérialisé et stocké dans un format binaire sur une instance du moteur de base de données cible, il peut être consommé à partir de cette instance du moteur de base de données même lors de l’intégration de R ou Python n’est pas installée. Pour plus d’informations, consultez [notation en temps réel avec sp_rxPredict](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).

## <a name="syntax"></a>Syntaxe

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Arguments

**model**

Un modèle préformé dans un format pris en charge. 

**input**

Une requête SQL valide

### <a name="return-values"></a>Valeurs retournées

Une colonne de score est renvoyée, ainsi que les colonnes SQL directes à partir de la source de données d’entrée.
Autres colonnes, telles que de l’intervalle de confiance de score, peut être retourné si l’algorithme prend en charge la génération de ces valeurs.

## <a name="remarks"></a>Notes

Pour activer l’utilisation de la procédure stockée, SQLCLR doit être activé sur l’instance.

> [!NOTE]
> Voici les implications de sécurité à l’activation de cette option. Utiliser une autre implémentation, tel que le [Transact-SQL prédire](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql?view=sql-server-2017) fonction SQLCLR ne peut pas être activée sur votre serveur.

L’utilisateur doit avoir `EXECUTE` autorisation sur la base de données.

### <a name="supported-algorithms"></a>Algorithmes pris en charge

Pour créer et former le modèle, utilisez un des algorithmes pris en charge pour R ou Python, fourni par [SQL Server 2016 R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services?view=sql-server-2017), [SQL Server 2016 R Server (autonome)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2016), [Machine SQL Server 2017 Learning Services (R ou Python)](https://docs.microsoft.com//sql/advanced-analytics/what-is-sql-server-machine-learning?view=sql-server-2017), ou [SQL Server 2017 Server (autonome) (R ou Python)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2017).

#### <a name="r-revoscaler-models"></a>R : Modèles de RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>R : Modèles de MicrosoftML

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>R : Transformations fournies par MicrosoftML

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

#### <a name="python-revoscalepy-models"></a>Python : modèles de revoscalepy

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit)
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree)
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)


#### <a name="python-microsoftml-models"></a>Python : modèles de microsoftml

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

#### <a name="python-transformations-supplied-by-microsoftml"></a>Python : Transformations fournies par microsoftml

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-referencee/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>Types de modèles non pris en charge

Les types de modèles suivants ne sont pas prises en charge :

+ Modèles à l’aide de la `rxGlm` ou `rxNaiveBayes` algorithmes dans RevoScaleR
+ Modèles PMML dans R
+ Modèles créés à l’aide d’autres bibliothèques tierces 

## <a name="examples"></a>Exemples

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

En plus de constituer une requête SQL valide, les données d’entrée dans *@inputData* doit inclure des colonnes compatibles avec les colonnes dans le modèle stocké.

`sp_rxPredict` prend en charge uniquement les types de colonne de .NET suivants : double, float, short, ushort, long, ulong et chaîne. Vous devrez peut-être filtrer les types non pris en charge dans vos données d’entrée avant de l’utiliser pour calculer les scores en temps réel. 

  Pour plus d’informations sur les types SQL correspondants, consultez [le mappage de Type SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) ou [mappage des données de paramètre CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

