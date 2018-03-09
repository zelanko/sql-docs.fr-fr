---
title: "L’ordinateur SQL Server Learning Services | Documents Microsoft"
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: 37362b8a3f6d8b41fe6b52f8445b9ba08ca54aa3
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="sql-server-machine-learning-services"></a>SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 Machine Learning Services (précédemment SQL Server 2016 R Services) fournit une plateforme de développement et le déploiement d’applications intelligentes ouvrent de nouvelles perspectives. Étant donné que l’apprentissage est intégré à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez conserver analytique proches des données et éliminer les coûts et les risques de sécurité liés au déplacement des données.
  
+ Dans SQL Server 2016, vous pouvez facilement développer et déployer des solutions basées sur le langage R populaire pour la science des données. 

    Les fonctionnalités incluent le [Microsoft R](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) bibliothèques, qui fournissent des performances et évolutivité de nouveau pour vos solutions R et les algorithmes de pointe dans [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package).
+ Dans SQL Server 2017, vous pouvez utiliser R et Python pour développer et opérationnaliser les solutions de science des données. 

    Le [revoscalepy](../python/what-is-revoscalepy.md) bibliothèque pour Python fournit des contextes de calcul à distance et l’évolutivité comparable à celles de RevoScaleR.

SQL Server prend en charge l’amélioration des performances, la sécurité et facilité de gestion pour les charges de travail machine learning via un ensemble complet d’outils et technologies. Vous pouvez déployer R ou Python solutions à l’aide de la pratique, familiers SQL méthodologie et des outils. Il suffit d’utiliser [!INCLUDE[tsql](../../includes/tsql-md.md)] pour appeler les runtimes R ou Python à partir de vos applications de production, pour générer des modèles ou récupérer des éléments visuels. Si vous avez déjà effectué l’apprentissage un modèle, vous pouvez générer des prédictions à l’aide de T-SQL uniquement, via [score natif](../sql-native-scoring.md).

## <a name="machine-learning-in-sql-server-2017"></a>Apprentissage automatique dans SQL Server 2017

+ Installer **Machine Learning Services (de-de base de données)** pendant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation pour activer l’exécution sécurisée des scripts R ou Python sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur.
  
    Lorsque vous activez cette fonctionnalité, les extensions sont installées dans le moteur de base de données pour prendre en charge l’exécution du code écrit de R ou Python. Création d’un nouveau service, le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], pour gérer les communications entre les runtimes externes et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.
  
+ Installer **Microsoft Machine Learning Server (autonome)** sur un ordinateur distinct si vous n’avez pas besoin d’utiliser SQL Server en tant que le contexte de calcul. Machine Learning Server inclut les mêmes composants d’apprentissage machine, ainsi que la possibilité d’exécuter des tâches d’apprentissage machine distribuée, évolutive comme un service web.
  
+ Installer [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) sur des ordinateurs distants pour développer des solutions qui peuvent être déployées vers SQL Server, ou à la Machine Learning Server sur Windows, Linux ou Hadoop.

## <a name="machine-learning-in-sql-server-2016"></a>Apprentissage automatique dans SQL Server 2016

+ Installer **R Services (de-de base de données)** pendant l’installation de SQL Server 2016 pour activer l’exécution sécurisée des scripts R sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur.
  
    Lorsque vous activez cette fonctionnalité, vous obtenez la capacité à exécuter un script R à l’aide de SQL Server en tant que le contexte de calcul, ou pour exécuter le script R dans une procédure stockée.
  
+ Installer **Microsoft R Server (autonome)** du programme d’installation de SQL Server 2016, pour installer les composants R sur un ordinateur distinct que vous pouvez utiliser pour le développement ou déploiement de solutions de R.

## <a name="how-to-get-started"></a>La prise en main

Le programme d’installation de SQL Server fournit deux options :

+ Installation de l’analytique dans base de données de fonctionnalité qui est intégré à SQL Server, ou
+ Installez la version autonome d’apprentissage d’ordinateur serveur (ou Microsoft R Server) qui prend en charge d’apprentissage à grande échelle sans une instance de SQL Server.

Si vous avez besoin exécuter votre code R [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l’aide de procédures stockées ou à l’aide de l’instance SQL Server en tant que le contexte de calcul, vous devez installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] comme décrit dans la [guide d’installation](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md). Cette option fournit la sécurité des données et l’intégration avec les outils SQL Server.

Microsoft Machine Learning Server (autonome) est une option distincte destinée à l’aide de la [Microsoft R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) et [liés de bibliothèques de Python](../python/what-is-revoscalepy.md) sur un ordinateur Windows qui n’exécute pas SQL Server. Cette option requiert une licence Enterprise Edition pour SQL Server.
    
Nous vous recommandons d’installer Machine Learning Server (autonome) sur un ordinateur portable ou un autre ordinateur distant utilisé pour le développement et d’utiliser cet ordinateur pour créer et tester des solutions d’apprentissage qui peuvent facilement être déployées sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est Machine Learning Services en cours d’exécution \(dans base de données\) ou l’autre contexte de calcul pris en charge.
  
Vous pouvez également utiliser le **mrsdeploy** package qui est installé avec Machine Learning Server pour publier et distribuer des travaux R et Python comme un service web.

## <a name="additional-resources"></a>Ressources supplémentaires

+ [Prise en main de SQL Server Machine Learning Services](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)
 
    Décrit des scénarios courants d’utilisation du R avec SQL Server

+ [Configurer SQL Server Machine Learning Services ou R Services dans-base de données](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

    Installer R et les composants de base de données associée dans le cadre du programme d’installation de SQL Server
  
+ [Didacticiels de SQL Server et R](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Découvrez comment créer des sources de données SQL Server dans votre code R et comment utiliser des contextes de calcul à distance. D’autres didacticiels destinés aux développeurs SQL illustrent comment former et déployer un modèle R dans SQL Server.
