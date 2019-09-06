---
title: Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?
titleSuffix: ''
description: Machine Learning Services est une fonctionnalité de SQL Server qui donne la possibilité d’exécuter des scripts Python et R avec des données relationnelles. Vous pouvez utiliser des infrastructures et des packages Open source, ainsi que les packages Microsoft Python et R pour l’analyse prédictive et les Machine Learning. Les scripts sont exécutés dans la base de données sans déplacer de données en dehors de SQL Server ou sur le réseau. Cet article explique les principes fondamentaux de SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/07/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d60445d52a8a78fb7924d82338162e4719f45681
ms.sourcegitcommit: 26715b4dbef95d99abf2ab7198a00e6e2c550243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70276666"
---
# <a name="what-is-sql-server-machine-learning-services-python-and-r"></a>Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Machine Learning Services est une fonctionnalité de SQL Server qui donne la possibilité d’exécuter des scripts Python et R avec des données relationnelles. Vous pouvez utiliser des infrastructures et des packages Open source, ainsi que les [packages Microsoft Python et R](#packages) pour l’analyse prédictive et les machine learning. Les scripts sont exécutés dans la base de données sans déplacer de données en dehors de SQL Server ou sur le réseau. Cet article explique les principes fondamentaux de SQL Server Machine Learning Services.

Dans Azure SQL Database, [machine learning services](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview) est actuellement en version préliminaire publique.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Pour exécuter Java dans SQL Server, consultez la documentation sur les [extensions de langage](../language-extensions/language-extensions-overview.md).
::: moniker-end

## <a name="what-is-machine-learning-services"></a>Qu’est-ce que Machine Learning Services ?

SQL Server Machine Learning Services vous permet d’exécuter des scripts Python et R dans la base de données. Vous pouvez l’utiliser pour préparer et nettoyer des données, procéder à l’ingénierie des fonctionnalités et former, évaluer et déployer des Machine Learning des modèles dans une base de données. La fonctionnalité exécute vos scripts où résident les données et élimine le transfert des données sur le réseau vers un autre serveur.

Les distributions de base de Python et R sont incluses dans Machine Learning Services. Vous pouvez installer et utiliser des packages et infrastructures Open source, tels que PyTorch, TensorFlow et scikit-Learn, en plus des packages Microsoft [revoscalepy](python/ref-py-revoscalepy.md) et [microsoftml](python/ref-py-microsoftml.md) pour Python [, et RevoScaleR,](r/ref-r-revoscaler.md) [microsoftml](r/ref-r-microsoftml.md), [olapr](r/ref-r-olapr.md)et [sqlrutils](r/ref-r-sqlrutils.md) pour R.

Machine Learning Services utilise une infrastructure d’extensibilité pour exécuter des scripts Python et R dans SQL Server. En savoir plus sur ce fonctionnement :

+ [Infrastructure d’extensibilité](concepts/extensibility-framework.md)
+ [Extension Python](concepts/extension-python.md)
+ [Extension R](concepts/extension-r.md)

## <a name="what-can-i-do-with-machine-learning-services"></a>Que puis-je faire avec Machine Learning Services ?

Vous pouvez utiliser Machine Learning Services pour créer et former des Machine Learning et des modèles d’apprentissage profond dans SQL Server. Vous pouvez également déployer des modèles existants pour Machine Learning Services et utiliser des données relationnelles pour les prédictions.

Voici des exemples de types de prédictions que vous pouvez utiliser SQL Server Machine Learning Services pour, notamment :

|||
|-|-|
|Classification/catégorisation|Diviser automatiquement les commentaires client en catégories positives et négatives|
|Régression/prédire les valeurs continues|Prédire le prix des maisons en fonction de la taille et de l’emplacement|
|Détection d’anomalie|Détecter les transactions bancaires frauduleuses |
|Recommandations|Suggérer des produits que les acheteurs en ligne peuvent souhaiter acheter, en fonction de leurs achats précédents|

### <a name="how-to-execute-python-and-r-scripts"></a>Comment exécuter des scripts Python et R

Il existe deux façons d’exécuter des scripts Python et R dans Machine Learning Services :

+ La méthode la plus courante consiste à utiliser la procédure stockée T-SQL [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Vous pouvez également utiliser votre client python ou R préféré et écrire des scripts qui poussent l’exécution (appelée *contexte de calcul distant*) à une SQL Server distante. Pour plus d’informations, consultez Comment configurer un client de science des données pour le [développement python](python/setup-python-client-tools-sql.md) et le [développement R](r/set-up-a-data-science-client.md) .

<a name="packages"></a>

## <a name="python-and-r-packages"></a>Packages Python et R

Vous pouvez utiliser des infrastructures et des packages Open source, en plus des packages d’entreprise Microsoft. Les packages Python et R Open source les plus courants sont préinstallés dans Machine Learning Services. Les packages Python et R suivants de Microsoft sont également inclus :

| Langue | Package | Description |
|-|-|-|
| Python | [revoscalepy](python/ref-py-revoscalepy.md) | Le package principal pour Python évolutif. Transformations et manipulations de données, synthèse statistique, visualisation et nombreuses formes de modélisation. En outre, les fonctions de ce package distribuent automatiquement les charges de travail entre les cœurs disponibles pour un traitement parallèle. |
| Python | [microsoftml](python/ref-py-microsoftml.md) | Ajoute des algorithmes de Machine Learning pour créer des modèles personnalisés pour l’analyse de texte, l’analyse d’images et l’analyse des sentiments. | 
| R | [RevoScaleR](r/ref-r-revoscaler.md) | Package principal pour les transformations et manipulations R. Data extensibles, synthèse statistique, visualisation et nombreuses formes de modélisation. En outre, les fonctions de ce package distribuent automatiquement les charges de travail entre les cœurs disponibles pour un traitement parallèle. |
| R | [MicrosoftML (R)](r/ref-r-microsoftml.md) | Ajoute des algorithmes de Machine Learning pour créer des modèles personnalisés pour l’analyse de texte, l’analyse d’images et l’analyse des sentiments. |
| R | [olapR](r/ref-r-olapr.md) | Fonctions R utilisées pour les requêtes MDX sur un cube SQL Server Analysis Services OLAP. |
| R | [sqlrutils](r/ref-r-sqlrutils.md) | Mécanisme permettant d’utiliser des scripts R dans une procédure stockée T-SQL, d’enregistrer cette procédure stockée avec une base de données et d’exécuter la procédure stockée à partir d’un [environnement de développement R](r/set-up-a-data-science-client.md). |
| R | [Microsoft R Open](https://mran.microsoft.com/rro) | Microsoft R Open (MRO) est la distribution améliorée de R de Microsoft. Il s’agit d’une plateforme open source complète pour l’analyse statistique et la science des données. Il est basé sur R et totalement compatible avec ce langage, et il inclut des capacités supplémentaires pour améliorer les performances et la reproductibilité. |

Pour plus d’informations sur les packages installés avec Machine Learning Services et sur l’installation d’autres packages, consultez :

+ [Recevoir des informations sur le package Python](package-management/python-package-information.md)
+ [Installer des packages Python avec sqlmlutils](package-management/install-additional-python-packages-on-sql-server.md)
+ [Récupérer les informations du package R](package-management/r-package-information.md)
+ [Installez de nouveaux packages R avec sqlmlutils](package-management/install-additional-r-packages-on-sql-server.md).

## <a name="how-do-i-get-started-with-machine-learning-services"></a>Comment faire la prise en main de Machine Learning Services ?

1. [Installer SQL Server Machine Learning Services](install/sql-machine-learning-services-windows-install.md)

1. Configurez vos outils de développement. Vous pouvez utiliser les éléments suivants :

    + [Azure Data Studio](../azure-data-studio/what-is.md) ou [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) pour utiliser T-SQL et la procédure stockée [Sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour exécuter votre script Python ou R.
    + Python ou R sur votre propre ordinateur portable ou station de travail de développement pour exécuter des scripts. Vous pouvez extraire des données localement ou envoyer l’exécution à distance pour SQL Server avec [revoscalepy](python/ref-py-revoscalepy.md) et [RevoScaleR](r/ref-r-revoscaler.md). Pour plus d’informations, consultez Comment configurer un client de science des données pour le [développement python](python/setup-python-client-tools-sql.md) et le [développement R](r/set-up-a-data-science-client.md) .

1. Écrire votre premier script Python ou R

    + Démarrage rapide : Exécuter un script « Hello World » [dans python](tutorials/quickstart-python-run-using-t-sql.md) ou [R](tutorials/quickstart-r-run-using-tsql.md)
    + Démarrage rapide : Créer un modèle prédictif [dans python](tutorials/quickstart-python-train-score-in-tsql.md) ou [R](tutorials/quickstart-r-create-predictive-model.md)
    + Tutoriel : [Utilisation de Python dans T-SQL](tutorials/sqldev-in-database-python-for-sql-developers.md): Explorez les données, effectuez l’ingénierie des caractéristiques, formez et déployez des modèles, puis faites des prédictions (série de cinq parties)
    + Tutoriel : [Utilisez R dans T-SQL](tutorials/sqldev-in-database-r-for-sql-developers.md): Explorez les données, effectuez l’ingénierie des caractéristiques, formez et déployez des modèles, puis faites des prédictions (série de cinq parties)
    + Tutoriel : [Utilisez machine learning services dans les outils R](tutorials/walkthrough-data-science-end-to-end-walkthrough.md): Explorez les données, créez des graphiques et des tracés, effectuez l’ingénierie des caractéristiques, formez et déployez des modèles, puis Élaborez des prédictions (série en six parties)

## <a name="next-steps"></a>Étapes suivantes

+ [Installer SQL Server Machine Learning Services](install/sql-machine-learning-services-windows-install.md)
+ Configurer un client de science des données pour le [développement python](python/setup-python-client-tools-sql.md) et le [développement R](r/set-up-a-data-science-client.md)
