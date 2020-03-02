---
title: Déployer du code R dans les procédures stockées
description: Incorporez le code de langage R dans une procédure stockée SQL Server pour le rendre accessible à toute application cliente ayant accès à une base de données SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 15c3406d6745802ece620942bf51b23c4d3643ee
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727444"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>Faire fonctionner votre code R à l’aide des procédures stockées dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Lorsque vous utilisez les fonctionnalités R et Python dans SQL Server Machine Learning Services, l’approche la plus courante pour déplacer des solutions vers un environnement de production consiste à incorporer du code dans des procédures stockées. Cet article résume les points clés que le développeur SQL peut prendre en compte lorsqu’il fait fonctionner du code R à l’aide de SQL Server.

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>Déployer un script prêt pour la production à l’aide de T-SQL et de procédures stockées

Traditionnellement, l’intégration de solutions de science des données impliquait un recodage extensif pour la prise en charge des performances et de l’intégration. SQL Server Machine Learning Services simplifie cette tâche, car le code R et Python peuvent être exécutés dans SQL Server et appelés à l’aide de procédures stockées. Pour plus d’informations sur le mécanisme d’incorporation de code dans des procédures stockées, consultez :

+ [Créer et exécuter des scripts R simples dans SQL Server](../tutorials/quickstart-r-create-script.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

Vous trouverez un exemple plus complet de déploiement de code R en production à l’aide des procédures stockées dans [Tutoriel : analytique de données R pour les développeurs SQL](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>Recommandations pour l’optimisation du code R pour SQL

La conversion de votre code R dans SQL est plus facile si certaines optimisations sont effectuées au préalable dans le code R ou Python. Il s’agit notamment d’éviter les types de données qui provoquent des problèmes, d’éviter les conversions de données inutiles et de réécrire le code R comme un appel de fonction unique pouvant être facilement paramétré. Pour plus d'informations, consultez les pages suivantes :

+ [Bibliothèques et types de données R](r-libraries-and-data-types.md)
+ [Conversion de code R pour une utilisation dans R Services](converting-r-code-for-use-in-sql-server.md)
+ [Utiliser des fonctions d’assistance sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Intégrer R et Python aux applications

Étant donné que vous pouvez exécuter R ou Python à partir d’une procédure stockée, vous pouvez exécuter des scripts à partir de n’importe quelle application qui peut envoyer une instruction T-SQL et gérer les résultats. Par exemple, vous pouvez reformer un modèle selon une planification à l’aide de la [tâche Execute T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) dans Integration Services ou à l’aide d’un autre planificateur de travaux qui peut exécuter une procédure stockée.

Le scoring est une tâche importante qui peut facilement être automatisée ou démarrée à partir d’applications externes. Vous formez le modèle au préalable, en utilisant R ou Python ou une procédure stockée, et [enregistrer le modèle au format binaire](../tutorials/walkthrough-build-and-save-the-model.md) dans une table. Ensuite, le modèle peut être chargé dans une variable dans le cadre d’un appel de procédure stockée, à l’aide de l’une de ces options pour le scoring à partir de T-SQL :

+ [Scoring en temps réel, optimisé pour les lots de petite taille
+ Scoring sur une ligne, pour appeler à partir d’une application
+ [Scoring natif](../sql-native-scoring.md), pour la prédiction de lot rapide à partir de SQL Server sans appeler R

Cette procédure pas à pas fournit des exemples de scoring à l’aide d’une procédure stockée à la fois dans les modes par lot et sur une ligne :

+ [Procédure pas à pas de la science des données de bout en bout pour R dans SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Pour obtenir des exemples d’intégration du scoring dans une application, consultez les modèles de solution suivants :

+ [Prévisions de ventes](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Détection des fraudes](https://github.com/Microsoft/r-server-fraud-detection)
+ [Clustering client](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Stimuler les performances et mettre à l'échelle

Si le langage R open source a des limites bien connues concernant les jeux de données volumineux, les [API du package RevoScaleR](ref-r-revoscaler.md) fournies avec SQL Server Machine Learning Service peuvent prendre en charge des jeux de données plus volumineux et tirer parti des calculs multithreads, multicœurs et multiprocessus au sein de la base de données.

Si votre solution R utilise des agrégations complexes ou des jeux de données volumineux, vous pouvez tirer parti des index columnstore et des agrégations en mémoire très efficaces de SQL Server, et utiliser le code R pour les calculs statistiques et les calculs de score.

Pour plus d’informations sur la façon de stimuler les performances dans SQL Server Machine Learning, consultez :

+ [Performance Tuning for SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md) (Réglage des performances pour SQL Server R Services)
+ [Trucs et astuces pour optimiser les performances](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Adapter le code R pour d’autres plateformes ou contextes de calcul

Le même code R que vous exécutez sur des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être utilisé sur d’autres sources de données, comme Spark sur HDFS, lorsque vous utilisez l’[option de serveur autonome](../install/sql-machine-learning-standalone-windows-install.md) dans l’installation de SQL Server ou lorsque vous installez le produit non-SQL, Microsoft Machine Learning Server (anciennement **Microsoft R Server**) :

+ [Machine Learning Server - Documentation](https://docs.microsoft.com/r-server/)

+ [Explorer R pour RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [Écrire des algorithmes de segmentation](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Calcul avec Big Data dans R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Développer votre propre algorithme parallèle](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

