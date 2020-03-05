---
title: Installer Analysis Services en mode multidimensionnel et d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, about installing Analysis Services
- installing Analysis Services
- SSAS, installing
- Analysis Services, installing
- SQL Server Analysis Services, installing
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
author: heidisteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: 002a4ce66108622ce5efcf33231edaed9cd1c99b
ms.sourcegitcommit: e914effe771a1ee323bb3653626cd4ba83d77308
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78280846"
---
# <a name="install-analysis-services-in-multidimensional-and-data-mining-mode"></a>Installer Analysis Services en mode multidimensionnel et exploration de données
  
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] : fournit des fonctionnalités OLAP et d'exploration de données pour les applications de décisionnel. Dans cette version, la prise en charge des bases de données OLAP et des modèles d’exploration [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de données est disponible lorsque vous installez en *mode multidimensionnel*. Le mode multidimensionnel est l'un des trois modes serveur dans lequel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s'exécute. Il s'agit du mode par défaut. Si vous installez [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] avec les valeurs par défaut, vous obtiendrez une instance qui exécute des bases de données multidimensionnelles et des modèles d'exploration de données multidimensionnelles.  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est un composant multi-instance, ce qui signifie que vous pouvez installer plusieurs instances d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur un même ordinateur ou exécuter une nouvelle instance d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] côte à côte avec une version antérieure. Le mode serveur est spécifique à une instance. L'utilisation d'autres modes requiert l'installation d'instances supplémentaires du serveur.  
  
 Vous pouvez installer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tout seul ou avec d'autres composants. Si vous installez uniquement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les fonctionnalités suivantes sont installées lorsque vous sélectionnez **Analysis Services** sur la page sélection de fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’Assistant Installation de :  
  
-   Serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour l'exécution des bases de données et modèles d'exploration de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   Fournisseurs de données utilisés pour l'accès aux données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aux bases de données sources  
  
-   Gestionnaire de configuration SQL Server  
  
## <a name="choosing-additional-features"></a>Choix des fonctionnalités supplémentaires  
 OLAP d'Analysis Services et les solutions d'entrepôt de données nécessitent l'installation d'autres composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre le développement, le déploiement et l'administration de bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les fonctionnalités supplémentaires suivantes sont des options pour un grand nombre de scénarios utilisateur classiques :  
  
-   
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], utilisé pour créer et visionner des structures de données Analysis Services et des modèles d’exploration de données.  
  
-   Composants Connectivité des outils clients utilisés pour la communication entre les clients et les serveurs, y compris les bibliothèques réseau pour DB-Library, ODBC et OLE DB.  
  
-   
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)],  un ensemble d'objets graphiques et programmables permettant de déplacer, copier et transformer des données.  
  
-   Outils d'administration, y compris le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et le moniteur de réplication.  
  
## <a name="installation-tasks"></a>Tâches d'installation  
 Les tâches d'installation sont les suivantes :  
  
|Liens|Tâches|  
|-----------|-----------|  
|[Configurations matérielle et logicielle requises pour installer SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) et [configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).|Avant d'exécuter le programme d'installation, vérifier la configuration requise pour l'installation d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et déterminer le compte à utiliser pour configurer le serveur.|  
|[Installez SQL Server 2014 à partir de l’Assistant installation &#40;&#41;d' ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)installation.|Exécuter le programme d'installation de SQL Server pour installer le logiciel.|  
|[Configurer le Pare-feu Windows pour autoriser l’accès à Analysis Services](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|Une fois l'installation terminée, vous devez configurer les paramètres de pare-feu de façon à autoriser les connexions à distance au serveur.|  
|[Autorisation de l’accès aux objets et opérations &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services)|Les utilisateurs qui accèdent aux bases de données Analysis Services doivent avoir l'autorisation de lecture d'au moins une base de données sur le serveur.|  
  
## <a name="related-content"></a>Contenu associé  
 Vous trouverez des informations supplémentaire sur l'installation dans les rubriques suivantes :  
  
 [Installer Analysis Services en mode tabulaire](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)  
  
 [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
 [Déterminer le mode serveur d’une instance de Analysis Services](https://docs.microsoft.com/analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance)  
  
 [Compléments d’exploration de données SQL Server](https://www.microsoft.com/download/details.aspx?id=35578)  
  
 Par défaut, les exemples de bases de données, les exemples de code et les compléments des applications clientes ne sont pas installés dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour installer les exemples de bases de données et les exemples de code, consultez le [site web CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473)   
 [Langues et classements &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md)   
 [Mettre à niveau Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
