---
title: Faire fonctionner le code R à l’aide de procédures stockées - SQL Server Machine Learning Services
description: Incorporer le code de langage R dans une procédure stockée SQL Server pour le rendre disponible à toute application cliente ayant un accès à une base de données SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3fc96e57fffb3e000a7e1a19887ed27651df9009
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432182"
---
# <a name="operationalize-r-code-machine-learning-services"></a>Faire fonctionner le code R (Machine Learning Services)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Les développeurs de base de données sont chargés d’intégrer plusieurs technologies et de les faire fonctionner ensemble afin que toute l’entreprise puisse en bénéficier. Le développeur de base de données fonctionne avec les développeurs d’applications, les développeurs SQL et aux chercheurs de données pour concevoir et déployer des solutions.

Cet article résume les points clés pour les développeurs de base de données prendre en compte lors de la mise en place du code R à l’aide de SQL Server.

## <a name="get-started-with-r-code-in-sql-server"></a>Bien démarrer avec le code R dans SQL Server

En règle générale, l’intégration des solutions machine learning est destinée à recoder étendu pour prendre en charge des performances et l’intégration. Toutefois, déplacement de code R et Python dans un environnement de production est beaucoup plus facile dans SQL Server Machine Learning Services, étant donné que le code peut être exécuté dans SQL Server et appelé à l’aide de procédures. Vous pouvez continuer à utiliser des outils familiers et que vous n’avez pas besoin d’installer un environnement de développement R. 

Pour plus d’informations sur la syntaxe de base, consultez :

+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
+ [À l’aide de code R dans SQL](../../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

Pour obtenir un exemple de comment vous pouvez déployer le code R en production à l’aide de procédures stockées, consultez :

+ [En base de données Analytique pour les développeurs SQL](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="optimize-your-r-code"></a>Optimiser votre code R

Bien sûr, il est plus facile si certaines optimisations sont effectuées au préalable dans le code R ou Python de convertir votre code R dans SQL. Ceux-ci incluent en évitant les types de données qui provoquent des problèmes, en évitant les conversions de données inutiles et réécrire le code R comme un appel de fonction unique qui peut être facilement paramétré. Pour plus d'informations, consultez :

+ [Bibliothèques et types de données R](r-libraries-and-data-types.md)

+ [Conversion de code R pour une utilisation dans R Services](converting-r-code-for-use-in-sql-server.md)

+ [Utiliser des fonctions d’assistance de sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Intégrer R et Python avec les applications

Étant donné que vous pouvez démarrer des Services Machine Learning à partir d’une procédure stockée, vous pouvez exécuter des scripts R ou Python à partir de n’importe quelle application qui peut envoyer une instruction T-SQL et gérer les résultats.

Par exemple, vous pouvez reformer un modèle selon une planification à l’aide de la tâche d’exécution de T-SQL dans Integration Services, ou à l’aide d’un autre planificateur de travaux pouvant s’exécuter une procédure stockée.

Calcul de score est une tâche importante qui peut facilement être automatisée, ou démarrée à partir d’applications externes. Vous formez le modèle au préalable, à l’aide de R ou Python ou une procédure stockée et que vous enregistrez le modèle au format binaire dans une table. Ensuite, le modèle peut être chargé dans une variable en tant que partie d’un appel de procédure stockée, à l’aide d’une des options suivantes pour calculer les scores à partir de T-SQL :

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

Bien que le langage open source R soit connu a ses limites, le package RevoScaleR API peuvent opèrent sur des jeux de données volumineux et tirer parti des calculs dans base de données multithreads, multicœurs et multiprocessus.

Si votre solution R utilise des agrégations complexes ou implique des jeux de données volumineux, vous pouvez tirer parti des agrégations en mémoire hautement efficaces de SQL Server et les index columnstore et laisser le code R les calculs statistiques et de notation.

Pour plus d’informations sur la façon d’améliorer les performances dans SQL Server Machine Learning, consultez :

+ [Optimisation des performances pour SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Conseils et astuces sur l’optimisation de performances](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Adapter le code R pour d’autres plateformes ou des contextes de calcul

Le code R que vous exécutez sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données peut être utilisées sur d’autres sources de données, telles que Hadoop et dans d’autres contextes de calcul.

Pour plus d’informations sur les plateformes prises en charge par Microsoft R, consultez :

+ [Introduction à Microsoft R](https://docs.microsoft.com/r-server/)

+ [Explorer RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

Pour plus d’informations sur la façon dont vous pouvez optimiser vos solutions de Microsoft R à exécuter sur les données de grande taille ou plusieurs plateformes, consultez :

+ [Écrire des algorithmes de segmentation](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Calcul de big Data dans R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Développez votre propre algorithme parallèle](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

