---
title: Package Python revoscalepy
description: Présentation du module revoscalepy dans SQL Server Machine Learning Services avec Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c6de9072c32155446b3ff40df3f81af9073c1090
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "73706814"
---
# <a name="revoscalepy-python-module-in-sql-server"></a>revoscalepy (module Python dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**revoscalepy** est un module compatible Python35 de Microsoft prenant en charge le calcul distribué, les contextes de calcul distants et les algorithmes de science des données hautes performances. Il est basé sur le package **RevoScaleR** pour R (distribué avec Microsoft R Server et SQL Server R Services) et offre des fonctionnalités similaires :

+ Contextes de calcul locaux et distants sur les systèmes utilisant la même version de **revoscalepy**
+ Fonctions de transformation et de visualisation des données
+ Fonctions de science des données évolutives via un traitement distribué ou parallèle
+ Performances améliorées avec utilisation des bibliothèques mathématiques Intel incluse

Les sources de données et les contextes de calcul que vous créez dans **revoscalepy** peuvent également être utilisés dans des algorithmes de Machine Learning. Pour suivre une présentation de ces algorithmes, consultez [microsoftml Python module in SQL Server](ref-py-microsoftml.md) (Module Python microsoftml dans SQL Server).

## <a name="full-reference-documentation"></a>Documentation de référence complète

La bibliothèque **revoscalepy** est distribuée dans plusieurs produits Microsoft, mais l’utilisation est la même que vous obteniez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont les mêmes, la [documentation de chaque fonction revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) est publiée au même endroit sous la [référence Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour Microsoft Machine Learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="versions-and-platforms"></a>Versions et plateformes

Le module **revoscalepy** est basé sur Python 3.5 et n’est disponible que lorsque vous installez l’un des produits ou téléchargements Microsoft suivants :

+ [Services de Machine Learning SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](https://docs.microsoft.com/machine-learning-server/)
+ [Bibliothèques clientes Python pour un client de science des données](setup-python-client-tools-sql.md)

> [!NOTE]
> Les versions complètes du produit sont uniquement disponibles sous Windows dans SQL Server 2017. Windows et Linux sont pris en charge pour **revoscalepy** dans [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous donner une idée de la façon dont chacune d’elles est utilisée. Vous pouvez également utiliser la [table des matières](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

## <a name="1-data-source-and-compute"></a>1-Source de données et calcul

**revoscalepy** comprend des fonctions permettant de créer des sources de données et de définir l’emplacement, ou *contexte de calcul*, où les calculs sont effectués. Les fonctions relatives aux scénarios SQL Server sont répertoriées dans le tableau ci-dessous.

Dans certains cas, SQL Server et Python utilisent des types de données différents. Pour obtenir la liste des mappages entre les types de données SQL et Python, consultez [Types de données Python vers SQL](python-libraries-and-data-types.md).

| Fonction| Description|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  Créez un objet de contexte de calcul SQL Server pour envoyer des calculs à une instance distante. Plusieurs fonctions **revoscalepy** prennent le contexte de calcul comme argument. Pour obtenir un exemple de changement de contexte, consultez [Créer un modèle à l’aide de revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md).|
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | Créez un objet de données basé sur une requête ou une table SQL Server. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| Créez une source de données basée sur une connexion ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | Créez une source de données basée sur un fichier XDF local. Les fichiers XDF sont souvent utilisés pour décharger les données en mémoire sur le disque. Un fichier XDF peut être utile quand la quantité des données utilisées est trop importante pour être transférée en un seul lot à partir de la base de données ou pour tenir dans la mémoire. Par exemple, si vous déplacez régulièrement de grandes quantités de données d’une base de données vers une station de travail locale, plutôt que d’interroger de façon répétée la base de données à chaque opération R, vous pouvez vous servir du fichier XDF comme cache pour enregistrer les données localement et les exploiter ensuite dans votre espace de travail R. |

> [!TIP]
> Si vous débutez avec les sources de données ou les contextes de calcul, nous vous recommandons de commencer par vous renseigner sur le [calcul distribué](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) dans la documentation de Microsoft Machine Learning Server.

## <a name="2-data-manipulation-etl"></a>2-Manipulation de données (ETL)

| Fonction | Description |
|----------|-------------|
|[rx_import](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-import) | Importer des données dans un fichier ou une trame de données au format .xdf.|
|[rx_data_step](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-data-step) | Transformer les données d’un jeu de données d’entrée en jeu de données de sortie.|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3-Formation et résumé

| Fonction| Description|
| ------- | ---------- |
|[rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) | Ajuster des arbres de décision améliorés par des gradients stochastiques|
|[rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) | Ajuster des forêts de décision de régression et de classification|
|[rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) | Ajuster des arbres de régression et de classification |
|[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | Créer un modèle de régression linéaire|
|[rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) | Créer un modèle de régression logistique|
|[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) | Produire des résumés d’objets à variable unique dans revoscalepy.|

Vous devez également examiner les fonctions dans [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) pour obtenir des approches supplémentaires.

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>4-Fonctions de scoring

| Fonction| Description|
| ------- | ---------- |
| [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Générer des prédictions à partir d’un modèle entraîné|) | Génère des prédictions à partir d’un modèle entraîné et peut être utilisé pour le scoring en temps réel. |
|[rx_predict_default](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | Calculer des résiduels et des valeurs prédites à l’aide d’objets rx_lin_mod et rx_logit. |
|[rx_predict_rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Calculer les valeurs prédites ou ajustées d’un jeu de données à partir d’un objet rx_dforest ou rx_btrees. |
|[rx_predict_rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Calculer les valeurs prédites ou ajustées d’un jeu de données à partir d’un objet rx_dtree. |

## <a name="how-to-work-with-revoscalepy"></a>Procédure d’utilisation de revoscalepy

Les fonctions de **revoscalepy** peuvent être appelées dans du code Python encapsulé dans des procédures stockées. La plupart des développeurs créent des solutions **revoscalepy** localement, puis migrent le code Python terminé vers les procédures stockées en guise d’exercice de déploiement.

Lors d’une exécution locale, vous exécutez généralement un script Python à partir de la ligne de commande, ou à partir d’un environnement de développement Python, et vous spécifiez un contexte de calcul SQL Server à l’aide de l’une des fonctions **revoscalepy**. Vous pouvez utiliser le contexte de calcul distant pour l’intégralité du code, ou pour des fonctions individuelles. Par exemple, vous souhaiterez peut-être décharger l’apprentissage du modèle sur le serveur pour utiliser les données les plus récentes et éviter le déplacement des données.

Lorsque vous êtes prêt à encapsuler le script Python à l’intérieur d’une procédure stockée, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), nous vous recommandons de réécrire le code sous la forme d’une fonction unique ayant des entrées et des sorties clairement définies. 

Les entrées et les sorties doivent correspondre à des trames de données **pandas**. Une fois cette opération effectuée, vous pouvez appeler la procédure stockée à partir de n’importe quel client prenant en charge T-SQL, transmettre simplement les requêtes SQL en tant qu’entrées, puis enregistrer les résultats dans des tables SQL. Pour obtenir un exemple, consultez [Analyse des données Python pour les développeurs SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-revoscalepy-with-microsoftml"></a>Utiliser revoscalepy avec microsoftml

Les fonctions Python pour [microsoftml](ref-py-microsoftml.md) sont intégrées aux contextes de calcul et aux sources de données fournis dans revoscalepy. Lorsque vous appelez des fonctions à partir de microsoftml, par exemple lors de la définition et de l’apprentissage d’un modèle, utilisez les fonctions revoscalepy pour exécuter le code Python localement ou dans un contexte de calcul distant SQL Server.

L’exemple suivant illustre la syntaxe permettant d’importer des modules dans votre code Python. Ainsi, vous pouvez référencer les fonctions individuelles dont vous avez besoin.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Voir aussi

+ [Didacticiels Python](../tutorials/sql-server-python-tutorials.md)
+ [Tutoriel : Incorporer du code Python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Référence Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)
