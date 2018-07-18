---
title: Installer Analysis Services multidimensionnel et en Mode d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, about installing Analysis Services
- installing Analysis Services
- SSAS, installing
- Analysis Services, installing
- SQL Server Analysis Services, installing
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
caps.latest.revision: 47
author: heidisteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: d90380f1e908c3b0cf1226f94de4a404ae5e65e5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222579"
---
# <a name="install-analysis-services-in-multidimensional-and-data-mining-mode"></a>Installer Analysis Services en mode multidimensionnel et exploration de données
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] : fournit des fonctionnalités OLAP et d'exploration de données pour les applications de décisionnel. Dans cette version, la prise en charge pour les bases de données OLAP et des modèles d’exploration de données est disponible lorsque vous installez [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans *mode multidimensionnel*. Le mode multidimensionnel est l'un des trois modes serveur dans lequel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s'exécute. Il s'agit du mode par défaut. Si vous installez [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] avec les valeurs par défaut, vous obtiendrez une instance qui exécute des bases de données multidimensionnelles et des modèles d'exploration de données multidimensionnelles.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est un composant multi-instance, ce qui signifie que vous pouvez installer plusieurs instances d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur un même ordinateur ou exécuter une nouvelle instance d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] côte à côte avec une version antérieure. Le mode serveur est spécifique à une instance. L'utilisation d'autres modes requiert l'installation d'instances supplémentaires du serveur.  
  
 Vous pouvez installer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tout seul ou avec d'autres composants. Si vous installez simplement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les fonctionnalités suivantes sont installées lorsque vous sélectionnez **Analysis Services** dans la page Sélection des fonctionnalités de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Installation :  
  
-   Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour l'exécution des bases de données et modèles d'exploration de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   Fournisseurs de données utilisés pour l'accès aux données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aux bases de données sources  
  
-   Gestionnaire de configuration SQL Server  
  
## <a name="choosing-additional-features"></a>Choix des fonctionnalités supplémentaires  
 OLAP d'Analysis Services et les solutions d'entrepôt de données nécessitent l'installation d'autres composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre le développement, le déploiement et l'administration de bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les fonctionnalités supplémentaires suivantes sont des options pour un grand nombre de scénarios utilisateur classiques :  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], utilisé pour créer et visionner des structures de données Analysis Services et des modèles d’exploration de données.  
  
-   Composants connectivité des outils client utilisé pour la communication entre les clients et serveurs, notamment les bibliothèques réseau pour DB-Library, ODBC et OLE DB.  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)],  un ensemble d'objets graphiques et programmables permettant de déplacer, copier et transformer des données.  
  
-   Outils d'administration, y compris le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et le moniteur de réplication.  
  
## <a name="installation-tasks"></a>Tâches d'installation  
 Les tâches d'installation sont les suivantes :  
  
|Liens|Tâches|  
|-----------|-----------|  
|[Matérielle et logicielle requise pour l’installation de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) et [configurer les comptes de Service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).|Avant d'exécuter le programme d'installation, vérifier la configuration requise pour l'installation d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et déterminer le compte à utiliser pour configurer le serveur.|  
|[Installer SQL Server 2014 à partir de l’Assistant Installation &#40;le programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).|Exécuter le programme d'installation de SQL Server pour installer le logiciel.|  
|[Configurer le Pare-feu Windows pour autoriser l’accès à Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|Une fois l'installation terminée, vous devez configurer les paramètres de pare-feu de façon à autoriser les connexions à distance au serveur.|  
|[Autorisation de l’accès à des objets et des opérations &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)|Les utilisateurs qui accèdent aux bases de données Analysis Services doivent avoir l'autorisation de lecture d'au moins une base de données sur le serveur.|  
  
## <a name="related-content"></a>Contenu associé  
 Vous trouverez des informations supplémentaire sur l'installation dans les rubriques suivantes :  
  
 [Installer Analysis Services en mode tabulaire](../../analysis-services/instances/install-windows/install-analysis-services.md)  
  
 [Installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
 [Déterminer le mode serveur d'une instance Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
 [Compléments d’exploration de données SQL Server](http://go.microsoft.com/fwlink/?LinkId=197091)  
  
 Par défaut, les exemples de bases de données, les exemples de code et les compléments des applications clientes ne sont pas installés dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour installer les exemples de bases de données et les exemples de code, consultez le [site web CodePlex](http://go.microsoft.com/fwlink/?LinkId=87843).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473)   
 [Langues et classements &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md)   
 [Mettre à niveau Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
