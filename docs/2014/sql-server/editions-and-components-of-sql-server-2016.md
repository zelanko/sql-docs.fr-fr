---
title: Éditions et composants de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Enterprise Edition [SQL Server]
- Developer Edition [SQL Server]
- 32-bit vs. 64-bit editions [SQL Server]
- default components
- Workgroup Edition [SQL Server]
- Internet servers [SQL Server]
- installing SQL Server, components
- Setup [SQL Server], components
- SQL Server, editions
- SQL Server, components
- client/server applications [SQL Server]
- editions [SQL Server]
- versions [SQL Server]
- Setup [SQL Server], editions
- SQL Server Installation Wizard
- components [SQL Server]
- Standard Edition [SQL Server]
- 64-bit edition [SQL Server]
- IIS [SQL Server]
- installing SQL Server, editions
- editions [SQL Server], about edition options
- Setup [SQL Server]
ms.assetid: e5186f02-dd91-47d0-8fa4-de3f41c76903
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6d3198f2d361726a3e17c152b259471062f6a297
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142189"
---
# <a name="editions-and-components-of-sql-server-2014"></a>Éditions et composants de SQL Server 2014
  La configuration requise pour l'installation varie selon vos besoins applicatifs. Les différentes éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'adaptent aux exigences de chaque organisation et de chaque individu en termes de performances, d'exécution et de prix. Les composants [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que vous installez dépendent également de vos exigences spécifiques. Les sections suivantes vous aident à choisir parmi les éditions et les composants disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="principal-editions-of-includesscurrentincludessscurrent-mdmd"></a>Principales éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Le tableau ci-dessous décrit les principales éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
|Édition de[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] |Définition|  
|---------------------------------------|----------------|  
|Enterprise (64 bits et 32 bits)|Offre Premium, l'édition [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise fournit des fonctions Datacenter avancées et complètes avec des performances ultra-rapides, une virtualisation illimitée et des fonctions Business Intelligence de bout en bout qui autorisent un haut niveau de service pour les charges de travail critiques et l'accès de l'utilisateur aux analyses de données.|  
|Business Intelligence (64 bits et 32 bits)|L'édition [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Business Intelligence fournit une plateforme complète autorisant les organisations à créer et déployer des solutions de BI sécurisées, évolutives et maniables. Il offre des fonctionnalités passionnantes telles que l’exploration de données et la visualisation ; basées sur un navigateur puissantes combinaison des fonctionnalités de données et de gestion de l’intégration améliorée.|  
|Standard (64 bits et 32 bits)|L'édition[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Standard permet la gestion des données de base et inclut une base de données Business Intelligence destinée aux services des grandes entreprises comme aux PME, leur permettant d'exécuter les applications et prenant en charge des outils de développement communs sur site et dans le cloud, pour une gestion efficace des bases de données avec des ressources informatiques minimales.|  
  
## <a name="specialized-editions-of-includesscurrentincludessscurrent-mdmd"></a>Éditions spécialisées de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Les éditions spécialisées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ciblent les différentes charges de travail de l'entreprise. Le tableau ci-dessous décrit les éditions spécialisées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|Édition de[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] |Description|  
|---------------------------------------|-----------------|  
|Web (64 bits et 32 bits)|L'édition Web[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] est une option offrant un coût total de possession faible destinée aux hébergeurs Web et aux VAP Web, fournissant des fonctions évolutives, rentables et gérables aux propriétés Web à petite ou grande échelle.|  
  
## <a name="breadth-editions-of-includesscurrentincludessscurrent-mdmd"></a>Éditions transversales de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Les éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] transverales sont conçues pour des scénarios clients spécifiques et sont offertes gratuitement ou à un coût nominal. Le tableau ci-dessous décrit les éditions transversales de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|Édition de[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] |Description|  
|---------------------------------------|-----------------|  
|Developer (64 bits et 32 bits)|L'édition[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Developer permet aux développeurs de créer des applications basées sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il inclut toutes les fonctionnalités de l'édition Enterprise, mais sa licence permet uniquement de l'utiliser comme un système de développement et de test, et non comme un serveur de production. L'édition [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Developer est la solution idéale pour le développement et le test d'applications.|  
|Express (64 bits et 32 bits)|L'édition [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Express est une édition de base comprenant une base de données gratuite, idéale pour découvrir et créer des applications bureatiques et de petites applications serveur pilotées par les données. C'est la solution idéale pour les éditeurs de logiciels, les développeurs et les amateurs de création d'applications clientes. Si vous avez besoin de fonctionnalités de base de données plus évoluées, vous pouvez mettre à niveau de manière transparente [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express vers des versions plus sophistiquées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La nouveauté de[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est Express LocalDB, une version allégée d'Express qui conserve toutes les fonctions de programmabilité de ce dernier, s'exécute en mode utilisateur, s'installe rapidement sans aucune configuration et n'exige que peu de conditions préalables.|  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-an-internet-server"></a>Utilisation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec un serveur Internet  
 Sur un serveur Internet, comme un serveur exécutant les services Internet (IIS), vous installez généralement les outils clients [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Les outils clients comprennent les composants de connectivité clients utilisés par une application qui se connecte à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Bien que vous puissiez installer une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un ordinateur exécutant les services Internet (IIS), ceci ne se fait en général que pour des sites Web de petite taille qui ne possèdent qu'un seul ordinateur serveur. La plupart des sites Web disposent de leur système IIS de niveau intermédiaire sur un serveur ou sur un cluster de serveurs, et de leurs bases de données sur un serveur distinct ou sur une fédération distincte de serveurs.  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-clientserver-applications"></a>Utilisation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec des applications client/serveur  
 Vous pouvez installer uniquement les composants clients de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un ordinateur exécutant des applications client/serveur qui se connectent directement à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Une installation de composants clients est également un bon choix si vous administrez une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un serveur de base de données ou si vous prévoyez de développer des applications [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 L'option d'outils clients installe les fonctionnalités suivantes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] : composants de compatibilité descendante, [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], composants de connectivité, outils d'administration, kit de développement logiciel et composants de la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [installer SQL Server 2014 à partir de l’Assistant Installation &#40;le programme d’installation&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
## <a name="deciding-among-includessnoversionincludesssnoversion-mdmd-components"></a>Choix des composants [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
 Utilisez la page de sélection de composant de l'Assistant Installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour sélectionner les composants à inclure dans une installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Par défaut, aucune des fonctionnalités incluses dans l'arborescence n'est sélectionnée.  
  
 Utilisez les informations des tableaux suivants pour déterminer le jeu de fonctionnalités qui répond le mieux à vos besoins.  
  
|Composants serveur|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] inclut le [!INCLUDE[ssDE](../includes/ssde-md.md)], le service principal de stockage, traitement et de sécurisation des données, réplication, recherche en texte intégral, outils de gestion relationnelles et XML et le [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] serveur (DQS).|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] inclut les outils de création et de gestion d’applications de traitement analytique en ligne (OLAP, OnLine Analytical Processing) et d’exploration de données.|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] inclut les composants serveur et clients permettant de créer, de gérer et de déployer des rapports tabulaires, de matrice, graphiques et de forme libre. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est également une plateforme évolutive que vous pouvez utiliser pour développer des applications de création de rapports.|  
|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] propose un ensemble d’outils graphiques et d’objets programmables permettant de déplacer, de copier et de transformer les données. Il inclut également le composant [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) pour [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) est la solution [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de gestion des données de référence. MDS peut être configuré pour gérer tout domaine (produits, clients, comptes) et inclut des hiérarchies, une sécurité granulaire, des transactions, la gestion des versions des données et les règles métier, ainsi que [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] , pouvant être utilisé pour gérer les données.|  
  
|Outils d'administration|Description|  
|----------------------|-----------------|  
|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] est un environnement intégré permettant d'accéder aux composants de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]en vue de les configurer, de les gérer, de les administrer et de les développer. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] permet aux développeurs et aux administrateurs de tous niveaux de compétence d'utiliser [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Gestionnaire de configuration|Le Gestionnaire de configuration[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] permet de gérer la configuration de base des services [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , des protocoles serveur et clients et des alias clients.|  
|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] fournit une interface utilisateur graphique qui permet d’analyser une instance du [!INCLUDE[ssDE](../includes/ssde-md.md)] ou d’ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|Assistant Paramétrage du[!INCLUDE[ssDE](../includes/ssde-md.md)] |L'Assistant Paramétrage du[!INCLUDE[ssDE](../includes/ssde-md.md)] permet de créer des ensembles d'index, des vues indexées et des partitions optimaux.|  
|Data Quality Client|Fournit une interface utilisateur graphique très facile et intuitive pour se connecter au serveur DQS et effectue des opérations de nettoyage des données. Il vous permet également de surveiller de façon centralisée différentes activités effectuées pendant l'opération de nettoyage des données.|  
|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] fournissent un environnement de développement intégré (IDE) permettant de générer des solutions pour les composants Business Intelligence : [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], et [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].<br /><br /> (Anciennement, Business Intelligence Development Studio.)<br /><br /> [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] inclut également des « projets de base de données », qui offrent un environnement intégré aux développeurs, afin qu'ils puissent mener à bien leurs travaux de création de bases de données quelle que soit la plateforme [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (sur site et hors site) dans Visual Studio. Les développeurs de bases de données peuvent utiliser l'explorateur de serveurs amélioré de Visual Studio pour créer ou modifier facilement des objets de base de données et des données, ou exécuter des requêtes.|  
|Composants de connectivité|Installe des composants permettant la communication entre les clients et les serveurs, et des bibliothèques réseau pour DB-Library, ODBC et OLE DB.|  
  
|Documentation|Description|  
|-------------------|-----------------|  
|Documentation en ligne[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] |Documentation de base de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Planification d'une installation SQL Server](install/planning-a-sql-server-installation.md)   
 [Installer SQL Server 2014 à partir de l’Assistant Installation &#40;le programme d’installation&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)  
  
  
