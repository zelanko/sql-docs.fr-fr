---
title: Didacticiels R et Python SQL Server
description: Exemples et didacticiels pour les scripts R et Python dans SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 9a212160c17e4cc3c8322af6026c9e2e4df97254
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343611"
---
# <a name="sql-server-machine-learning-tutorials-in-r-and-python"></a>Didacticiels de Machine Learning SQL Server dans R et Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fournit une liste complète de didacticiels et d’exemples de code illustrant les fonctionnalités Machine Learning de [SQL Server 2016 R services](../install/sql-r-services-windows-install.md) ou [SQL Server 2017 machine learning services](../install/sql-machine-learning-services-windows-install.md). 

+ Les Démarrages rapides utilisent des données intégrées ou aucune donnée pour une exploration rapide avec un minimum d’effort.
+ Les didacticiels vont plus loin avec davantage de tâches, des jeux de données plus volumineux et des explications plus longues.
+ Les exemples et solutions sont destinés aux développeurs qui préfèrent commencer à utiliser du code, revenir à des concepts et leçons pour combler les lacunes de connaissances.

Vous allez apprendre à utiliser des bibliothèques R et Python avec des données relationnelles résidentes dans le même contexte opérationnel, à utiliser des SQL Server des procédures stockées pour exécuter et à déployer du code personnalisé, et à appeler les bibliothèques Microsoft R et Python pour des données hautes performances. tâches scientifiques et Machine Learning.

Dans un premier temps, passez en revue les concepts fondamentaux de l’intégration de R et Python de Microsoft avec SQL Server.

## <a name="concepts"></a>Concepts

L’analytique dans la base de données fait référence à la prise en charge native de R et Python sur SQL Server lorsque vous installez SQL Server Machine Learning Services ou SQL Server 2016 R services (R uniquement) en tant que module complémentaire du moteur de base de données. L’intégration de R et Python comprend des distributions Open source de base, ainsi que des bibliothèques spécifiques à Microsoft pour une analyse haute performance.

À partir d’un point de vue d’architecture, votre code s’exécute en tant que processus externe sur la zone afin de préserver l’intégrité du moteur de base de données. Toutefois, l’accès aux données et la sécurité s’effectuent via SQL Server rôles et autorisations de base de données, ce qui signifie que toute application ayant accès à SQL Server peut accéder à votre script R et Python quand vous le déployez en tant que procédure stockée, ou sérialiser et enregistrer un modèle formé dans SQL Base de données du serveur.

Les principales différences entre la prise en charge de R et Python sur les SQL Server et la prise en charge de langage équivalente dans d’autres produits et services Microsoft sont les suivantes:

+ Capacité à «empaqueter» du code dans des procédures stockées ou en tant que modèles binaires.
+ Écrivez du code qui appelle les bibliothèques Microsoft R et Python installées localement avec les fichiers programme SQL Server.
+ Appliquez l’architecture de sécurité de la base de données de SQL Server à vos solutions R et Python.
+ Tirez parti de SQL Server infrastructure et de la prise en charge administrative de vos solutions personnalisées.

## <a name="quickstarts"></a>Démarrages rapides

Commencez ici pour découvrir comment exécuter R ou python à partir de T-SQL et comment mettre en œuvre votre code R et Python pour un environnement de production SQL.

+ [Software Exécuter Python à l’aide de T-SQL](run-python-using-t-sql.md)
+ [R Hello World dans R et SQL](rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R Gérer les entrées et les sorties](rtsql-working-with-inputs-and-outputs.md)
+ [R Gérer les types de données et les objets](rtsql-r-and-sql-data-types-and-data-objects.md)
+ [R Utilisation des fonctions R](rtsql-using-r-functions-with-sql-server-data.md)
+ [R Créer un modèle prédictif](rtsql-create-a-predictive-model-r.md)
+ [R Prédire et tracer à partir du modèle](rtsql-predict-and-plot-from-model.md)

## <a name="tutorials"></a>Tutoriels

Tirez parti de votre première expérience avec R et Python et T-SQL en examinant de plus près les packages Microsoft et les opérations plus spécialisées, telles que le décalage des contextes de calcul locaux à distants.

+ [Didacticiels Python](sql-server-python-tutorials.md)
+ [Didacticiels R](sql-server-r-tutorials.md)

<a name ="bkmk_samples"></a>

## <a name="samples"></a>Exemples

Ces exemples et démonstrations fournis par l’équipe de développement SQL Server et R Server mettent en évidence des moyens d’utiliser des analyses incorporées dans des applications réelles.

| Lien | Description | 
|------|-------------|
| [Effectuer un clustering des clients à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Utilisez l’apprentissage non supervisé pour segmenter les clients en fonction des données de ventes. Cet exemple utilise l’algorithme rxKmeans Scalable de Microsoft R pour créer le modèle de clustering. |
| [Effectuer un clustering client à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Découvrez comment utiliser l’algorithme KMeans pour effectuer un clustering de clients non supervisé. Cet exemple utilise le langage Python dans la base de données.| SQL Server 2017 |
| [Créer un modèle prédictif à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Découvrez comment une entreprise de location de ski peut utiliser Machine Learning pour prédire les futurs loyers, ce qui aide le plan et le personnel de l’entreprise à répondre à la demande future. Cet exemple utilise les algorithmes Microsoft pour créer des modèles de régression logistique et d’arbres de décision. | 
| [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Créez l’application d’analyse de location de ski à l’aide de Python pour aider à planifier les demandes futures. Cet exemple utilise la nouvelle bibliothèque Python, **revoscalepy**, pour créer un modèle de régression linéaire. | 

<a name="bkmk_solutions"></a>

## <a name="solution-templates"></a>Modèles de solution

L’équipe Microsoft de la science des données a fourni des modèles de solution personnalisables qui peuvent être utilisés pour lancer des solutions pour des scénarios courants. Chaque solution est adaptée à une tâche ou à un problème de secteur spécifique. La plupart des solutions sont conçues pour s’exécuter dans SQL Server ou dans un environnement Cloud tel que Azure Machine Learning. D’autres solutions peuvent s’exécuter sur Linux ou dans des clusters Spark ou Hadoop à l’aide de Microsoft R Server ou Machine Learning Server.

Tout le code est fourni, ainsi que des instructions sur la façon d’effectuer l’apprentissage et le déploiement d’un modèle pour l’évaluation à l’aide de SQL Server procédures stockées.

+ [Détection des fraudes](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [Prédiction d’évolution personnalisée](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [Maintenance prédictive](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Prédire la durée de séjour de l’hôpital](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

