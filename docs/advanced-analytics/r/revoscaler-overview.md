---
title: RevoScaleR | Documents Microsoft
ms.custom: ''
ms.date: 11/29/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: fac746fbc9b880fdb2b97a69dffa402bf291c1f2
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2018
---
# <a name="revoscaler"></a>RevoScaleR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR est un ensemble de fonctions d’apprentissage machine, fourni par Microsoft, qui prend en charge pour la science des données à grande échelle.

+ Fonctions prennent en charge l’importation de données, de transformation de données, de synthèse, de visualisation et d’analyse.

+ _À l’échelle_ signifie que les opérations peuvent être exécutées sur des jeux de données très volumineux, en parallèle et distribuées sur des systèmes de fichiers. Algorithmes peuvent opérer sur des jeux de données qui ne tiennent pas dans la mémoire, à l’aide de segmentation et REASSEMBLAGE résultats une fois les opérations terminées.

+ RevoScaleR fournit de nombreuses améliorations sur les fonctions R open source. Il existe des fonctions RevoScaleR correspondant à la plupart des fonctions R plus populaires base. Les fonctions RevoScaleR sont signalées par un **rx** ou **Rx** préfixe pour les rendre plus faciles à identifier.

+ RevoScaleR sert à une plateforme pour la science des données distribuées. Par exemple, vous pouvez utiliser les contextes de calcul RevoScaleR et les transformations avec les algorithmes de pointe dans [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Vous pouvez également utiliser [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) pour exécuter les fonctions de base R en parallèle.

Pour obtenir des exemples de RevoScaleR en action, consultez les blogs : 

+ [Créer et déployer un modèle de prévision à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Prédictions d’un million par seconde avec le serveur de Machine Learning](https://blogs.msdn.microsoft.com/mlserver/2017/10/15/1-million-predictionssec-with-machine-learning-server-web-service/)

+ [Conseils de taxi prédiction à l’aide de MicrosoftML](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/01/17/predicting-nyc-taxi-tips-using-microsoftml/)

+ [Optimisation des performances avec rxExec](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/11/14/performance-optimization-when-using-rxexec-to-parallelize-algorithms/)

## <a name="how-to-get-revoscaler"></a>Obtention de RevoScaleR

Le package RevoScaleR pour R est installé gratuitement dans le Client Microsoft R. Si vous avez Machine Learning serveur ou que vous utilisez R dans SQL Server, RevoScaleR est inclus par défaut.

Si vous utilisez Python, le [revoscalepy](../python/what-is-revoscalepy.md) package fournit des fonctionnalités équivalentes.

> [!IMPORTANT]
> Le package RevoScaleR ne peut pas être téléchargé ou utilisé indépendamment les produits et services qui fournissent.

## <a name="use-revoscaler-in-sql-server"></a>Utiliser RevoScaleR dans SQL Server

Ces didacticiels et les exemples montrent comment utiliser les fonctions RevoScaleR pour obtenir des données à partir de SQL Server, de générer des modèles et d’enregistrer des modèles à une base de données pour calculer les scores.

+ [Apprenez à utiliser les contextes de calcul](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R pour les développeurs SQL : Train et effectuent un modèle](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Exemples de produits Microsoft sur GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)

## <a name="learn-more-about-revoscaler"></a>En savoir plus sur RevoScaleR

Ces didacticiels illustrent l’utilisation de RevoScaleR dans d’autres contextes de calcul pris en charge par [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), notamment Hadoop.

+ [Nouveautés RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler)

+ [Explorer RevoScaleR dans les 25 fonctions](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler)

+ [Référence de package RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)

