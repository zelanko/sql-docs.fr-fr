---
title: SQL Server Machine Learning Services Tutorials | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b692b9660c3caec18c689f56ba382f8df194a9cc
ms.sourcegitcommit: b1990ec4491b5a8097c3675334009cb2876673ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49384124"
---
# <a name="tutorials-for-sql-server-machine-learning-services"></a>Didacticiels pour SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fournit une liste complète des didacticiels, des démonstrations et des exemples d’applications qui utilisent des fonctionnalités d’apprentissage automatique dans SQL Server 2016 ou SQL Server 2017. Commencez ici pour découvrir comment exécuter R ou Python à partir de T-SQL, comment utiliser des contextes de calcul locaux et distants et comment optimiser votre code R et Python pour un environnement de production SQL.

+ [Didacticiels Python](../tutorials/sql-server-python-tutorials.md)

+ [Didacticiels R](../tutorials/sql-server-r-tutorials.md)

Pour plus d’informations sur les exigences et obtenir la configuration, consultez [conditions préalables](#bkmk_prerequisites).

## <a name="samples-and-solutions"></a>Exemples et solutions

+ [Exemples](#bkmk_samples) 

    Ces scénarios réalistes à partir de l’équipe de développement SQL Server montrent comment incorporer un apprentissage automatique dans les applications. Tous les exemples incluent le code que vous pouvez télécharger, modifier et utiliser en production.

+ [Solutions](#bkmk_solutions) 

    Les modèles à partir de l’équipe de science des données de Microsoft sont personnalisables, pour vous aider à démarrer rapidement avec l’apprentissage. Chaque solution est adaptée à un problème spécifique de tâche ou du secteur. La plupart des solutions est conçue pour s’exécuter dans SQL Server ou dans un environnement de cloud comme Azure Machine Learning. Autres solutions peuvent exécuter sur Linux ou dans les clusters Spark ou Hadoop, à l’aide de Microsoft R Server ou Machine Learning Server.

### <a name ="bkmk_samples"></a>Exemples de produit de SQL Server

Ces exemples et les démonstrations fournies par l’équipe de développement SQL Server et R Server mettez en surbrillance les façons dont vous pouvez utiliser analytique incorporée dans les applications réelles.

| Lien | Description | S'applique à |
|------|-------------|------------|
| [Exécuter le client clustering à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Utiliser l’apprentissage non supervisé pour segmenter les clients basés sur les données de ventes. Cet exemple utilise l’algorithme rxKmeans évolutive à partir de Microsoft R pour générer le modèle de clustering. | SQL Server 2016 ou SQL Server 2017 |
| [Exécuter le client clustering à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Découvrez comment utiliser l’algorithme de Kmeans pour effectuer la mise en cluster non supervisé des clients. Cet exemple utilise le langage Python-database.| SQL Server 2017 |
| [Créer un modèle prédictif à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Découvrez comment une entreprise de location de skis peut utiliser machine learning pour prédire les locations à venir, qui permet du plan d’activités et du personnel pour répondre à la demande future. Cet exemple utilise les algorithmes Microsoft pour générer des modèles d’arbres de décision et de régression logistique. | SQL Server 2016 ou SQL Server 2017 |
| [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Générez l’application d’analyse de location ski à l’aide de Python, pour faciliter la planification de la demande future. Cet exemple utilise la nouvelle bibliothèque Python, **revoscalepy**, pour créer un modèle de régression linéaire. | SQL Server 2017 |
| [Comment utiliser un Tableau avec SQL Server Machine Learning Services](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/) | Analyser les médias sociaux et créer des graphiques de Tableau, à l’aide de SQL Server et R. | SQL Server 2016 ou SQL Server 2017 |

### <a name="bkmk_solutions"></a>Modèles de solution

L’équipe de Science des données de Microsoft a fourni des modèles de solution qui peuvent être utilisées pour lancer rapidement des solutions pour les scénarios courants. Tout le code est fourni, ainsi que d’obtenir des instructions sur comment former et déployer un modèle pour calculer les scores à l’aide de procédures stockées SQL Server.

+ [Détection des fraudes](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [Prédiction d’évolution personnalisée](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [Maintenance prédictive](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Prédire la durée hôpital du séjour](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

Pour plus d’informations, consultez [Machine Learning Templates with SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/) (Modèles d’apprentissage automatique avec SQL Server 2016 R Services).

## <a name="more-resources-and-reading"></a>Plus de ressources et de lecture

+ [Pourquoi nous générez-le ?](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/01/10/sql-server-r-services-why-did-we-build-it/)

    Vous voulez savoir ce qui se cache derrière R Services ? Lisez cet article à partir de l’équipe de développement et PM qui explique l’origine et les objectifs de SQL Server R Services.

+ [Didacticiels et exemples de données pour Microsoft R](https://docs.microsoft.com/machine-learning-server/r/tutorial-introduction)

    Découvrez comment Microsoft R et proposées par le package RevoScaleR dans cette collection de didacticiels rapides. Apprenez à écrire le code R une seule fois et de déployer n’importe où, à l’aide de sources de données de RevoScaleR et les contextes de calcul distants.

+ [Prise en main MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)

  Découvrez comment utiliser les nouveaux algorithmes dans le package MicrosoftML pour la modélisation avancée et de transformations de données évolutive, optimisées pour plusieurs contextes de calcul.
