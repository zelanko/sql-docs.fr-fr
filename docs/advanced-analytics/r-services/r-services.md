---
title: "R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/20/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 341e80f5-3b59-4122-bbaa-969d7904297d
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 20
---
# R Services
  Microsoft R Services fournit deux plateformes serveurs d’intégration du langage R open source, très en vogue, avec les applications métiers : **SQL Server R Services (dans la base de données)**, pour l’intégration avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et **Microsoft R Server**.  
  
-   **R Services (dans la base de données)**  
  
     L'objectif de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] est de permettre un développement, un déploiement et une opérationnalisation rapides des solutions R fondées sur la plateforme [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les services associés.  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] transmet le calcul aux données en permettant à R de s’exécuter sur le même ordinateur que la base de données. Cela inclut un service de base de données qui s’exécute en dehors du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et communique de façon sécurisée avec le runtime R. Vous pouvez former des modèles R, créer des tracés R, effectuer l’évaluation et déplacer facilement des données entre R et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les scientifiques des données qui testent et développent des solutions peuvent communiquer avec le serveur à partir d’un ordinateur de développement distant pour exécuter du code R sur le serveur et déployer des solutions terminées sur SQL Server en incorporant des appels à R dans les procédures stockées.  
  
     Ce téléchargement inclut une distribution du langage R open source, ainsi que ScaleR, un ensemble de packages R très performants et évolutifs. Il comprend également des fournisseurs pour une connectivité plus facile et plus rapide avec toutes les technologies [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Pour plus d’informations, consultez [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md). Pour des exemples de scénarios, consultez [SQL Server R Services Tutorials](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md).  
  
-   **Microsoft R Server**  
  
     Ce système de serveur autonome prend en charge les solutions R évolutives et distribuées sur plusieurs plateformes et avec plusieurs sources de données d'entreprise, notamment Linux, Hadoop et Teradata.  
  
     Pour plus d'informations, consultez [Microsoft R Server (MSDN)](https://msdn.microsoft.com/microsoft-r/index).  
  
## <a name="related-technologies"></a>Technologies associées  
 Microsoft assure une vaste prise en charge de l'écosystème du langage R open source, notamment les outils, les fournisseurs, les packages R améliorées et les environnements de développement intégrés.  
  
-   **Outils R pour Visual Studio**  
  
     Visual Studio fournit un environnement de développement complet pour le langage R. Le plug-in inclut un éditeur, une fenêtre interactive, un outil de traçage, un débogueur et plus encore. Vous pouvez utiliser les langages .NET à partir de R ou appeler R à partir de .NET au moyen de bibliothèques open source comme R.NET et rClr.  
  
     Pour plus d’informations, consultez [R Tools pour Visual Studio](https://www.visualstudio.com/vs/rtvs/).  
  
-   **R dans Azure Machine Learning**  
  
     Créez votre propre espace de travail dans Azure Machine Learning Studio, d’où vous pouvez accéder à plus de 400 packages R préinstallés. Générez des modèles et effectuez l’apprentissage en vue d’un déploiement en tant que service web ou écrivez des scripts personnalisés pour transformer les données. Créez vos propres packages R, chargez-les vers Azure pour qu’ils s'exécutent sous forme de modules personnalisés et publiez des solutions sur [Machine Learning Marketplace](http://datamarket.azure.com/browse/data?category=machine-learning).  
  
     Pour plus d’informations, consultez [Prolonger votre expérience avec R](https://docs.microsoft.com/azure/machine-learning/machine-learning-extend-your-experiment-with-r) et [Créer des modules R personnalisés dans Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/machine-learning-custom-r-modules).  
  
-   **Machines virtuelles pour la science des données**  
  
     Vous pouvez déployer une version préinstallée et préconfigurée de [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] dans Microsoft Azure, qui vous permet de vous familiariser immédiatement avec l’exploration et la modélisation de données sur le cloud sans installer un système entièrement configuré localement.  
  
     Azure Marketplace contient plusieurs machines virtuelles qui prennent en charge la science des données :
     + La **machine virtuelle pour la science des données Microsoft** est configurée avec Microsoft R Server, ainsi que Python (distribution Anaconda), un serveur Jupyter Notebook, Visual Studio Community Edition, Power BI Desktop, le Kit de développement logiciel (SDK) Azure et SQL Server Express Edition. 
     + **Microsoft R Server 2016 pour Linux** contient la dernière version de R Server (version 9.0.1). Des machines virtuelles distinctes sont disponibles pour CentOS version 7.2 et Ubuntu version 16.04. 
     + La machine virtuelle **SQL Server 2016 Enterprise R Server Only** inclut un programme d’installation autonome pour R Server 9.0.1 qui prend en charge le nouveau modèle de licence de cycle de vie des logiciels modernes.
 

## <a name="see-also"></a>Voir aussi  
[Prise en main de SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md) 

[Prise en main de Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  

 [Installer le moteur de base de données SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)  
  
  