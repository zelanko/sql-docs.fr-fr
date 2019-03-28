---
title: Didacticiels SQL Server R et Python - SQL Server Machine Learning
description: Exemples et didacticiels pour R et Python dans SQL Server Machine Learning Services de script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2b30daadd23cbea244576c461ec783e67b2189cf
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511046"
---
# <a name="sql-server-machine-learning-tutorials-in-r-and-python"></a>Didacticiels de SQL Server Machine Learning dans R et Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fournit une liste complète des didacticiels et exemples de code illustrant les fonctionnalités d’apprentissage [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) ou [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md). 

+ Démarrages rapides utilisent des données intégré ou aucune donnée pour l’exploration rapide avec moins d’efforts.
+ Didacticiels aller plus loin avec plusieurs tâches, jeux de données volumineux et plus de temps des explications.
+ Solutions et des exemples sont destinés aux développeurs qui préfèrent pour démarrer avec le code, en travaillant pour les concepts et les leçons pour combler les lacunes de la base de connaissances.

Vous allez apprendre à utiliser les bibliothèques de R et Python avec des données relationnelles résidentes dans le même contexte opérationnel, l’utilisation de procédures stockées SQL Server pour l’exécution et le déploiement de code personnalisé et comment appeler Microsoft R et Python pour les données de hautes performances science et tâches d’apprentissage.

Dans un premier temps, passez en revue les concepts fondamentaux de Microsoft de sauvegarde intégration R et Python avec SQL Server.

## <a name="concepts"></a>Concepts

Dans la base de données analytique fait référence à la prise en charge native pour R et Python sur SQL Server lorsque vous installez SQL Server Machine Learning Services ou SQL Server 2016 R Services (R uniquement) comme un module complémentaire pour le moteur de base de données. Intégration de R et Python inclut base distributions open source, ainsi que des bibliothèques spécifiques à Microsoft pour l’analytique des performances élevées.

À partir d’un point de vue architecture, votre code s’exécute comme un processus externe dans la boîte pour préserver l’intégrité du moteur de base de données. Toutefois, toutes les données d’accès et sécurité via des rôles de base de données SQL Server et autorisations, ce qui signifie que n’importe quelle application ayant accès à SQL Server puissent accéder aux votre script R et Python lorsque vous déployez en tant que d’une procédure stockée, ou sérialisez et enregistrez un modèle formé dans une instance SQL Base de données du serveur.

Principales différences entre R et Python prennent en charge sur SQL Server par rapport à la prise en charge de langue équivalents dans d’autres produits Microsoft et les services incluent :

+ Possibilité de code « package » dans les procédures stockées ou en tant que modèles binaires.
+ Écrire du code qui appelle les bibliothèques Microsoft R et Python installés localement avec les fichiers de programme de SQL Server.
+ Appliquer l’architecture de sécurité de base de données du serveur SQL à vos solutions R et Python.
+ Exploiter l’infrastructure de SQL Server et la prise en charge administrative pour vos solutions personnalisées.

## <a name="quickstarts"></a>Démarrages rapides

Commencez ici pour découvrir comment exécuter R ou Python à partir de T-SQL et comment faire fonctionner votre code R et Python pour un environnement de production SQL.

+ [Python : Exécutez le code Python à l’aide de T-SQL](run-python-using-t-sql.md)
+ [R : Hello World dans R et SQL](rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R : Gérer les entrées et sorties](rtsql-working-with-inputs-and-outputs.md)
+ [R : Gérer des objets et des types de données](rtsql-r-and-sql-data-types-and-data-objects.md)
+ [R : Utilisation des fonctions R](rtsql-using-r-functions-with-sql-server-data.md)
+ [R : Créer un modèle prédictif](rtsql-create-a-predictive-model-r.md)
+ [R : Prédire et tracer à partir du modèle](rtsql-predict-and-plot-from-model.md)

## <a name="tutorials"></a>Didacticiels

Créez sur votre première expérience avec R et Python et T-SQL en prenant les examiner plus en détail les packages de Microsoft et les opérations plus spécialisées telles que le passage à partir de local à des contextes de calcul à distance.

+ [Didacticiels Python](sql-server-python-tutorials.md)
+ [Didacticiels R](sql-server-r-tutorials.md)

<a name ="bkmk_samples"></a>

## <a name="samples"></a>Exemples

Ces exemples et les démonstrations fournies par l’équipe de développement SQL Server et R Server mettez en surbrillance les façons dont vous pouvez utiliser analytique incorporée dans les applications réelles.

| Lien | Description | 
|------|-------------|
| [Exécuter le client clustering à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Utiliser l’apprentissage non supervisé pour segmenter les clients basés sur les données de ventes. Cet exemple utilise l’algorithme rxKmeans évolutive à partir de Microsoft R pour générer le modèle de clustering. |
| [Exécuter le client clustering à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Découvrez comment utiliser l’algorithme de Kmeans pour effectuer la mise en cluster non supervisé des clients. Cet exemple utilise le langage Python-database.| SQL Server 2017 |
| [Créer un modèle prédictif à l’aide de R et SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Découvrez comment une entreprise de location de skis peut utiliser machine learning pour prédire les locations à venir, qui permet du plan d’activités et du personnel pour répondre à la demande future. Cet exemple utilise les algorithmes Microsoft pour générer des modèles d’arbres de décision et de régression logistique. | 
| [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Générez l’application d’analyse de location ski à l’aide de Python, pour faciliter la planification de la demande future. Cet exemple utilise la nouvelle bibliothèque Python, **revoscalepy**, pour créer un modèle de régression linéaire. | 
| [Comment utiliser un Tableau avec SQL Server Machine Learning Services](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/) | Analyser les médias sociaux et créer des graphiques de Tableau, à l’aide de SQL Server et R. | 

<a name="bkmk_solutions"></a>

## <a name="solution-templates"></a>Modèles de solution

L’équipe de Science des données de Microsoft a fourni des modèles de solution personnalisable qui peuvent être utilisées pour lancer rapidement des solutions pour les scénarios courants. Chaque solution est adaptée à un problème spécifique de tâche ou du secteur. La plupart des solutions est conçue pour s’exécuter dans SQL Server ou dans un environnement de cloud comme Azure Machine Learning. Autres solutions peuvent exécuter sur Linux ou dans les clusters Spark ou Hadoop, à l’aide de Microsoft R Server ou Machine Learning Server.

Tout le code est fourni, ainsi que d’obtenir des instructions sur comment former et déployer un modèle pour calculer les scores à l’aide de procédures stockées SQL Server.

+ [Détection des fraudes](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [Prédiction d’évolution personnalisée](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [Maintenance prédictive](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Prédire la durée hôpital du séjour](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

Pour plus d’informations, consultez [Machine Learning Templates with SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/) (Modèles d’apprentissage automatique avec SQL Server 2016 R Services).

