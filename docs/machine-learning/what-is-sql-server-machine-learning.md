---
title: Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?
titleSuffix: ''
description: Machine Learning Services est une fonctionnalité de SQL Server qui permet d’exécuter des scripts Python et R avec des données relationnelles. Vous pouvez utiliser des frameworks et des packages open source, ainsi que les packages Microsoft Python et R, pour l’analyse prédictive et le machine learning. Les scripts sont exécutés dans la base de données sans déplacer de données en dehors de SQL Server ou sur le réseau. Cet article présente les notions de base de SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/06/2020
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a94a3aea418a4c404b568fe6df7af701bc46de34
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81115682"
---
# <a name="what-is-sql-server-machine-learning-services-python-and-r"></a>Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Machine Learning Services est une fonctionnalité de SQL Server qui permet d’exécuter des scripts Python et R avec des données relationnelles. Vous pouvez utiliser des frameworks et des packages open source, ainsi que les [packages Microsoft Python et R](#packages), pour l’analyse prédictive et le machine learning. Les scripts sont exécutés dans la base de données sans déplacer de données en dehors de SQL Server ou sur le réseau. Cet article présente les notions de base de SQL Server Machine Learning Services.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Pour exécuter Java dans SQL Server, consultez la [documentation sur les extensions de langage](../language-extensions/language-extensions-overview.md).
::: moniker-end

## <a name="what-is-machine-learning-services"></a>Qu’est-ce que Machine Learning Services ?

SQL Server Machine Learning Services vous permet d’exécuter des scripts Python et R en base de données. Vous pouvez vous en servir pour préparer et nettoyer des données, effectuer l’ingénierie des fonctionnalités et entraîner, évaluer et déployer des modèles Machine Learning dans une base de données. La fonctionnalité exécute vos scripts là où résident les données, ce qui vous évite d’avoir à transférer les données vers un autre serveur à travers le réseau.

Les distributions de base de Python et de R sont incluses dans Machine Learning Services. Vous pouvez installer et utiliser des frameworks et des packages open source comme PyTorch, TensorFlow et scikit-learn, en plus des packages Microsoft [revoscalepy](python/ref-py-revoscalepy.md) et [microsoftml](python/ref-py-microsoftml.md) pour Python, et [RevoScaleR](r/ref-r-revoscaler.md), [MicrosoftML](r/ref-r-microsoftml.md), [olapR](r/ref-r-olapr.md) et [sqlrutils](r/ref-r-sqlrutils.md) pour R.

Machine Learning Services utilise un framework d’extensibilité pour exécuter les scripts Python et R dans SQL Server. Pour en savoir plus, consultez :

+ [Framework d’extensibilité](concepts/extensibility-framework.md)
+ [Extension Python](concepts/extension-python.md)
+ [Extension R](concepts/extension-r.md)

## <a name="what-can-i-do-with-machine-learning-services"></a>Que puis-je faire avec Machine Learning Services ?

Vous pouvez utiliser Machine Learning Services pour générer et entraîner des modèles Machine Learning et Deep Learning dans SQL Server. Vous pouvez également déployer des modèles existants sur Machine Learning Services et utiliser des données relationnelles pour les prédictions.

Voici des exemples de types de prédictions pour lesquels vous pouvez utiliser SQL Server Machine Learning Services :

|||
|-|-|
|Classification/catégorisation|Diviser automatiquement les commentaires des clients en catégories positives et négatives|
|Régression/prédiction de valeurs continues|Prédire le prix de maisons en fonction de la taille et de l’emplacement|
|Détection des anomalies|Détecter les transactions bancaires frauduleuses |
|Recommandations|Suggérer des produits que les acheteurs en ligne peuvent souhaiter acheter, en fonction de leurs achats précédents|

### <a name="how-to-execute-python-and-r-scripts"></a>Comment exécuter des scripts Python et R

Vous pouvez exécuter des scripts Python et R dans Machine Learning Services de deux façons :

+ La méthode la plus courante consiste à utiliser la procédure stockée T-SQL [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Vous pouvez également utiliser votre client Python ou R préféré et écrire des scripts qui envoient (push) l’exécution (appelée *contexte de calcul distant*) à un serveur SQL Server distant. Pour plus d’informations, découvrez comment configurer un client de science des données pour le [développement Python](python/setup-python-client-tools-sql.md) et le [développement R](r/set-up-a-data-science-client.md).

<a name="versions"></a>

## <a name="python-and-r-versions"></a>Versions de Python et de R

La version de Python et de R fournie dans Machine Learning Services dépend de la version de SQL Server que vous utilisez. 

| Version de SQL Server | Version Python | Version de R |
|-|-|-|
| SQL Server 2017 | 3.5.2 | 3.3.3 |
| SQL Server 2019 | 3.7.3 | 3.5.2 |

Pour savoir quelle version de R est fournie dans SQL Server 2016, consultez la [section sur les versions de R dans Qu’est-ce que R Services ?](r/sql-server-r-services.md#version)

<a name="packages"></a>

## <a name="python-and-r-packages"></a>Packages Python et R

Vous pouvez utiliser des frameworks et des packages open source, en plus des packages d’entreprise Microsoft. Les packages Python et R open source les plus courants sont préinstallés dans Machine Learning Services. Les packages Python et R suivants de Microsoft sont également inclus :

| Langage | Package | Description |
|-|-|-|
| Python | [revoscalepy](python/ref-py-revoscalepy.md) | Package principal pour créer du code Python scalable : transformations et manipulations de données, totalisation statistique, visualisation et nombreuses formes de modélisation. De plus, les fonctions de ce package distribuent automatiquement les charges de travail entre les cœurs disponibles pour un traitement parallèle. |
| Python | [microsoftml](python/ref-py-microsoftml.md) | Ajoute des algorithmes de machine learning pour créer des modèles personnalisés pour l’analyse des textes, l’analyse des images et l’analyse des sentiments. | 
| R | [RevoScaleR](r/ref-r-revoscaler.md) | Package principal pour créer du code Python scalable : transformations et manipulations de données, totalisation statistique, visualisation et nombreuses formes de modélisation. De plus, les fonctions de ce package distribuent automatiquement les charges de travail entre les cœurs disponibles pour un traitement parallèle. |
| R | [MicrosoftML (R)](r/ref-r-microsoftml.md) | Ajoute des algorithmes de machine learning pour créer des modèles personnalisés pour l’analyse des textes, l’analyse des images et l’analyse des sentiments. |
| R | [olapR](r/ref-r-olapr.md) | Fonctions R utilisées pour les requêtes MDX sur un cube OLAP SQL Server Analysis Services. |
| R | [sqlrutils](r/ref-r-sqlrutils.md) | Mécanisme permettant d’utiliser les scripts R dans une procédure stockée T-SQL, d’inscrire cette procédure auprès d’une base de données et d’exécuter la procédure stockée à partir d’un [environnement de développement R](r/set-up-a-data-science-client.md). |
| R | [Microsoft R Open](https://mran.microsoft.com/rro) | Microsoft R Open (MRO) est la distribution améliorée de R fournie par Microsoft. Il s’agit d’une plate-forme open source complète pour l’analyse statistique et la science des données. Basée sur R et entièrement compatible avec ce langage, elle comprend des fonctionnalités supplémentaires visant à améliorer les performances et la reproductibilité. |

Pour plus d’informations sur les packages installés avec Machine Learning Services et sur l’installation d’autres packages, consultez :

+ [Obtenir des informations sur les packages Python](package-management/python-package-information.md)
+ [Installer des packages Python avec sqlmlutils](package-management/install-additional-python-packages-on-sql-server.md)
+ [Obtenir des informations sur les packages R](package-management/r-package-information.md)
+ [Installer de nouveaux packages R avec sqlmlutils](package-management/install-additional-r-packages-on-sql-server.md)

## <a name="how-do-i-get-started-with-machine-learning-services"></a>Comment bien démarrer avec Machine Learning Services ?

1. [Installer SQL Server Machine Learning Services](install/sql-machine-learning-services-windows-install.md)

1. Configurez vos outils de développement. Vous pouvez utiliser :

    + [Azure Data Studio](../azure-data-studio/what-is.md) ou [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) pour utiliser T-SQL et la procédure stockée [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour exécuter votre script Python ou R.
    + Python ou R sur votre propre ordinateur portable ou station de travail de développement pour exécuter des scripts. Vous pouvez tirer (pull) les données localement ou envoyer (push) l’exécution à distance vers SQL Server avec [revoscalepy](python/ref-py-revoscalepy.md) et [RevoScaleR](r/ref-r-revoscaler.md). Pour plus d’informations, découvrez comment configurer un client de science des données pour le [développement Python](python/setup-python-client-tools-sql.md) et le [développement R](r/set-up-a-data-science-client.md).

1. Écrivez votre premier script Python ou R.

    + Démarrage rapide : [Exécuter des scripts Python simples](tutorials/quickstart-python-create-script.md)
    + Démarrage rapide : [Exécuter des scripts R simples](tutorials/quickstart-r-create-script.md)
    + Tutoriel : [Utiliser Python dans T-SQL](tutorials/sqldev-in-database-python-for-sql-developers.md). Explorez les données, effectuez l’ingénierie des caractéristiques, entraînez et déployez des modèles, et faites des prédictions (série en cinq parties)
    + Tutoriel : [Utiliser R dans T-SQL](tutorials/sqldev-in-database-r-for-sql-developers.md). Explorez les données, effectuez l’ingénierie des caractéristiques, entraînez et déployez des modèles, et faites des prédictions (série en cinq parties)

## <a name="next-steps"></a>Étapes suivantes

+ [Installer SQL Server Machine Learning Services](install/sql-machine-learning-services-windows-install.md)
+ Configurer un client de science des données pour le [développement Python](python/setup-python-client-tools-sql.md) et le [développement R](r/set-up-a-data-science-client.md)
