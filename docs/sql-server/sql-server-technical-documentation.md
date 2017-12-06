---
title: Documentation SQL Server | Microsoft Docs
ms.date: 10/30/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-non-specified
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.portal.f1
helpviewer_keywords:
- documentation [SQL Server], home page
- Help [SQL Server]
- SQL Server, documentation
- home page [SQL Server]
- Help [SQL Server], documentation home page
- Books Online [SQL Server], home page
- portal page [SQL Server]
ms.assetid: 674933a8-e423-4d44-a39b-2a997e2c2333
caps.latest.revision: "106"
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 15e4d0a993dbc4b97413f94ccdb2620fc2baf24a
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-documentation"></a>Documentation SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server est un élément central de la plateforme de données Microsoft. SQL Server est un leader dans le secteur des systèmes de gestion de base de données opérationnelles (ODBMS). Cette documentation vous aide à installer, à configurer et à utiliser SQL Server. Le contenu inclut des exemples de bout en bout, des exemples de code et des vidéos. Pour connaître les rubriques relatives au langage SQL Server, consultez [Référence du langage](../t-sql/language-reference.md).

|Nouveautés  | Notes de publication  |
|---------|---------|
|[Nouveautés de SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)     | [Notes de publication de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)        |
|[Nouveautés de SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)     | [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)        |
|[Nouveautés de SQL Server 2014](https://msdn.microsoft.com/library/bb500435(v=sql.120).aspx)     | [SQL Server 2014 Release Notes](../sql-server/sql-server-2014-release-notes.md)        |
   
**Essayer SQL Server**

|||
|-|-|
|[![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=829477) [Télécharger SQL Server 2017](http://go.microsoft.com/fwlink/?LinkID=829477) | [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) [Télécharger SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) |
|[![Créer une machine virtuelle ](../includes/media/azure-vm.png)](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm) [Obtenir une machine virtuelle avec SQL Server](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm) | [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) [Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) |
| [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](../ssdt/download-sql-server-data-tools-ssdt.md) [Télécharger SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | |

    
## <a name="sql-server-technologies"></a>Technologies SQL Server    
    
|||    
|-|-|    
|![Moteur de base de données SQL](../sql-server/media/sql-database-engine.png "Moteur de base de données SQL")|**[Moteur de base de données](../database-engine/configure-windows/sql-server-database-engine.md)**<br /><br /> Le moteur de base de données est un service central qui permet de stocker, traiter et sécuriser les données. Il fournit des accès contrôlés et des traitements de transactions rapides pour répondre aux besoins des applications les plus gourmandes en données utilisées au sein des entreprises. Il offre également les fonctions nécessaires pour faire face à des besoins de haute disponibilité.|
|![Integration Services](../sql-server/media/integration-services.png "Integration Services")|**[Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est une plateforme permettant de créer des solutions d’intégration de données à hautes performances, y compris des packages qui autorisent les processus d’extraction, de transformation et de chargement (ETL) pour l’entreposage de données.|    
|![Analysis Services](../sql-server/media/analysis-services.png "Analysis Services")|**[Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> [!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] est une plateforme de données analytiques et un ensemble d'outils dédié au décisionnel personnel, en équipe et en entreprise. Les serveurs et concepteurs de clients prennent en charge des solutions OLAP traditionnelles, de nouvelles solutions de modélisation tabulaire, ainsi que des fonctionnalités d’analyse et de collaboration en libre-service grâce à [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], à Excel et à un environnement de serveur SharePoint. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] propose également l’exploration des données pour que vous puissiez découvrir les modèles et relations masqués à l’intérieur de grands volumes de données.|    
|![Reporting Services](../sql-server/media/reporting-services.png "Reporting Services")|**[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)**<br /><br /> Reporting Services fournit des fonctionnalités web de création de rapports d’entreprise.  Vous pouvez créer des rapports qui extraient du contenu de sources de données très diverses, publier des rapports dans différents formats et gérer de façon centralisée la sécurité et les abonnements.|
|![R Server](../sql-server/media/r-server.png "R Server")|**[Machine Learning Services](../advanced-analytics/r-services/r-services.md)**<br /><br /> Microsoft Machine Learning Services prend en charge l’intégration de la technologie Machine Learning, à l’aide des langages R et Python populaires, dans les workflows d’entreprise.<br /><br /> Machine Learning Services (dans la base de données) intègre R et Python à SQL Server, ce qui permet de générer, reformer et évaluer facilement les modèles en appelant des procédures stockées.  Microsoft Machine Learning Server fournit la prise en charge de R et Python à l’échelle de l’entreprise, sans nécessiter SQL Server.|
|![Data Quality Services](../sql-server/media/data-quality-services.png "Data Quality Services")|**[Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> SQL Server Data Quality Services (DQS) fournit une solution de nettoyage de données reposant sur des connaissances. DQS vous permet de générer une base de connaissances, puis utilise cette dernière pour effectuer la correction des données et la déduplication de vos données, à l'aide de moyens assistés par ordinateur et interactifs. Vous pouvez utiliser des services de données de référence en nuage, et vous pouvez générer une solution de gestion de données qui intègre DQS avec SQL Server Integration Services et Master Data Services.|
|![Services de réplication](../sql-server/media/replication-services.png "Services de réplication")|**[Réplication](../relational-databases/replication/sql-server-replication.md)**<br /><br /> La réplication repose sur un ensemble de technologies qui permettent de copier et de distribuer des données et des objets de base de données d'une base de données vers une autre, puis de synchroniser les bases de données afin de maintenir leur cohérence. Avec la réplication, vous pouvez distribuer des données vers différents emplacements et à des utilisateurs distants ou mobiles par l'intermédiaire de réseaux locaux ou étendus, de connexions d'accès à distance, de connexions sans fil et d'Internet.|
|![Master Data Services](../sql-server/media/master-data-services.png)|**[Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est la solution [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de gestion des données de référence. Une solution reposant sur [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] garantit que la création de rapports et l'analyse sont basées sur les informations adéquates. [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]vous permet de créer un référentiel central pour vos données de référence et de conserver un enregistrement vérifiable et sécurisable de ces données au fur et à mesure de leur modification.|

## <a name="migrate-and-move-data"></a>Migrer et déplacer les données
- [Importer et exporter des données avec l’Assistant Importation et Exportation SQL Server](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)
- [Assistant Migration de données Microsoft](https://www.microsoft.com/download/details.aspx?id=53595)
- [Migration d’une base de données SQL Server vers Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

## <a name="earlier-sql-server-versions"></a>Versions antérieures de SQL Server
- [Centre de mise à jour SQL Server - liens et informations pour toutes les versions prises en charge](https://msdn.microsoft.com/library/ff803383.aspx)
- [Documentation de SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx)
- [Documentation de SQL Server 2012](https://technet.microsoft.com/library/bb418433(v=sql.10).aspx)  
- [Documentation de SQL Server 2008 R2](https://msdn.microsoft.com/library/hh278298(v=sql.10).aspx)  
- [Documentation de SQL Server 2008](https://msdn.microsoft.com/library/hh994727(v=sql.10).aspx) 
- [Documentation archivée de SQL Server 2005](https://msdn.microsoft.com/library/hh278313(v=sql.10).aspx)    

## <a name="samples"></a>Exemples  
- [Exemple de base de données World Wide Importers](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx)  
- [Exemples de bases de données AdventureWorks et de scripts pour SQL Server 2016](https://www.microsoft.com/download/details.aspx?id=49502) 
- [Exemples SQL Server sur GitHub](https://github.com/Microsoft/sql-server-samples) 
   
[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
