---
title: "L’ordinateur SQL Server Learning Services | Documents Microsoft"
ms.date: 11/09/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: "38"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: fb770b52f2cacfc527f6bb89955acfbda243c18a
ms.sourcegitcommit: ec5f7a945b9fff390422d5c4c138ca82194c3a3b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="sql-server-machine-learning-services"></a>SQL Server Machine Learning Services

  SQL Server 2017 Machine Learning Services (précédemment SQL Server 2016 R Services) fournit une plateforme de développement et le déploiement d’applications intelligentes ouvrent de nouvelles perspectives. Vous pouvez utiliser le riche et puissant langage R ainsi que les nombreux packages de la communauté pour créer des modèles et générer des prédictions à l’aide de vos données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
  Étant donné que l’apprentissage est intégré à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez conserver analytique proches des données et éliminer les coûts et les risques de sécurité liés au déplacement des données.
  
SQL Server prend en charge le langage R open source avec un ensemble complet d’outils et technologies qui offrent de meilleures performances, de sécurité, de fiabilité et de facilité de gestion. Vous pouvez déployer des solutions de R à l’aide des outils SQL pratiques et familiers, et vos applications de production peuvent appeler le runtime R et récupérer des prédictions et des éléments visuels à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Vous obtenez également les [Microsoft R](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) bibliothèques afin d’améliorer l’évolutivité et des performances de vos solutions R, y compris RevoScaleR, revoscalepy et MicrososftML.
  
Le programme d’installation de SQL Server vous permet d’installer les composants clients et serveur.
  
## <a name="machine-learning-in-sql-server-2017"></a>Apprentissage automatique dans SQL Server 2017

+ Installer **Machine Learning Services (de-de base de données)** pendant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation pour activer l’exécution sécurisée des scripts R ou Python sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur.
  
    Lorsque vous activez cette fonctionnalité, les extensions sont installées dans le moteur de base de données pour prendre en charge l’exécution du code écrit de R ou Python. Création d’un nouveau service, le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], pour gérer les communications entre les runtimes externes et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.
  
+ Installer **Microsoft Machine Learning Server (autonome)** sur un ordinateur distinct si vous n’avez pas besoin d’utiliser SQL Server en tant que le contexte de calcul. Machine Learning Server inclut les mêmes composants d’apprentissage machine, ainsi que la possibilité d’exécuter des tâches d’apprentissage machine distribuée, évolutive comme un service web.
  
+    Installer [Microsoft R Client](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client) sur des ordinateurs distants pour développer des solutions qui peuvent être déployées vers SQL Server, ou à la Machine Learning Server sur Windows, Linux ou Hadoop.

## <a name="machine-learning-in-sql-server-2016"></a>Apprentissage automatique dans SQL Server 2016

+ Installer **R Services (de-de base de données)** pendant l’installation de SQL Server 2016 pour activer l’exécution sécurisée des scripts R sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordinateur.
  
    Lorsque vous activez cette fonctionnalité, vous obtenez la capacité à exécuter un script R à l’aide de SQL Server en tant que le contexte de calcul, ou pour exécuter le script R dans une procédure stockée.
  
+   Installer **Microsoft R Server (autonome)** du programme d’installation de SQL Server 2016, pour installer les composants R sur un ordinateur distinct que vous pouvez utiliser pour le développement ou déploiement de solutions de R.


## <a name="which-type-of-machine-learning-service-do-i-need"></a>Le type de service de machine learning besoin ?

+ Si vous avez besoin exécuter votre code R [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l’aide de procédures stockées ou à l’aide de l’instance SQL Server en tant que le contexte de calcul, vous devez installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] comme décrit [ici](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).

+ Microsoft Machine Learning Server (autonome) est une option distincte destinée à l’aide de la [Microsoft R](https://docs.microsoft.com/r-server/r-reference/introducing-r-server-r-package-reference) et [liés de bibliothèques de Python](../python/what-is-revoscalepy.md) sur un ordinateur Windows qui n’exécute pas SQL Server. Il existe, toutefois, nécessite une licence Enterprise Edition pour SQL Server.
    
    Nous vous recommandons d’installer Microsoft Machine Learning Server (autonome) sur un ordinateur portable ou un autre ordinateur distant utilisé pour le développement et d’utiliser cet ordinateur pour créer et tester des solutions d’apprentissage machine qui peuvent facilement être déployées sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est en cours d’exécution Machine Learning Services \(dans base de données\) ou l’autre contexte de calcul pris en charge.
  
    Vous pouvez également utiliser le **mrsdeploy** package qui est installé avec Machine Learning Server pour publier et distribuer des travaux R et Python comme un service web.

## <a name="additional-resources"></a>Ressources supplémentaires

+ [Prise en main de SQL Server R Services](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)
 
    Décrit des scénarios courants d’utilisation du R avec SQL Server

+ [Configurer SQL Server R Services (dans la base de données)](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

    Installer R et les composants de base de données associée dans le cadre du programme d’installation de SQL Server
  
+ [Didacticiels pour SQL Server R](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Découvrez comment créer des sources de données SQL Server dans votre code R et comment utiliser des contextes de calcul à distance. D’autres didacticiels destinés aux développeurs SQL illustrent comment former et déployer un modèle R dans SQL Server.
