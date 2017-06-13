---
title: Documentation technique de SQL Server | Documents Microsoft
ms.date: 03/24/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.portal.f1
helpviewer_keywords:
- documentation [SQL Server], home page
- Help [SQL Server]
- SQL Server, documentation
- home page [SQL Server]
- Help [SQL Server], documentation home page
- Books Online [SQL Server], home page
- portal page [SQL Server]
ms.assetid: 674933a8-e423-4d44-a39b-2a997e2c2333
caps.latest.revision: 106
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 6ba40fbd036ee6476d7eb3439a5d9e816e79651d
ms.contentlocale: fr-fr
ms.lasthandoff: 05/25/2017

---
# <a name="sql-server-technical-documentation"></a>Documentation technique de SQL Server
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 > Pour obtenir un contenu pour les versions précédentes de SQL Server, consultez [Installation de SQL Server 2014](https://msdn.microsoft.com/en-US/library/bb500469(SQL.120).aspx).

 Documentation d’aide à l’installation, à la configuration et à l’utilisation de SQL Server. Le contenu inclut des exemples de bout en bout, des exemples de code et des vidéos. Pour connaître les rubriques relatives au langage [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] , consultez l’article [Référence du langage](../t-sql/language-reference.md).

**SQL Server 2017**

- [Notes de mise à jour de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)
- [Quelles sont les nouveautés dans SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)
 
**SQL Server 2016 :**
 
- [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
- [Nouveautés de SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)
    
 **Essayer SQL Server**    
 - [**Télécharger SQL Server 2016 à partir du Centre d’évaluation**](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) 
 - **[Lancer une machine virtuelle sur laquelle SQL Server 2016 est déjà installé](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**    
 - **[Télécharger la dernière version de SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**   
      
## <a name="sql-server-technologies"></a>Technologies SQL Server    
    
|||    
|-|-|    
|![Moteur de base de données SQL](../sql-server/media/sql-database-engine.png "Moteur de base de données SQL")|**[Moteur de base de données](../database-engine/configure-windows/sql-server-database-engine.md)**<br /><br /> Le moteur de base de données est un service central qui permet de stocker, traiter et sécuriser les données. Il fournit des accès contrôlés et des traitements de transactions rapides pour répondre aux besoins des applications les plus gourmandes en données utilisées au sein des entreprises. Il offre également les fonctions nécessaires pour faire face à des besoins de haute disponibilité.|    
|![R Server](../sql-server/media/r-server.png "R Server")|**[R Services](../advanced-analytics/r-services/r-services.md)**<br /><br /> Microsoft R Services fournit plusieurs moyens d’intégrer le langage R populaire dans les workflows d’entreprise.<br /><br /> [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] intègre le langage R avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]pour simplifier la génération, le recyclage et l’évaluation des modèles en appelant des procédures stockées [!INCLUDE[tsql](../includes/tsql-md.md)] .<br /><br /> Microsoft R Server assure une prise en charge multi-plateforme et évolutive pour R à l’échelle de l’entreprise et prend en charge les sources de données telles que Hadoop et Teradata.|    
|![Data Quality Services](../sql-server/media/data-quality-services.png "Data Quality Services")|**[Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> SQL Server Data Quality Services (DQS) fournit une solution de nettoyage de données reposant sur des connaissances. DQS vous permet de générer une base de connaissances, puis utilise cette dernière pour effectuer la correction des données et la déduplication de vos données, à l'aide de moyens assistés par ordinateur et interactifs. Vous pouvez utiliser des services de données de référence en nuage, et vous pouvez générer une solution de gestion de données qui intègre DQS avec SQL Server Integration Services et Master Data Services.|    
|![Integration Services](../sql-server/media/integration-services.png "Integration Services")|**[Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est une plateforme permettant de créer des solutions d’intégration de données à hautes performances, y compris des packages qui autorisent les processus d’extraction, de transformation et de chargement (ETL) pour l’entreposage de données.|    
|![Master Data Services](../sql-server/media/master-data-services.png)|**[Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est la solution [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de gestion des données de référence. Une solution reposant sur [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] garantit que la création de rapports et l'analyse sont basées sur les informations adéquates. [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]vous permet de créer un référentiel central pour vos données de référence et de conserver un enregistrement vérifiable et sécurisable de ces données au fur et à mesure de leur modification.|    
|![Analysis Services](../sql-server/media/analysis-services.png "Analysis Services")|**[Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> [!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] est une plateforme de données analytiques et un ensemble d'outils dédié au décisionnel personnel, en équipe et en entreprise. Les serveurs et concepteurs de clients prennent en charge des solutions OLAP traditionnelles, de nouvelles solutions de modélisation tabulaire, ainsi que des fonctionnalités d’analyse et de collaboration en libre-service grâce à [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], à Excel et à un environnement de serveur SharePoint. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] propose également l’exploration des données pour que vous puissiez découvrir les modèles et relations masqués à l’intérieur de grands volumes de données.|    
|![Services de réplication](../sql-server/media/replication-services.png "Services de réplication")|**[Réplication](../relational-databases/replication/sql-server-replication.md)**<br /><br /> La réplication repose sur un ensemble de technologies qui permettent de copier et de distribuer des données et des objets de base de données d'une base de données vers une autre, puis de synchroniser les bases de données afin de maintenir leur cohérence. Avec la réplication, vous pouvez distribuer des données vers différents emplacements et à des utilisateurs distants ou mobiles par l'intermédiaire de réseaux locaux ou étendus, de connexions d'accès à distance, de connexions sans fil et d'Internet.|    
|![Reporting Services](../sql-server/media/reporting-services.png "Reporting Services")|**[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)**<br /><br /> Reporting Services fournit des fonctionnalités Web de création de rapports d'entreprise qui permettent d'extraire du contenu d'une large gamme de sources de données, de publier des rapports dans différents formats et de gérer de façon centralisée la sécurité et les abonnements.|    

    
## <a name="earlier-sql-server-versions"></a>Versions antérieures de SQL Server
- [Documentation en ligne de la documentation en ligne de SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx)
- [Installer SQL Server 2014 Express et d’autres versions plus anciennes de SQL Server](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx). (**Merci à [Scott Hanselman](http://www.hanselman.com/) d’avoir collecté et placé à un même endroit tous les liens vers les packages d’installation !**)  
- [Documentation technique de SQL Server 2012](https://technet.microsoft.com/library/bb418433(v=sql.10).aspx)  
- [Documentation produit de SQL Server 2008 R2](https://msdn.microsoft.com/library/hh278298(v=sql.10).aspx)  
- [Documentation technique de SQL Server 2008](https://msdn.microsoft.com/library/hh994727(v=sql.10).aspx) 
- [Documentation archivée de SQL Server 2005](https://msdn.microsoft.com/library/hh278313(v=sql.10).aspx)    

**Exemples de bases de données**  
- [Exemple de base de données World Wide Importers](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx)  
- [Exemples de bases de données AdventureWorks et de scripts pour SQL Server 2016](https://www.microsoft.com/en-us/download/details.aspx?id=49502) 
- [Exemples SQL Server sur GitHub](https://github.com/Microsoft/sql-server-samples) 
   
 ## <a name="more-information"></a>Informations complémentaires   
+ [Gestionnaire de configuration SQL Server](../relational-databases/sql-server-configuration-manager.md)
+ Liens du[Centre de mise à jour SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) et informations concernant toutes les versions prises en charge 
+ [Installer le moteur de base de données SQL Server](../database-engine/install-windows/install-sql-server-database-engine.md) 
+ [Installer les Outils d’administration SQL Server avec SSMS](https://msdn.microsoft.com/library/bb500441.aspx) 
+ [SQL Server Data Tools dans Visual Studio 2015](https://msdn.microsoft.com/mt186501.aspx)
+ [Vidéos, exemples et ressources communautaires](https://msdn.microsoft.com/library/dn237258.aspx)
  
[!INCLUDE[feedback_stackoverflow_msdn_connect-md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

