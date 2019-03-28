---
title: package Python revoscalepy - SQL Server Machine Learning Services
description: Introduction au module revoscalepy dans SQL Server 2017 Machine Learning Services avec Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e0cded793f6017398641ffa055deec62010b2b3d
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510606"
---
# <a name="revoscalepy-python-module-in-sql-server"></a>revoscalepy (module Python dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy** est un module Python35 compatible de Microsoft qui prend en charge l’informatique distribuée, les contextes de calcul distants et les algorithmes de science des données hautes performances. Il est basé sur le **RevoScaleR** package pour R (distribué avec Microsoft R Server et SQL Server R Services), offre des fonctionnalités similaires :

+ Locale et à distance de contextes sur des systèmes comportant la même version de calculent **revoscalepy**
+ Fonctions de transformation et de visualisation de données
+ Fonctions de science des données, évolutives via le traitement distribué ou en parallèle
+ Amélioration des performances, notamment l’utilisation des bibliothèques de mathématiques Intel

Sources de données et les contextes de calcul que vous créez dans **revoscalepy** peut également être utilisé dans les algorithmes d’apprentissage automatique. Pour une introduction à ces algorithmes, consultez [module Python de microsoftml dans SQL Server](ref-py-microsoftml.md).

## <a name="full-reference-documentation"></a>Documentation de référence complète

Le **revoscalepy** library est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même, si vous obtenez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont les mêmes, [documentation pour les fonctions individuelles revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) est publié dans un seul emplacement sous la [référence Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour Microsoft Machine Learning Server. Doivent tout propres au produit comportements existent, les différences sont notées dans la page d’aide (fonction).

## <a name="versions-and-platforms"></a>Versions et plateformes

Le **revoscalepy** module est en fonction de Python 3.5 et disponible uniquement lorsque vous installez un des produits Microsoft ou des téléchargements suivants :

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 ou version ultérieure](https://docs.microsoft.com/machine-learning-server/)
+ [Bibliothèques de client Python pour un client de science des données](setup-python-client-tools-sql.md)

> [!NOTE]
> Les versions de produit complet sont Windows uniquement, en commençant par SQL Server 2017. Prise en charge de Linux pour **revoscalepy** est une nouveauté de [SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Fonctions par catégorie

Cette section répertorie les fonctions par catégorie pour vous donner une idée de l’utilisation de chacun d’eux. Vous pouvez également utiliser le [table des matières](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) pour rechercher des fonctions dans l’ordre alphabétique.

## <a name="1-data-source-and-compute"></a>Calcul et la source de données 1

**revoscalepy** inclut des fonctions pour la création des sources de données et la définition de l’emplacement, ou *contexte de calcul*, d’où les calculs sont effectués. Fonctions liées aux scénarios de SQL Server sont répertoriées dans le tableau ci-dessous.

SQL Server et Python utilisent différents types de données dans certains cas. Pour obtenir la liste de mappages entre les types de données SQL et Python, consultez [les types de données de Python-to-SQL](python-libraries-and-data-types.md).

| Fonction| Description|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  Créer un objet de contexte de calcul de SQL Server pour envoyer des calculs à une instance distante. Plusieurs **revoscalepy** fonctions acceptent le contexte de calcul en tant qu’argument. Pour obtenir un exemple de changement de contexte, consultez [créer un modèle à l’aide de revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md).|
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | Créer un objet de données basé sur une requête SQL Server ou une table. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| Créer une source de données basée sur une connexion ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | Créer une source de données basée sur un fichier XDF local. Fichiers XDF sont souvent utilisés pour décharger les données en mémoire sur le disque. Un fichier XDF peut être utile lorsque vous travaillez avec plus de données peuvent être transférées à partir de la base de données dans un lot, ou plus de données que peut tenir dans la mémoire. Par exemple, si vous déplacez régulièrement des grandes quantités de données à partir d’une base de données vers une station de travail locale, plutôt que d’interroger la base de données à plusieurs reprises pour chaque opération R, vous pouvez utiliser le fichier XDF comme un type de cache pour enregistrer les données localement et puis les utiliser dans votre espace de travail R. |

> [!TIP]
> Si vous ne connaissez pas l’idée de sources de données ou les contextes de calcul, nous vous recommandons de commencer avec [distributed computing](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) dans la documentation de Microsoft Machine Learning Server.

## <a name="2-data-manipulation-etl"></a>Manipulation de données-2 (ETL)

| Fonction | Description |
|----------|-------------|
|[rx_import](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-import) | Importer des données dans une trame de données ou de fichier .xdf.|
|[rx_data_step](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-data-step) | Transformer des données à partir d’un jeu de données d’entrée à un jeu de données de sortie.|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3-formation et synthèse

| Fonction| Description|
| ------- | ---------- |
|[rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) | Ajuster les arbres de décision augmentés de gradient stochastique|
|[rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) | Ajuster les forêts de décision de classification et de régression|
|[rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) | Ajuster des arbres de classification et de régression |
|[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | Créer un modèle de régression linéaire|
|[rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) | Créer un modèle de régression logistique|
|[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) | Générer des résumés à variable unique des objets de revoscalepy.|

Vous devez également examiner les fonctions dans [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) pour d’autres approches.

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>Fonctions de calcul de score 4

| Fonction| Description|
| ------- | ---------- |
| [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Générer des prédictions à partir d’un modèle formé|) | Génère des prédictions à partir d’un modèle formé et peut être utilisé pour calculer les scores en temps réel. |
|[rx_predict_default](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | Calcul des valeurs prédites et résidus à l’aide d’objets rx_lin_mod et rx_logit. |
|[rx_predict_rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Calculer les valeurs prédites ou montés pour un jeu de données à partir d’un objet rx_dforest ou rx_btrees. |
|[rx_predict_rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Calculer les valeurs prédites ou montés pour un jeu de données à partir d’un objet rx_dtree. |

## <a name="how-to-work-with-revoscalepy"></a>Comment travailler avec revoscalepy

Fonctions dans **revoscalepy** peuvent être appelées dans le code Python encapsulé dans des procédures stockées. La plupart des développeurs build **revoscalepy** solutions localement, puis migrez le code Python terminé à des procédures stockées comme un exercice de déploiement.

Lorsque vous exécutez localement, vous généralement exécuter un script Python à partir de la ligne de commande, ou à partir d’un environnement de développement Python et spécifier un contexte de calcul de SQL Server à l’aide d’une de la **revoscalepy** fonctions. Vous pouvez utiliser le contexte de calcul à distance pour l’ensemble du code, ou pour des fonctions individuelles. Par exemple, vous souhaiterez peut-être décharger l’apprentissage du modèle sur le serveur d’utiliser des données les plus récentes et éviter le déplacement des données.

Lorsque vous êtes prêt à encapsuler le script Python à l’intérieur d’une procédure stockée, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), nous vous recommandons de réécrire le code comme une fonction unique qui a défini clairement les entrées et sorties. 

Entrées et sorties doivent être **pandas** des trames de données. Dans ce cas, vous pouvez appeler la procédure stockée à partir de n’importe quel client qui prend en charge T-SQL, facilement transmettre les requêtes SQL en tant qu’entrées et enregistrer les résultats dans des tables SQL. Pour obtenir un exemple, consultez [Découvrez analytique de Python dans base de données pour les développeurs SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-revoscalepy-with-microsoftml"></a>À l’aide de revoscalepy avec microsoftml

Fonctions de Python pour [microsoftml](ref-py-microsoftml.md) sont intégrées avec les calcul des contextes et sources de données qui sont fournies dans revoscalepy. Lors de l’appel des fonctions à partir de microsoftml, par exemple lorsque définition et l’apprentissage d’un modèle, utilisez les fonctions revoscalepy pour exécuter les Python code soit localement ou dans SQl Server à distance le contexte de calcul.

L’exemple suivant montre la syntaxe pour l’importation de modules dans votre code Python. Vous pouvez ensuite référencer les fonctions individuelles que vous avez besoin.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Voir aussi

+ [Didacticiels Python](../tutorials/sql-server-python-tutorials.md)
+ [Didacticiel : Incorporer le code Python dans T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Référence Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)
