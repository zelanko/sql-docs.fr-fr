---
title: "SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: 38
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 36
---
# SQL Server R Services
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fournit une plateforme pour le développement et le déploiement d’applications intelligentes qui ouvrent de nouvelles perspectives. Vous pouvez utiliser le riche et puissant langage R ainsi que les nombreux packages de la communauté pour créer des modèles et générer des prédictions à l’aide de vos données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Étant donné que [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] intègre le langage R avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez conserver les analyses proches des données et éliminer les coûts et les risques de sécurité liés au déplacement des données.  
  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] prend en charge le langage R open source avec un ensemble complet d’outils et de technologies [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui offrent des performances, une sécurité, un fiabilité et une facilité de gestion supérieures. Vous pouvez déployer des solutions de R à l’aide d’outils pratiques et familiers, et vos applications de production peuvent appeler le runtime R et récupérer des prédictions et des visuels à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Vous obtenez également les bibliothèques [ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) afin d’améliorer la scalabilité et les performances de vos solutions R.  
  
Le programme d’installation de SQL Server vous permet d’installer les composants clients et serveur.  
  
+   **R Services (dans la base de données) :** installez cette fonctionnalité durant la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour activer l’exécution sécurisée des scripts R sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Quand vous activez cette fonctionnalité, des extensions sont installées dans le moteur de base de données pour prendre en charge l’exécution de scripts R et le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] est créé, qui gère les communications entre le runtime R et l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
+   **Microsoft R Server (autonome) :** distribution de R open source avec des packages propriétaires qui prennent en charge le traitement parallèle et d’autres améliorations des performances. R Services (en base de données) et Microsoft R Server (autonome) incluent tous deux les packages et le runtime R de base, ainsi que les bibliothèques **ScaleR** pour une connectivité et des performances améliorées. 
  
+    [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/index#mrc) est disponible en tant que programme d’installation distinct et gratuit.  Vous pouvez utiliser Microsoft R Client pour développer des solutions qui peuvent être déployées vers R Services exécuté sur SQL Server ou vers Microsoft R Server exécuté sur Windows, Teradata ou Hadoop. 
     

  > [!NOTE] Si vous devez exécuter votre code R dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], veillez à installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] comme décrit [ici](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).
  >  
  > Microsoft R Server \(autonome\) est une option distincte conçue pour l’utilisation des bibliothèques ScaleR sur un ordinateur Windows qui n’exécute pas SQL Server. 
>   
>  Toutefois, si vous avez Enterprise Edition, nous vous recommandons d’installer Microsoft R Server \(autonome\) sur un ordinateur portable ou un autre ordinateur utilisé pour le développement R, pour créer des solutions R qui peuvent être déployées facilement sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui exécute R Services \(en base de données\).
  
## <a name="additional-resources"></a>Ressources supplémentaires  
  
 [Prise en main de SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 Décrit des scénarios courants d’utilisation de R avec SQL Server.  
  
[Configurer SQL Server R Services (dans la base de données)](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
Installez R et les composants de base de données associés dans le cadre de l’installation de SQL Server.  
  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
Découvrez comment créer des sources de données SQL Server dans votre code R et comment utiliser des contextes de calcul à distance. D’autres didacticiels destinés aux développeurs SQL illustrent comment former et déployer un modèle R dans SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
  
 [Bien démarrer avec Microsoft R Server &#40;autonome&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
 
 [Configurer un serveur R autonome)](../../advanced-analytics/r-services/create-a-standalone-r-server.md) 
  