---
title: Installer les fonctionnalités BI de SQL Server 2014
ms.custom: ''
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.date: 10/24/2018
ms.technology: install
ms.openlocfilehash: 93f362adfbc85500854943a479dac01988eb3a01
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952560"
---
# <a name="install-sql-server-2014-bi-features"></a>Installer les fonctionnalités BI de SQL Server 2014

  Les fonctionnalités SQL Server qui font partie de la plateforme Business Intelligence de Microsoft sont notamment [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], ainsi que plusieurs applications clientes servant à créer ou utiliser des données analytiques. Cette section de la documentation du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] explique comment installer ces fonctionnalités.  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peuvent être installés comme serveurs autonomes, dans les configurations avec montée en puissance parallèle, ou comme applications de service partagé dans une batterie de serveurs SharePoint. L’installation des services dans une batterie permet d’activer les fonctionnalités BI disponibles seulement dans SharePoint, notamment [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint et [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], le concepteur de rapports interactifs ad hoc [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui s’exécute sur des bases de données du modèle tabulaire [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ou [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Si vous êtes déjà familiarisé avec les étapes d'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou PowerPivot pour SharePoint, passez aux listes de vérification pour obtenir de l'aide sur la manière d'activer des scénarios spécifiques. Pour plus d’informations, consultez [listes de vérification pour l’installation des fonctionnalités décisionnelles avec SharePoint](checklists-for-installing-bi-features-with-sharepoint.md).  
  
## <a name="contents"></a>Contents

Dans cette section :
  
|Lien|Tâche|  
|----------|----------|  
|[Listes de vérification pour installer des fonctionnalités BI avec SharePoint](checklists-for-installing-bi-features-with-sharepoint.md)|Si vous savez déjà ce que vous souhaitez installer et les étapes d'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint vous sont familières, utilisez les listes de vérification de cette section pour obtenir de l'aide sur l'ordre d'installation, la configuration requise pour les autorisations et les comptes, ainsi que les étapes de déploiement des topologies avancées, y compris les déploiements multiserveurs et multifonctionnalité.|  
|[Installer SQL Server fonctionnalités BI avec SharePoint &#40;PowerPivot et Reporting Services&#41;](install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)|Cette section explique comment installer les fonctionnalités de SQL Server dans un environnement SharePoint. Elle identifie les fonctionnalités SQL Server disponibles en fonction d'une version et d'une édition spécifiques de SharePoint. Elle inclut également des procédures d'installation de PowerPivot pour SharePoint et Reporting Services en mode SharePoint.|  
|[Installer Analysis Services en mode multidimensionnel et exploration de données](install-analysis-services-in-multidimensional-and-data-mining-mode.md)<br /><br /> [Installer Analysis Services en mode tabulaire](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)<br /><br /> [Installer Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)<br /><br /> [Installer Integration Services](../../integration-services/install-windows/install-integration-services.md)<br /><br /> [Installer Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)<br /><br /> [Installer le serveur de rapports Reporting Services en mode natif](../../reporting-services/install-windows/install-reporting-services-native-mode-report-server.md)|Cette section fournit des instructions d'installation pour Analysis Services, Integration Services, Master Data Services et Reporting Services, pour les installations d'Analysis Services et de Reporting Services sans SharePoint. Cette opération est parfois appelée *mode natif*et c’est le scénario d’installation le plus courant pour les Reporting Services et les Analysis Services. Dans cette section, vous découvrirez les options d'installation qui déterminent directement le contexte opérationnel de votre serveur. Pour Reporting Services, cela peut être un serveur qui est préconfiguré ou un qui requiert plusieurs étapes de configuration pour pouvoir l'utiliser. Pour Analysis Services, les options d'installation que vous sélectionnez déterminent le type de projet que vous pouvez déployer sur le serveur.|  
|[Vérifier l'installation de fonctionnalités SQL Server BI ou résoudre des problèmes liés](../../../2014/sql-server/install/verify-or-troubleshoot-sql-server-bi-feature-installation-problems.md)|Cette section présente les étapes pour vérifier une installation. Elle fournit également des liens vers des informations de dépannage sur le Web.|  
  
## <a name="related-content"></a>Contenu connexe  
  
|Lien|Tâche|  
|----------|----------|  
|[Mettre à niveau vers SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)<br /><br /> [Mettre à niveau Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)<br /><br /> [Mettre à niveau PowerPivot pour SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)<br /><br /> [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)|Utilisez les instructions de cette section pour mettre à niveau les serveurs et le contenu d'une version précédente vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|[Désinstaller SQL Server 2014](uninstall-sql-server.md)<br /><br /> [Désinstaller PowerPivot pour SharePoint](../../../2014/sql-server/install/uninstall-power-pivot-for-sharepoint.md)<br /><br /> [Désinstaller Reporting Services](../../../2014/sql-server/install/uninstall-reporting-services.md)|Utilisez les instructions de cette section pour désinstaller des fonctionnalités BI.|  
  
## <a name="see-also"></a>Voir aussi

* [Nouveautés &#40;Reporting Services&#41;](../../../2014/reporting-services/what-s-new-reporting-services.md)

* [Nouveautés dans Analysis Services et Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)

* [Installer SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)

* [Mettre à niveau vers SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)
