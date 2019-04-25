---
title: Installer des fonctionnalités BI de SQL Server avec SharePoint (PowerPivot et Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 3166107c-30c2-468e-bb1b-bb42b79b37c3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1e391bc85bc74ac9bd7394161298b190426926ad
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62473467"
---
# <a name="install-sql-server-bi-features-with-sharepoint-powerpivot-and-reporting-services"></a>Installer des fonctionnalités SQL Server BI avec SharePoint (PowerPivot et Reporting Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peuvent être intégrés avec une batterie de serveurs Microsoft SharePoint pour activer les fonctionnalités Business Intelligence (BI) dans SharePoint. Les fonctionnalités incluent [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] est utilisé pour [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] accès aux données dans une batterie de serveurs SharePoint. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] est le moteur de données des classeurs créés dans [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour Excel et accessibles à partir d'une bibliothèque SharePoint. Une fois que vous avez enregistré un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans SharePoint, vous pouvez l'utiliser en tant que source de données des rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] .  
  
 Certaines étapes d'installation et de configuration requises pour SharePoint 2010 sont différentes des étapes requises pour SharePoint 2013. Certains des rubriques de cette section s'appliquent aux deux versions de SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 ![Remarque](../../../2014/reporting-services/media/rs-fyinote.png "Remarque") pour les notes de publication, consultez [SQL server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
##  <a name="bkmk_top"></a> Dans cette rubrique  
  
-   [Scénarios d’analyse Décisionnelle SQL Server et SharePoint 2013](#bkmk_bi_scenarios)  
  
-   [Vue d’ensemble de l’Installation](#bkmk_install_sharepoint2013_overview)  
  
## <a name="in-this-section"></a>Dans cette section  
 Outre les informations de cette rubrique, les rubriques associées suivantes sont disponible dans cette section.  
  
 [Topologies de déploiement pour les fonctionnalités SQL Server BI dans SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)  
  
 [Instructions d’utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
 [Listes de vérification pour installer des fonctionnalités BI avec SharePoint](../../../2014/sql-server/install/checklists-for-installing-bi-features-with-sharepoint.md)  
  
 [Installation en Mode SharePoint de Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  
  
 [Installation de PowerPivot pour SharePoint 2013](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [Installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
##  <a name="bkmk_bi_scenarios"></a> Scénarios d’analyse Décisionnelle SQL Server et SharePoint 2013  
 Cette section résume les différents niveaux des fonctionnalités BI que vous pouvez choisir d'installer et de configurer.  
  
 Excel Services dans SharePoint 2013 comprend la fonctionnalité de modèle de données qui permet l'interaction avec un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans le navigateur. Pour les fonctionnalités du modèle de données de base, vous n'avez pas besoin de déployer le complément [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 dans la batterie de serveurs. Vous devez uniquement installer un serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint et inscrire le serveur dans les paramètres **Modèle de données** d'Excel Services.  
  
 Le déploiement du complément [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 ajoute de nouvelles fonctionnalités à votre batterie de serveurs SharePoint. Les fonctionnalités supplémentaires comprennent la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , l'actualisation planifiée des données et le tableau de bord de gestion PowerPivot. Pour plus d'informations, reportez-vous au tableau.  
  
||Level|Fonctionnalités|Installer ou configurer|  
|-|-----------|--------------|--------------------------|  
|1|SharePoint uniquement|Fonctionnalités natives d'Excel Services|Excel Services et autres services fournis avec SharePoint Server 2013.|  
|**2**|SharePoint avec Analysis Services en mode SharePoint|Classeurs PowerPivot interactifs dans le navigateur|Installez [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint.<br /><br /> Inscrivez le serveur Analysis Services dans Excel Services.|  
|**3**|SharePoint avec Reporting Services en mode SharePoint|Power View|Installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.<br /><br /> Installez le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **(rsSharePoint.msi)** pour SharePoint. Pour plus d’informations, consultez [installer ou désinstaller le logiciel complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)|  
|**4**|Toutes les fonctionnalités de PowerPivot|Accédez aux classeurs comme source de données provenant de l'extérieur de la batterie.<br /><br /> Actualisation planifiée des données.<br /><br /> Galerie PowerPivot.<br /><br /> Tableau de bord de gestion.<br /><br /> Type de contenu de fichier de liaison BISM.|Déployez le complément PowerPivot pour SharePoint 2013 **(spPowerPivot.msi)**. Pour plus d'informations, consultez les documents suivants :<br /><br /> [Installer ou désinstaller le PowerPivot pour SharePoint Add-in &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)<br /><br /> Pour plus d'informations sur le téléchargement de **spPowerPivot.msi**, consultez [Télécharger SQL Server 2014 PowerPivot pour SharePoint](https://go.microsoft.com/fwlink/?LinkID=296473).|  
  
 Pour plus d’informations sur l’activation de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fonctionnalités, consultez [The SQL Server BI mise en évidence d’histoire pour SharePoint 2013](https://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx) (https://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx).  
  
##  <a name="bkmk_install_sharepoint2013_overview"></a> Vue d’ensemble de l’Installation  
 Si vous souhaitez utiliser [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], exécutez l'Assistant Installation de SQL Server deux fois. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sont des options distinctes sur le **rôle d’installation** page de l’Assistant d’installation de SQL Server.  
  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] prend en charge SharePoint 2010 et SharePoint 2013 ; cependant, une architecture et une procédure d'installation différentes sont utilisées en fonction de la version de SharePoint.  
  
 Vous trouverez ci-dessous un résumé des étapes d'installation pour déployer les fonctionnalités BI de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur un seul serveur :  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013**  
  
 Pour **SharePoint 2013**, l'installation de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] peut être exécutée sur un serveur sur lequel aucun produit SharePoint n'est installé. L'architecture de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] utilisée pour SharePoint 2013 s'exécute **en dehors** de la batterie de serveurs SharePoint et peut être installée sur un serveur qui contient également une installation de SharePoint ou sur un serveur qui NE contient PAS d'installation SharePoint.  
  
1.  Installez SharePoint Server 2013 et activez Excel Services.  
  
2.  Installez [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint, et accordez à la batterie SharePoint et aux comptes de services des droits d'administrateur de serveur dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Pour les deux versions de SharePoint, le processus d'installation de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] commence par la sélection du rôle d'installation de **SQL Server PowerPivot pour SharePoint** dans l'Assistant Installation de SQL Server ou en utilisant une installation à partir d'une invite de commandes SQL Server.  
  
     ![Rôle d’installation](../../../2014/sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "rôle d’installation")  
  
3.  Pour SharePoint 2013, vous pouvez étendre les fonctionnalités et l'expérience de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Téléchargez **spPowerPivot.msi** afin d'ajouter le traitement de l'actualisation des données côté serveur, la collaboration et la prise en charge de la gestion de classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Pour plus d'informations, consultez [Microsoft SQL Server 2014 PowerPivot pour Microsoft® SharePoint](https://go.microsoft.com/fwlink/?LinkID=324854).  
  
     Exécuter le package d'installation **spPowerPivot.msi** de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 sur chaque serveur de la batterie de serveurs SharePoint pour veiller à ce la version appropriée des fournisseurs de données soit installée.  
  
4.  Pour configurer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint 2013, utilisez l'outil **Configuration de PowerPivot pour SharePoint 2013** .  
  
     L'Assistant Installation de SQL Server installe deux outils de configurations [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . L'un des outils de configuration prend en charge SharePoint 2013 et l'autre prend en charge SharePoint 2010.  
  
     ![Deux outils de configuration de PowerPivot](../../../2014/analysis-services/media/as-powerpivot-configtools-bothicons.gif "Deux outils de configuration de PowerPivot")  
  
5.  Configurez Excel Services dans SharePoint Server 2013 de façon à utiliser l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour plus d’informations, consultez la section « Configurer Analysis Services intégration SharePoint de base » dans [Installation PowerPivot pour SharePoint 2013](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).et [(SharePoint Server de paramètres de modèle de données de gérer les Services Excel 2013)](https://technet.microsoft.com/library/jj219780.aspx) (https://technet.microsoft.com/library/jj219780.aspx).  
  
6.  Pour plus d'informations, consultez [PowerPivot for SharePoint 2013 Installation](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010**  
  
 Pour SharePoint 2010, il est nécessaire que l'installation de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint s'exécute sur un serveur sur lequel SharePoint 2010 est déjà installé ou va être installé. L'architecture [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint 2010 s'exécute **à l'intérieur** de la batterie de serveurs et requiert SharePoint sur le serveur sur lequel [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint est installé.  
  
1.  Installez [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint, et accordez à la batterie SharePoint et aux comptes de services des droits d'administrateur de serveur dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Un déploiement SharePoint 2010 ne prend pas en charge spPowerPivot.msi, et le fichier .msi n'est **pas** nécessaire avec SharePoint 2010.  
  
     Pour les deux versions de SharePoint, le processus d'installation de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] commence par la sélection du rôle d'installation de **SQL Server PowerPivot pour SharePoint** dans l'Assistant Installation de SQL Server ou en utilisant une installation à partir d'une invite de commandes SQL Server.  
  
2.  L'Assistant Installation de SQL Server installe deux outils de configurations [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . L'un des outils de configuration prend en charge SharePoint 2013 et l'autre prend en charge SharePoint 2010.  
  
     Pour configurer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint 2010, utilisez l' **outil de configuration de PowerPivot** .  
  
3.  Pour plus d'informations, consultez [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md).  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**  pour SharePoint 2010 et 2013  
  
1.  L'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint est inchangée par rapport à la version précédente.  
  
     Les étapes d'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint 2010 et SharePoint 2013 sont très similaires. Remarques importantes concernant les versions de SharePoint :  
  
    -   Consultez les combinaisons prises en charge des éléments suivants :  
  
        -   Version de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
        -   Complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint.  
  
        -   Version du produit SharePoint.  
  
         [Prise en charge les combinaisons de SharePoint et Reporting Services serveur et complément &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
    -   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur SharePoint 2010 nécessite SharePoint 2010 Service Pack 2 (SP2).  
  
    1.  Installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint. [Installation en Mode SharePoint de Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41; ](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md) et [installer Reporting Services en Mode SharePoint pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
    2.  Configurez le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint (rsSharePoint.msi). Consultez [installer ou désinstaller le complément Services Reporting pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Pour la version actuelle de la [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] complément pour SharePoint, consultez [où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
    3.  Configurez le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint et créez au moins une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations, consultez la section « Créer une Application Reporting Services Service » dans [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).  
  
##  <a name="bkm_database_attach"></a> Vue d’ensemble de l’attacher à la base de données mise à niveau et SharePoint 2013  
 SharePoint 2013 ne prend pas en charge la mise à niveau sur place. Cependant, **la mise à niveau avec liaison des bases de données est prise en charge**.  
  
 Si vous avez une installation existante de PowerPivot intégrée à SharePoint 2010, vous ne pouvez pas effectuer une mise à niveau sur place du serveur SharePoint.  Toutefois, vous pouvez effectuer les étapes suivantes dans le cadre d'une mise à niveau avec liaison des bases de données SharePoint :  
  
1.  Installez une nouvelle batterie de serveurs SharePoint Server 2013.  
  
2.  Effectuez une mise à niveau avec liaison des bases de données SharePoint, puis migrez les bases de données de contenu associées à PowerPivot vers la batterie de serveurs SharePoint 2013.  
  
3.  Installez une instance de SQL Server Analysis Services en mode SharePoint, et accordez à la batterie SharePoint et aux comptes de services des droits d'administrateur de serveur dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
4.  Installez le package d'installation PowerPivot pour SharePoint 2013 **spPowerPivot.msi** sur chaque serveur de la batterie SharePoint.  
  
5.  Dans l'Administration centrale de SharePoint 2013, configurez Excel Services de sorte à utiliser le serveur Analysis Services exécuté en mode SharePoint créé à l'étape 3.  
  
     Pour migrer les planifications d'actualisation, configurez l'application de service PowerPivot.  
  
> [!NOTE]  
>  Pour plus d'informations sur la mise à niveau avec liaison aux bases de données de PowerPivot et SharePoint, consultez les rubriques suivantes :  
  
-   [Migrer PowerPivot vers SharePoint 2013](../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)  
  
-   [Présentation de la procédure de mise à niveau vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Nettoyer les préparations avant la mise à niveau vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Mettre à niveau les bases de données de SharePoint 2010 vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
## <a name="see-also"></a>Voir aussi  
 [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Prise en charge les combinaisons de SharePoint et Reporting Services serveur et complément &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)   
 [Installer ou désinstaller le complément Services Reporting pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
