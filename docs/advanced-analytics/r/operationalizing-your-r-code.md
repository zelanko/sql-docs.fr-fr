---
title: Rendre le code R opérationnel à l’aide de procédures stockées
description: Incorporez le code de langage R dans une procédure stockée SQL Server pour le rendre accessible à toute application cliente ayant accès à une base de données SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: adcac48bc7d90aae5f05a9b671f05e34cc8cf554
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715686"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>Rendre le code R opérationnel à l’aide de procédures stockées dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Lorsque vous utilisez les fonctionnalités R et Python dans SQL Server Machine Learning Services, l’approche la plus courante pour déplacer des solutions vers un environnement de production consiste à incorporer du code dans des procédures stockées. Cet article résume les points clés que le développeur SQL peut prendre en compte lors de la prise en compte du code R à l’aide de SQL Server.

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>Déployer un script prêt pour la production à l’aide de T-SQL et de procédures stockées

Traditionnellement, l’intégration de solutions de science des données impliquait un recodage extensif pour la prise en charge des performances et de l’intégration. SQL Server Machine Learning Services simplifie cette tâche, car le code R et Python peut être exécuté dans SQL Server et appelé à l’aide de procédures stockées. Pour plus d’informations sur le mécanisme d’incorporation de code dans des procédures stockées, consultez:

+ [Démarrage rapide : Script R «Hello World» dans SQL Server](../../advanced-analytics/tutorials//quickstart-r-run-using-tsql.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

Vous trouverez un exemple plus complet de déploiement du code R en production à l’aide des procédures stockées [dans le didacticiel: Analyse des données R pour les développeurs SQL](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>Instructions pour l’optimisation du code R pour SQl

La conversion de votre code R dans SQL est plus facile si certaines optimisations sont effectuées au préalable dans le code R ou python. Il s’agit notamment d’éviter les types de données qui provoquent des problèmes, d’éviter les conversions de données inutiles et de réécrire le code R comme un appel de fonction unique pouvant être facilement paramétré. Pour plus d'informations, consultez :

+ [Bibliothèques et types de données R](r-libraries-and-data-types.md)
+ [Conversion de code R pour une utilisation dans R services](converting-r-code-for-use-in-sql-server.md)
+ [Utiliser les fonctions d’assistance sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Intégrer R et Python aux applications

Étant donné que vous pouvez exécuter R ou python à partir d’une procédure stockée, vous pouvez exécuter des scripts à partir de n’importe quelle application qui peut envoyer une instruction T-SQL et gérer les résultats. Par exemple, vous pouvez reformer un modèle selon une planification à l’aide de la [tâche exécuter T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) dans Integration Services, ou à l’aide d’un autre planificateur de travaux qui peut exécuter une procédure stockée.

Le calcul des scores est une tâche importante qui peut facilement être automatisée ou démarrée à partir d’applications externes. Vous procédez à l’apprentissage préalable du modèle à l’aide de R ou python ou d’une procédure stockée, puis vous [Enregistrez le modèle au format binaire dans](../tutorials/walkthrough-build-and-save-the-model.md) une table. Ensuite, le modèle peut être chargé dans une variable dans le cadre d’un appel de procédure stockée, à l’aide de l’une de ces options pour la notation à partir de T-SQL:

+ [Notation en temps réel, optimisée pour les lots de petite taille
+ Notation à une seule ligne, pour appeler à partir d’une application
+ [Notation Native](../sql-native-scoring.md), pour une prédiction de lot rapide à partir de SQL Server sans appeler R

Cette procédure pas à pas fournit des exemples de notation à l’aide d’une procédure stockée à la fois dans les modes batch et une ligne:

+ [Procédure pas à pas de la science des données de bout en bout pour R dans SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Pour obtenir des exemples d’intégration de la notation dans une application, consultez les modèles de solution suivants:

+ [Prévisions de vente au détail](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Détection des fraudes](https://github.com/Microsoft/r-server-fraud-detection)
+ [Clustering des clients](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Améliorez les performances et la mise à l’échelle

Bien que le langage R Open source ait des limitations connues en ce qui concerne les jeux de données volumineux, les [API de package RevoScaleR](ref-r-revoscaler.md) incluses avec SQL Server Service machine learning peuvent fonctionner sur des jeux de données volumineux et tirer parti de l’utilisation de plusieurs threads, multicœurs, calculs dans les bases de données multiprocessus.

Si votre solution R utilise des agrégations complexes ou implique des jeux de données volumineux, vous pouvez tirer parti des agrégations ColumnStore et des agrégations en mémoire très efficaces de SQL Server, et laisser le code R gérer les calculs statistiques et le score.

Pour plus d’informations sur la façon d’améliorer les performances dans SQL Server Machine Learning, consultez:

+ [Réglage des performances pour SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Trucs et astuces d’optimisation des performances](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Adapter le code R pour d’autres plateformes ou contextes de calcul

Le même code R que vous exécutez sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des données peut être utilisé sur d’autres sources de données, telles que Spark sur HDFS, lorsque vous utilisez l' [option de serveur autonome](../install/sql-machine-learning-standalone-windows-install.md) dans SQL Server installation ou lorsque vous installez le produit non-SQL, Microsoft machine learning Serveur (précédemment appelé **Microsoft R Server**):

+ [Documentation Machine Learning Server](https://docs.microsoft.com/r-server/)

+ [Explorez R pour RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [Écrire des algorithmes de segmentation](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Calcul avec Big Data dans R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Développez votre propre algorithme parallèle](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

