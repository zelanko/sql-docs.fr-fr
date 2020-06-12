---
title: PowerPivot pour SharePoint (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34a4cc6b16e22a20e0e8be3ded12b0465ba46eab
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84535121"
---
# <a name="powerpivot-for-sharepoint-ssas"></a>PowerPivot pour SharePoint (SSAS)
  PowerPivot pour SharePoint est un serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] exécuté en mode SharePoint. PowerPivot pour SharePoint permet l’hébergement de serveur de données PowerPivot dans une batterie de serveurs SharePoint. Les données PowerPivot sont un modèle de données analytiques que vous créez à l'aide de :  
  
-   Complément PowerPivot pour Excel 2010  
  
-   Excel 2013  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2010  
  
 L'hébergement sur serveur de ces données requiert SharePoint, Excel Services et une installation de PowerPivot pour SharePoint. Les données sont chargées sur les instances de PowerPivot pour SharePoint où elles peuvent être actualisées à des fréquences planifiées à l'aide de la fonction d'actualisation des données PowerPivot que le serveur fournit pour les classeurs Excel 2010, ou qu'Excel Services dans SharePoint 2013 fournit pour les classeurs Excel 2013.  
  
## <a name="powerpivot-for-sharepoint-2013"></a>PowerPivot pour SharePoint 2013  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]prend en charge [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 2013 Excel Services utilisation des classeurs Excel contenant des modèles de données et des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] rapports de Power View.  
  
 Excel Services dans SharePoint 2013 comprend la fonctionnalité de modèle de données qui permet l'interaction avec un classeur PowerPivot dans le navigateur. Vous n'avez pas besoin de déployer le complément PowerPivot pour SharePoint 2013 dans la batterie de serveurs. Vous devez uniquement installer un serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint et inscrire le serveur dans les paramètres **Modèle de données** d'Excel Services.  
  
 Le déploiement du complément PowerPivot pour SharePoint 2013 ajoute de nouvelles fonctionnalités à votre batterie de serveurs SharePoint. Les fonctionnalités supplémentaires comprennent la Galerie PowerPivot, l'actualisation des données de planification et le tableau de bord de gestion PowerPivot.  
  
 ![Déploiement de 2 serveurs en mode PowerPivot SSAS](../media/as-powerpivot-mode-2server-deployment.gif "Déploiement de 2 serveurs en mode PowerPivot SSAS")  
  
## <a name="powerpivot-for-sharepoint-2010"></a>PowerPivot pour SharePoint 2010  
 PowerPivot pour SharePoint 2010 assure l'hébergement des données PowerPivot dans une batterie de serveurs SharePoint 2010. Les données PowerPivot sont un modèle de données analytiques que vous créez dans Excel à l'aide du complément PowerPivot pour Excel. L'hébergement sur serveur de ces données requiert SharePoint 2010, Excel Services et une installation de PowerPivot pour SharePoint. Les données sont chargées dans les instances de PowerPivot pour SharePoint dans la batterie, où elles peuvent être actualisées à intervalles planifiés à l'aide de la fonctionnalité d'actualisation des données PowerPivot fournie par le serveur.  
  
### <a name="components-of-powerpivot-for-sharepoint-2010"></a>Composants de PowerPivot pour SharePoint 2010  
 PowerPivot pour SharePoint est implémenté en tant que service partagé, ce qui signifie que les fonctionnalités intégrées et l'infrastructure peuvent être utilisées pour administrer, sécuriser et utiliser une application de service PowerPivot. La découverte de serveur et de base de données, la redirection, et la gestion des connexions sont gérées au niveau de la batterie de serveurs. L'Administration centrale fournit l'interface d'administration des services utilisés pour gérer l'identité du serveur, l'état du serveur et les propriétés de configuration.  
  
 Un déploiement complet de PowerPivot pour SharePoint comprend des composants clients et serveurs qui s'intègrent à Excel et Excel Services dans une batterie de serveurs SharePoint. Les données PowerPivot situées dans un classeur Excel sont une base de données Analysis Services nécessitant un moteur d'analyse en mémoire xVelocity Analysis Services (VertiPaq) pour charger et interroger les données. Sur une station de travail cliente, le moteur xVelocity s'exécute dans un processus interne dans Excel. Dans une batterie de serveurs SharePoint, Analysis Services s'exécute sur un serveur d'applications où il est couplé aux services connexes qui gèrent les demandes de données PowerPivot. Le diagramme suivant illustre les composants PowerPivot clients et serveurs :  
  
 ![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")  
  
 Le service Web PowerPivot s'exécute sur un serveur d'applications Web. Il redirige les demandes de l'application Web vers une instance de service système PowerPivot dans la batterie.  
  
 Le service système PowerPivot transmet les demandes de charge au serveur Analysis Services et gère les connexions entrantes aux données déjà chargées en mémoire, en procédant à la mise en cache ou au déchargement des données si elles ne sont plus utilisées ou en cas de contention des ressources système. Il suit également l'activité des utilisateurs. Les données relatives à l'intégrité des serveurs et les autres données d'utilisation sont recueillies et présentées dans des rapports qui vous fournissent des informations sur les performances du système.  
  
 Une instance de serveur Analysis Service en mode intégré SharePoint complète le déploiement. Elle charge, interroge et décharge les données. Elle traite également les données si le classeur est configuré pour l'actualisation des données PowerPivot.  Chaque instance est étroitement associée au service système PowerPivot local qui fait partie de la même installation.  
  
##  <a name="in-this-section"></a><a name="bkmk_RelatedContent"></a> Dans cette section  
 [Administration et configuration d’un serveur PowerPivot dans l’Administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [Configuration de PowerPivot à l’aide de Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
 [Outils de configuration de PowerPivot](power-pivot-configuration-tools.md)  
  
 [Authentification et autorisation PowerPivot](power-pivot-authentication-and-authorization.md)  
  
 [Règles d'intégrité de PowerPivot - Configurer](configure-power-pivot-health-rules.md)  
  
 [Tableau de bord de gestion PowerPivot et données d’utilisation](power-pivot-management-dashboard-and-usage-data.md)  
  
 [Galerie PowerPivot](../../2014-toc/index.yml)  
  
 [Accès aux données PowerPivot](power-pivot-data-access.md)  
  
 [Actualisation des données PowerPivot](power-pivot-data-refresh.md)  
  
 [Flux de données PowerPivot](power-pivot-data-feeds.md)  
  
 [Connexion de modèle sémantique BI PowerPivot &#40;. BISM&#41;](power-pivot-bi-semantic-model-connection-bism.md)  
  
 **Sections connexes**  
  
## <a name="additional-topics"></a>Rubriques supplémentaires  
 [Mettre à niveau PowerPivot pour SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)  
  
 [PowerPivot for SharePoint 2013 Installation](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [Référence PowerShell pour PowerPivot pour SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
 [Exemples de topologies et coûts de licence pour SQL Server 2014 en libre-service Business Intelligence](../../sql-server/install/example-license-topologies-costs-self-service-business-intelligence.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Planification et déploiement de PowerPivot](https://go.microsoft.com/fwlink/?linkID=220972)   
 [Récupération d'urgence pour PowerPivot pour SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
