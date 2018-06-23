---
title: PowerPivot pour SharePoint (SSAS) | Documents Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1caed8888e1307950971914f48887facac409741
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050913"
---
# <a name="powerpivot-for-sharepoint-ssas"></a>PowerPivot pour SharePoint (SSAS)
  PowerPivot pour SharePoint est un serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] exécuté en mode SharePoint. PowerPivot pour SharePoint fournit le serveur qui héberge des données PowerPivot dans une batterie de serveurs SharePoint. Les données PowerPivot sont un modèle de données analytiques que vous créez à l'aide de :  
  
-   Complément PowerPivot pour Excel 2010  
  
-   Excel 2013  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010  
  
 L'hébergement sur serveur de ces données requiert SharePoint, Excel Services et une installation de PowerPivot pour SharePoint. Les données sont chargées sur les instances de PowerPivot pour SharePoint où elles peuvent être actualisées à des fréquences planifiées à l'aide de la fonction d'actualisation des données PowerPivot que le serveur fournit pour les classeurs Excel 2010, ou qu'Excel Services dans SharePoint 2013 fournit pour les classeurs Excel 2013.  
  
## <a name="powerpivot-for-sharepoint-2013"></a>PowerPivot pour SharePoint 2013  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] prend en charge l’utilisation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 2013 Excel Services pour gérer les classeurs Excel contenant des modèles de données et des rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Power View.  
  
 Excel Services dans SharePoint 2013 comprend la fonctionnalité de modèle de données qui permet l'interaction avec un classeur PowerPivot dans le navigateur. Vous n'avez pas besoin de déployer le complément PowerPivot pour SharePoint 2013 dans la batterie de serveurs. Vous devez uniquement installer un serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint et inscrire le serveur dans les paramètres **Modèle de données** d'Excel Services.  
  
 Le déploiement du complément PowerPivot pour SharePoint 2013 ajoute de nouvelles fonctionnalités à votre batterie de serveurs SharePoint. Les fonctionnalités supplémentaires comprennent la Galerie PowerPivot, l'actualisation des données de planification et le tableau de bord de gestion PowerPivot.  
  
 ![Déploiement de serveur SSAS PowerPivot Mode 2](../media/as-powerpivot-mode-2server-deployment.gif "déploiement de serveur SSAS PowerPivot Mode 2")  
  
## <a name="powerpivot-for-sharepoint-2010"></a>PowerPivot pour SharePoint 2010  
 PowerPivot pour SharePoint 2010 assure l'hébergement des données PowerPivot dans une batterie de serveurs SharePoint 2010. Les données PowerPivot sont un modèle de données analytiques que vous créez dans Excel à l'aide du complément PowerPivot pour Excel. L'hébergement sur serveur de ces données requiert SharePoint 2010, Excel Services et une installation de PowerPivot pour SharePoint. Les données sont chargées dans les instances de PowerPivot pour SharePoint dans la batterie, où elles peuvent être actualisées à intervalles planifiés à l'aide de la fonctionnalité d'actualisation des données PowerPivot fournie par le serveur.  
  
### <a name="components-of-powerpivot-for-sharepoint-2010"></a>Composants de PowerPivot pour SharePoint 2010  
 PowerPivot pour SharePoint est implémenté en tant que service partagé, ce qui signifie que les fonctionnalités intégrées et l'infrastructure peuvent être utilisées pour administrer, sécuriser et utiliser une application de service PowerPivot. La découverte de serveur et de base de données, la redirection, et la gestion des connexions sont gérées au niveau de la batterie de serveurs. L'Administration centrale fournit l'interface d'administration des services utilisés pour gérer l'identité du serveur, l'état du serveur et les propriétés de configuration.  
  
 Un déploiement complet de PowerPivot pour SharePoint comprend des composants clients et serveurs qui s'intègrent à Excel et Excel Services dans une batterie de serveurs SharePoint. Les données PowerPivot situées dans un classeur Excel sont une base de données Analysis Services nécessitant un moteur d'analyse en mémoire xVelocity Analysis Services (VertiPaq) pour charger et interroger les données. Sur une station de travail cliente, le moteur xVelocity s'exécute dans un processus interne dans Excel. Dans une batterie de serveurs SharePoint, Analysis Services s'exécute sur un serveur d'applications où il est couplé aux services connexes qui gèrent les demandes de données PowerPivot. Le diagramme suivant illustre les composants PowerPivot clients et serveurs :  
  
 ![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")  
  
 Le service Web PowerPivot s'exécute sur un serveur d'applications Web. Il redirige les demandes de l'application Web vers une instance de service système PowerPivot dans la batterie.  
  
 Le service système PowerPivot transmet les demandes de charge au serveur Analysis Services et gère les connexions entrantes aux données déjà chargées en mémoire, en procédant à la mise en cache ou au déchargement des données si elles ne sont plus utilisées ou en cas de contention des ressources système. Il suit également l'activité des utilisateurs. Les données relatives à l'intégrité des serveurs et les autres données d'utilisation sont recueillies et présentées dans des rapports qui vous fournissent des informations sur les performances du système.  
  
 Une instance de serveur Analysis Service en mode intégré SharePoint complète le déploiement. Elle charge, interroge et décharge les données. Elle traite également les données si le classeur est configuré pour l'actualisation des données PowerPivot.  Chaque instance est étroitement associée au service système PowerPivot local qui fait partie de la même installation.  
  
##  <a name="bkmk_RelatedContent"></a> Dans cette section  
 [Administration de serveur PowerPivot et de Configuration dans l’Administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [Configuration de PowerPivot à l’aide de Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
 [Outils de Configuration PowerPivot](power-pivot-configuration-tools.md)  
  
 [Authentification et autorisation PowerPivot](power-pivot-authentication-and-authorization.md)  
  
 [Règles de contrôle d’intégrité PowerPivot - configurer](configure-power-pivot-health-rules.md)  
  
 [Tableau de bord de gestion PowerPivot et les données d’utilisation](power-pivot-management-dashboard-and-usage-data.md)  
  
 [La galerie PowerPivot](../../2014-toc/books-online-for-sql-server-2014.md)  
  
 [Accès aux données PowerPivot](power-pivot-data-access.md)  
  
 [Actualisation des données PowerPivot](power-pivot-data-refresh.md)  
  
 [Flux de données PowerPivot](power-pivot-data-feeds.md)  
  
 [Connexion de modèle sémantique BI PowerPivot &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md)  
  
 **Sections connexes**  
  
## <a name="additional-topics"></a>Rubriques supplémentaires  
 [Mise à niveau PowerPivot pour SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)  
  
 [Installation PowerPivot pour SharePoint 2013](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [Référence PowerShell pour PowerPivot pour SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
 [Exemples de Topologies de licence et les coûts pour SQL Server 2014 Self-service Business Intelligence](../../sql-server/install/example-license-topologies-costs-self-service-business-intelligence.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Planification et déploiement PowerPivot](http://go.microsoft.com/fwlink/?linkID=220972)   
 [Récupération d’urgence pour PowerPivot pour SharePoint](http://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
