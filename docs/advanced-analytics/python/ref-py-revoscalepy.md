---
title: package Python revoscalepy
description: Introduction au module revoscalepy dans SQL Server 2017 Machine Learning Services avec Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e38cac8969544a93d7487d83636c866ec7b09ce9
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344612"
---
# <a name="revoscalepy-python-module-in-sql-server"></a>revoscalepy (module python dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy** est un module compatible Python35 de Microsoft qui prend en charge l’informatique distribuée, les contextes de calcul à distance et les algorithmes de science des données à hautes performances. Il est basé sur le package **RevoScaleR** pour R (distribué avec Microsoft R Server et SQL Server R services), offrant des fonctionnalités similaires:

+ Contextes de calcul locaux et distants sur les systèmes ayant la même version de **revoscalepy**
+ Fonctions de transformation et de visualisation des données
+ Fonctions de science des données, évolutives via un traitement distribué ou parallèle
+ Amélioration des performances, y compris l’utilisation des bibliothèques mathématiques Intel

Les sources de données et les contextes de calcul que vous créez dans **revoscalepy** peuvent également être utilisés dans des algorithmes de machine learning. Pour une introduction à ces algorithmes, consultez [module python microsoftml dans SQL Server](ref-py-microsoftml.md).

## <a name="full-reference-documentation"></a>Documentation de référence complète

La bibliothèque **revoscalepy** est distribuée dans plusieurs produits Microsoft, mais l’utilisation est la même que vous obteniez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont identiques, la [documentation des fonctions revoscalepy individuelles](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) est publiée dans un seul emplacement sous la [référence python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour Microsoft machine learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="versions-and-platforms"></a>Versions et plateformes

Le module **revoscalepy** est basé sur Python 3,5 et n’est disponible que lorsque vous installez l’un des produits ou téléchargements Microsoft suivants:

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](https://docs.microsoft.com/machine-learning-server/)
+ [Bibliothèques clientes Python pour un client de science des données](setup-python-client-tools-sql.md)

> [!NOTE]
> Les versions complètes du produit sont uniquement Windows, à partir de SQL Server 2017. La prise en charge de Linux pour **revoscalepy** est une nouveauté de [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous faire une idée de la façon dont chacune d’elles est utilisée. Vous pouvez également utiliser la [table des matières](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

## <a name="1-data-source-and-compute"></a>1-source de données et calcul

**revoscalepy** comprend des fonctions permettant de créer des sources de données et de définir l’emplacement, ou le *contexte de calcul*, de l’endroit où les calculs sont effectués. Les fonctions relatives aux scénarios de SQL Server sont répertoriées dans le tableau ci-dessous.

SQL Server et Python utilisent différents types de données dans certains cas. Pour obtenir la liste des mappages entre les types de données SQL et Python, consultez [types de données python-to-SQL](python-libraries-and-data-types.md).

| Fonction| Description|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  Créez un objet de contexte de calcul SQL Server pour envoyer des calculs à une instance distante. Plusieurs fonctions **revoscalepy** prennent le contexte de calcul comme argument. Pour obtenir un exemple de commutateur de contexte, consultez [créer un modèle à l’aide de revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md).|
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | Créez un objet de données basé sur une requête ou une table SQL Server. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| Créer une source de données basée sur une connexion ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | Créer une source de données basée sur un fichier XDF local. Les fichiers XDF sont souvent utilisés pour décharger les données en mémoire sur le disque. Un fichier XDF peut être utile lors de l’utilisation de plus de données que celles pouvant être transférées à partir de la base de données en un seul lot, ou plus de données que la mémoire ne peut en contenir. Par exemple, si vous déplacez régulièrement de grandes quantités de données d’une base de données vers une station de travail locale, au lieu d’interroger la base de données à plusieurs reprises pour chaque opération R, vous pouvez utiliser le fichier XDF comme un type de cache pour enregistrer les données localement, puis les utiliser dans votre espace de travail R. |

> [!TIP]
> Si vous débutez avec l’idée des sources de données ou des contextes de calcul, nous vous recommandons de commencer avec l' [informatique distribuée](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) dans la documentation de Microsoft machine learning Server.

## <a name="2-data-manipulation-etl"></a>2-manipulation de données (ETL)

| Fonction | Description |
|----------|-------------|
|[rx_import](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-import) | Importez des données dans un fichier ou une trame de données. XDF.|
|[rx_data_step](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-data-step) | Transformez les données d’un jeu de données d’entrée en jeu de données de sortie.|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3-formation et résumé

| Fonction| Description|
| ------- | ---------- |
|[rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) | Ajuster les arbres de décision améliorés du gradient stochastique|
|[rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) | Tenir les forêts de décision de classification et de régression|
|[rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) | Ajuster les arborescences de classification et de régression |
|[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | Créer un modèle de régression linéaire|
|[rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) | Créer un modèle de régression logistique|
|[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) | Produire des résumés Student d’objets dans revoscalepy.|

Vous devez également examiner les fonctions dans [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) pour obtenir des approches supplémentaires.

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>4-fonctions de calcul de score

| Fonction| Description|
| ------- | ---------- |
| [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Générer des prédictions à partir d’un modèle formé|) | Génère des prédictions à partir d’un modèle formé et peut être utilisé pour le calcul de score en temps réel. |
|[rx_predict_default](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | Calculez les valeurs prédites et les résidus à l’aide d’objets rx_lin_mod et rx_logit. |
|[rx_predict_rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Calcule les valeurs prédites ou ajustées d’un jeu de données à partir d’un objet rx_dforest ou rx_btrees. |
|[rx_predict_rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Calcule les valeurs prédites ou ajustées d’un jeu de données à partir d’un objet rx_dtree. |

## <a name="how-to-work-with-revoscalepy"></a>Utilisation de revoscalepy

Les fonctions dans **revoscalepy** peuvent être appelées dans du code python encapsulé dans des procédures stockées. La plupart des développeurs créent des solutions **revoscalepy** localement, puis migrent le code python terminé vers les procédures stockées en tant qu’exercice de déploiement.

Lors d’une exécution locale, vous exécutez généralement un script Python à partir de la ligne de commande, ou à partir d’un environnement de développement Python, et spécifiez un SQL Server contexte de calcul à l’aide de l’une des fonctions **revoscalepy** . Vous pouvez utiliser le contexte de calcul distant pour l’intégralité du code, ou pour des fonctions individuelles. Par exemple, vous souhaiterez peut-être décharger l’apprentissage du modèle sur le serveur pour utiliser les données les plus récentes et éviter le déplacement des données.

Lorsque vous êtes prêt à encapsuler le script Python à l’intérieur d’une procédure stockée, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), nous vous recommandons de réécrire le code sous la forme d’une fonction unique ayant des entrées et des sorties clairement définies. 

Les entrées et les sorties  doivent être des trames de données pandas. Une fois cette opération effectuée, vous pouvez appeler la procédure stockée à partir de n’importe quel client qui prend en charge T-SQL, transmettre facilement des requêtes SQL en tant qu’entrées et enregistrer les résultats dans des tables SQL. Pour obtenir un exemple, consultez [l’analyse Python en base de données pour les développeurs SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-revoscalepy-with-microsoftml"></a>Utilisation de revoscalepy avec microsoftml

Les fonctions Python pour [microsoftml](ref-py-microsoftml.md) sont intégrées aux contextes de calcul et aux sources de données fournies dans revoscalepy. Lors de l’appel de fonctions à partir de microsoftml, par exemple lors de la définition et de l’apprentissage d’un modèle, utilisez les fonctions revoscalepy pour exécuter le code python localement ou dans un contexte de calcul distant SQl Server.

L’exemple suivant illustre la syntaxe pour l’importation de modules dans votre code Python. Vous pouvez ensuite référencer les fonctions individuelles dont vous avez besoin.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Voir aussi

+ [Didacticiels Python](../tutorials/sql-server-python-tutorials.md)
+ [Tutoriel : Incorporer du code python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Informations de référence sur Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)
