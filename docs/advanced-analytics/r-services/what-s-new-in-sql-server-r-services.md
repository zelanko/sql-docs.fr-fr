---
title: "Nouveaut&#233;s de SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
caps.latest.revision: 36
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 35
---
# Nouveaut&#233;s de SQL Server R Services
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] est une fonctionnalité de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et SQL Server vNext qui prend en charge la science des données à l’échelle de l’entreprise.  R est le langage de programmation le plus utilisé pour l’analyse avancée, offre un ensemble de packages incroyablement riche et est associé à une communauté de développeurs dynamique et en pleine expansion. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] aide votre entreprise à adopter le très populaire langage R open source. 
  
 > [!TIP] Vous possédez déjà SQL Server 2016 R Services ?
 > À présent, vous pouvez installer la dernière version de Microsoft R Server sur vos instances 2016 pour tirer parti des mises à jour plus fréquentes des composants R. Pour plus d’informations, consultez l’article [Microsoft R Server 9.0.1](https://msdn.microsoft.com/microsoft-r/rserver-whats-new).  

## <a name="whats-new-in-sql-server-vnext"></a>Nouveautés de SQL Server vNext
  
+ Présentation du package **MicrosoftML**

   MicrosoftML est un nouveau package de Machine Learning pour R provenant des équipes Microsoft R Server et de science des données Microsoft. MicrosoftML offre vitesse accrue, performances et évolutivité pour gérer un corpus important de données texte et de données catégorielles comportant de nombreuses dimensions dans les modèles R avec seulement quelques lignes de code. En outre, les clients Microsoft R Server auront accès à cinq apprentissages rapides et très précis qui sont inclus dans Azure Machine Learning. 
   
   Pour plus d’informations, consultez [Utilisation du package MicrosoftML dans SQL Server R Services](../../advanced-analytics/r-services/using-the-microsoftml-package-with-sql-server-r-services.md).
   
+ Une gestion simplifiée des packages pour les spécialistes des données

  Vous n’avez plus à vous appuyer sur l’administrateur de base de données pour installer les packages R dont vous avez besoin sur SQL Server. Les nouvelles fonctions d’installation et de désinstallation de packages dans **RevoScaleR** vous permettent d’installer et de mettre à jour facilement des packages dans R Services à partir d’un ordinateur client. 
  
  Pour l’administrateur de base de données, les nouveaux rôles sont inclus dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] pour la gestion des autorisations associées aux packages, tant à l’échelle des instances qu’à l’échelle des bases de données. 
  
  Pour plus d’informations, consultez [Gestion des packages R pour SQL Server R Services](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 
     
+ Nouvelles fonctions dans **RevoScaleR** pour la lecture et l’écriture d’objets de modèle R

  RevoScaleR inclut désormais de nouvelles fonctions de sérialisation et un format de stockage de modèles plus compact pour accélérer le chargement et la lecture des modèles. 
  
  Pour plus d’informations, consultez [Enregistrer et charger des objets R à partir de SQL Server à l’aide d’ODBC](../../advanced-analytics/r-services/save-and-load-r-objects-from-sql-server-using-odbc.md). 

+ Package **sqlrutils** pour faciliter l’intégration SQL

  Ce package R vous permet de générer l’appel de procédure stockée SQL pour votre code R. Les procédures stockées SQL générées peuvent ensuite servir dans SQL Server R Services. Des exemples sont fournis pour vous aider à consolider votre code R en une fonction qui peut être paramétrée dans une procédure stockée SQL.
  
  Pour plus d’informations, consultez [Génération d’une procédure stockée pour du code R à l’aide du package sqlrutils](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md). 
  

+ Package **olapR** pour une connectivité SSAS facile

   Ce nouveau package fournit une nouvelle dimension de connectivité pour R et SQL Server Analysis Services, facilitant ainsi l’utilisation des données OLAP pour l’analyse dans R. Vous pouvez exécuter des requêtes MDX existantes et revenir à une trame de données R, ou créer des instructions MDX simples en définissant des axes de cube et des secteurs dans le code R. 
   
   Pour plus d’informations, consultez [Utilisation de données à partir de cubes OLAP dans R](../../advanced-analytics/r-services/using-data-from-olap-cubes-in-r.md).
   

  
## <a name="features-in-sql-server-2016-r-services-and-sql-server-vnext"></a>Fonctionnalités dans SQL Server 2016 R Services et SQL Server vNext  
  
- Package **RevoScaleR** pour un Machine Learning rapide et parallélisable avec R.

-   Prend en charge les connexions SQL et l’authentification Windows intégrée.  
    
-   Améliorations significatives des performances, notamment optimisation des processus SQL Satellite, qui connectent R et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], prise en charge des données de pagination pour permettre l’utilisation de données volumineuses et diffusion en continu pour permettre le traitement rapide de milliards de lignes. 
  
-   Utilisez des pools de ressources SQL Server pour gérer la mémoire utilisée par les processus R. Pour plus d’informations, consultez [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md).  
  

### <a name="tools-and-setup"></a>Outils et configuration

-   Configuration facile de tous les composants. L’assistant de configuration SQL Server peut installer **SQL Server R Services (dans la base de données)** ou le nouveau composant **Microsoft R Server (autonome)**.   Lorsque vous exécutez l’Assistant de configuration, choisissez R Services si vous configurez une instance SQL Server, et choisissez R Server (autonome) si vous configurez une station de travail de science des données.   Pour plus d’informations sur les options de configuration, consultez [Configurer SQL Server R Services &#40;dans la base de données&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md) ou [Créer un R Server autonome](../../advanced-analytics/r-services/create-a-standalone-r-server.md).  

-   Si vous n’avez pas besoin d’utiliser des données dans SQL Server, envisagez [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)], qui s’exécute sur un large éventail de plateformes et offre des performances de niveau entreprise du langage R open source populaire. [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)]. Pour plus d’informations, consultez [R Server &#40;autonome&#41;](../../advanced-analytics/r-services/r-server-standalone.md) ou [Présentation de R Server](https://msdn.microsoft.com/microsoft-r/rserver) sur MSDN.

- Pour mettre à niveau votre instance SQL Server 2016 pour utiliser Microsoft R Server 9.0.1, ayez recours à [l’utilitaire SqlBindR.exe](https://msdn.microsoft.com/library/mt791781.aspx).  

- [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-install) est un environnement R gratuit qui inclut l’ensemble des outils et bibliothèques dont vous aurez besoin pour créer des solutions R s’exécutant sur R Services ou R Server.  

-   Les outils R pour Visual Studio sont un plug-in gratuit pour Visual Studio avec prise en charge de R, notamment des fenêtres standard R interactives et des fenêtres variables, d’Intellisense pour les fonctions R, du débogage et de R Markdown, en plus de l’exportation vers Word et HTML.  Pour plus d’informations, consultez [R Tools pour Visual Studio](https://www.visualstudio.com/vs/rtvs/).  

## <a name="learn-more"></a>En savoir plus
  
-  Les ressources sont disponibles pour les experts des données qui souhaitent en savoir plus sur l’intégration de SQL Server et les développeurs qui souhaitent créer des solutions R à l’aide de T-SQL et de l’environnement familier de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 
   + [Didacticiels pour SQL Server R Services](https://msdn.microsoft.com/library/mt591993.aspx)
   + [Livre électronique gratuit : Science des données avec SQL Server 2016](https://mva.microsoft.com/ebooks/)
 
+ Si vous avez besoin de solutions prédéfinies, les [modèles de Machine Learning](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/) de l’équipe de science des données de Microsoft illustrent des solutions pratiques pour les tâches d’analyse courantes, notamment la maintenance prédictive et la prévention des désabonnements.
 

  
## <a name="see-also"></a>Voir aussi  
[Nouveautés de SQL Server vNext](../../sql-server/what-s-new-in-sql-server-vnext.md)
  