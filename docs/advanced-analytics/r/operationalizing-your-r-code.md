---
title: Faire fonctionner le code R à l’aide de procédures stockées - SQL Server Machine Learning Services
description: Incorporer le code de langage R dans une procédure stockée SQL Server pour le rendre disponible à toute application cliente ayant un accès à une base de données SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2b8e6a655ef96da042575a3b48809dbad1215242
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57976269"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>Faire fonctionner le code R à l’aide de procédures stockées dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Lorsque vous utilisez les fonctionnalités de R et Python dans SQL Server Machine Learning Services, l’approche la plus courante pour le déplacement des solutions dans un environnement de production est en incorporant le code dans les procédures stockées. Cet article résume les points clés pour les développeurs SQL à prendre en compte lors de la mise en place du code R à l’aide de SQL Server.

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>Déployer le script prête à l’aide de T-SQL et des procédures stockées

En règle générale, l’intégration de solutions de science des données est destinée à recoder étendu pour prendre en charge des performances et l’intégration. SQL Server Machine Learning Services simplifie cette tâche, car le code R et Python peut être exécuté dans SQL Server et appelé à l’aide de procédures stockées. Pour plus d’informations sur les mécanismes d’incorporer du code dans les procédures stockées, consultez :

+ [Démarrage rapide : Script R « Hello world » dans SQL Server](../../advanced-analytics/tutorials//quickstart-r-run-using-tsql.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

Vous trouverez un exemple plus détaillé de déploiement de code R en production à l’aide de procédures stockées dans [didacticiel : Analytique de données R pour les développeurs SQL](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>Recommandations pour l’utilisation de code R pour SQl

Conversion de votre code R dans SQL est plus facile si certaines optimisations sont effectuées au préalable dans le code R ou Python. Ceux-ci incluent en évitant les types de données qui provoquent des problèmes, en évitant les conversions de données inutiles et réécrire le code R comme un appel de fonction unique qui peut être facilement paramétré. Pour plus d'informations, consultez :

+ [Bibliothèques et types de données R](r-libraries-and-data-types.md)
+ [Conversion de code R pour une utilisation dans R Services](converting-r-code-for-use-in-sql-server.md)
+ [Utiliser des fonctions d’assistance de sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Intégrer R et Python avec les applications

Étant donné que vous pouvez exécuter R ou Python à partir d’une procédure stockée, vous pouvez exécuter des scripts à partir de n’importe quelle application qui peut envoyer une instruction T-SQL et gérer les résultats. Par exemple, vous pouvez reformer un modèle selon une planification à l’aide de la [tâche d’exécution de T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) dans Integration Services, ou en utilisant un autre planificateur de travaux pouvant s’exécuter une procédure stockée.

Calcul de score est une tâche importante qui peut facilement être automatisée, ou démarrée à partir d’applications externes. Vous former au préalable, à l’aide de R ou Python ou une procédure stockée, et [enregistrer le modèle au format binaire](../tutorials/walkthrough-build-and-save-the-model.md) à une table. Ensuite, le modèle peut être chargé dans une variable en tant que partie d’un appel de procédure stockée, à l’aide d’une des options suivantes pour calculer les scores à partir de T-SQL :

+ [En temps réel](../real-time-scoring.md) de score, optimisé pour les petits lots
+ Calculer les scores, pour l’appel d’une application de ligne unique
+ [Notation native](../sql-native-scoring.md), pour la prédiction rapide de lots à partir de SQL Server sans appeler R

Cette procédure pas à pas fournit des exemples de calcul de score à l’aide d’une procédure stockée dans le lot et les modes de ligne unique :

+ [Bout en bout de procédure pas à pas la science des données pour R dans SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Consultez ces modèles de solution pour obtenir des exemples montrant comment intégrer la notation dans une application :

+ [Prévisions de vente au détail](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Détection des fraudes](https://github.com/Microsoft/r-server-fraud-detection)
+ [Client de gestion de clusters](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Améliorer les performances et mise à l’échelle

Bien que le langage R open source a connu des limitations en ce qui concerne les jeux de données volumineux, le [API du package RevoScaleR](ref-r-revoscaler.md) inclus avec le Service SQL Server Machine Learning peuvent opérer sur les jeux de données volumineux et tirer parti multithread , les calculs de la base de données multicœurs et multiprocessus.

Si votre solution R utilise des agrégations complexes ou implique des jeux de données volumineux, vous pouvez tirer parti des agrégations en mémoire hautement efficaces de SQL Server et les index columnstore et laisser le code R les calculs statistiques et de notation.

Pour plus d’informations sur la façon d’améliorer les performances dans SQL Server Machine Learning, consultez :

+ [Optimisation des performances pour SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Conseils et astuces sur l’optimisation de performances](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Adapter le code R pour d’autres plateformes ou des contextes de calcul

Le code R que vous exécutez sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données peuvent être utilisées sur d’autres sources de données, tels que Spark sur HDFS, lorsque vous utilisez le [option de serveur autonome](../install/sql-machine-learning-standalone-windows-install.md) dans le programme d’installation de SQL Server ou lorsque vous installez le produit de marque non SQL, Microsoft Machine Learning Server (anciennement **Microsoft R Server**) :

+ [Documentation sur la machine Learning Server](https://docs.microsoft.com/r-server/)

+ [Explorez R revoscaler](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [Écrire des algorithmes de segmentation](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Calcul de big Data dans R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Développez votre propre algorithme parallèle](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

