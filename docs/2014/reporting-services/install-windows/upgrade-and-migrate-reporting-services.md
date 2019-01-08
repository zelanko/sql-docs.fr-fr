---
title: Mettre à niveau et migrer Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSRS, upgrading
- Reporting Services, upgrades
- SQL Server Reporting Services, upgrading
- upgrading Reporting Services
ms.assetid: 851a19a8-07ab-4d42-992f-1986c4c8df55
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 28f25620cede6c626280a8a095c66457344679d2
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53363011"
---
# <a name="upgrade-and-migrate-reporting-services"></a>Upgrade and Migrate Reporting Services
  Cette rubrique est une vue d’ensemble des options de mise à niveau et migration pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Il existe deux approches générales liées à la mise à niveau d'un déploiement de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
-   **Mise à niveau :** vous mettez à niveau les composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur les serveurs et instances où ils sont installés. C’est ce que l’on appelle communément une mise à niveau « sur place ». La mise à niveau sur place n'est pas prise en charge d'un mode de serveur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à un autre. Par exemple, vous ne pouvez pas mettre à niveau un serveur de rapports en mode natif vers un serveur de rapports en mode SharePoint. vous pouvez migrer vos éléments de rapport d'un mode à l'autre. Pour plus d’informations, consultez la section « Native pour la Migration de SharePoint » plus loin dans ce document et de la rubrique connexe [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
-   **Migrer**: vous installez et configurez un nouvel environnement SharePoint, copiez vos éléments de rapport et ressources dans le nouvel environnement et configurez le nouvel environnement de façon à utiliser le contenu existant. une forme de migration de niveau inférieur consiste à copier les bases de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , les fichiers de configuration, et si vous utilisez le mode SharePoint, les bases de données de contenu SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint|  
  
##  <a name="bkmk_top"></a> Dans cette rubrique :  
  
-   [Problèmes connus de mise à niveau et meilleures pratiques](#bkmk_known_issues)  
  
-   [Installations côte à côte](#bkmk_side_by_side)  
  
-   [Mise à niveau sur place](#bkmk_inplace_upgrade)  
  
-   [Liste de vérification de pré-mise à niveau](#bkmk_upgrade_checklist)  
  
-   [Mise à niveau en Mode natif et les scénarios de Migration](#bkmk_native_scenarios)  
  
-   [Mettre à niveau un déploiement évolutif de Reporting Services en Mode natif](#bkmk_native_scaleout)  
  
-   [Mise à niveau du Mode SharePoint et les scénarios de Migration](#bkmk_sharePoint_scenarios)  
  
-   [Considérations relatives à une Migration](#bkmk_migration_considerations)  
  
-   [Ressources supplémentaires](#bkmk_additional_resources)  
  
##  <a name="bkmk_known_issues"></a> Problèmes connus de mise à niveau et meilleures pratiques  
 Pour obtenir la liste des éditions et versions prises en charge que vous pouvez mettre à niveau, consultez [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
> [!TIP]
>  Pour obtenir les dernières informations concernant les problèmes avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consultez les ressources suivantes :  
> 
>  -   [Notes de mise à jour de SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
> -   [Conseils, astuces et dépannage pour SQL Server 2014 Reporting Services](https://go.microsoft.com/fwlink/?LinkID=391254).  
> -   Utilisez le Conseiller de mise à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [problèmes de mise à niveau des Services Reporting &#40;Upgrade Advisor&#41; ](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md) et [Comment : Installer le Conseiller de mise à niveau](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md).  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
##  <a name="bkmk_side_by_side"></a> Installations côte à côte  
 Le mode natif [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] peut être installé côte à côte avec un déploiement en mode natif [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
 Il n'existe aucune prise en charge des déploiements côte à côte du mode SharePoint [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] et des versions antérieures des composants du mode SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
##  <a name="bkmk_inplace_upgrade"></a> Mise à niveau sur place  
 La mise à niveau est effectuée par le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être utilisé pour mettre à niveau tout ou partie des composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , y compris [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Le programme d'installation détecte les instances existantes et vous invite à procéder à la mise à niveau. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] L'installation fournit des options de mise à niveau que vous pouvez spécifier comme argument de ligne de commande ou dans l'Assistant Installation.  
  
 Lorsque vous exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sélectionnez l'option de mise à niveau de l'une des versions suivantes ou installez une nouvelle instance de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] qui s'exécute côte à côte avec les installations existantes :  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
 Pour plus d'informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez les documents suivants :  
  
||  
|-|  
|[Mise à niveau vers SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)|  
|[Mise à niveau vers SQL Server 2014 à l’aide de l’Assistant Installation &#40;le programme d’installation&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)|  
|[Installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)|  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
##  <a name="bkmk_upgrade_checklist"></a> Liste de contrôle préalable à la mise à niveau  
 Avant d'effectuer la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consultez les rubriques suivantes :  
  
-   Passez en revue la configuration requise afin de déterminer si votre matériel et vos logiciels peuvent prendre en charge [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]. Pour plus d'informations, consultez [Hardware and Software Requirements for Installing SQL Server 2014](../../../2014/sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Utilisez l'outil d'analyse de configuration système (SCC, System Configuration Checker) pour analyser le serveur de rapports afin d'y déceler d'éventuels défauts pouvant empêcher une installation réussie de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d'informations, consultez [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md).  
  
-   Prenez connaissance des meilleures pratiques recommandées et de l'aide pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d'informations, consultez [Security Considerations for a SQL Server Installation](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
-   Exécutez le Conseiller de mise à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le serveur de rapports afin de déterminer les problèmes éventuels susceptibles d'empêcher la mise à niveau. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
-   Sauvegardez votre clé symétrique. Pour plus d’informations, consultez [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
-   Sauvegardez les fichiers de configuration et bases de données du serveur de rapports. Pour plus d'informations, consultez [Backup and Restore Operations for Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md).  
  
-   Sauvegardez toutes les personnalisations effectuées dans les répertoires virtuels [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans IIS.  
  
-   Supprimez les certificats SSL non valides.  Cela inclut les certificats expirés et que vous ne projetez pas de mettre à jour avant la mise à niveau de Reporting Services.  Certificats non valides provoqueront l’échec mise à niveau et un message d’erreur semblable au suivant sera écrit dans le fichier journal Reporting Services : **Microsoft.ReportingServices.WmiProvider.WMIProviderException : Un certificat Secure Sockets Layer (SSL) n’est pas configuré sur le site Web.** .  
  
 Avant de mettre à niveau un environnement de production, veillez à toujours exécuter une mise à niveau de test dans un environnement de préproduction qui a la même configuration que votre environnement de production.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
## <a name="overview-of-migration-scenarios"></a>Présentation des scénarios de migration  
 Si vous effectuez une mise à niveau à partir d'une version prise en charge de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous exécutez généralement l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour mettre à niveau les fichiers programme du serveur de rapports, la base de données et toutes les données d'application.  
  
 Toutefois, la **migration** manuelle d'une installation du serveur de rapports est requise si vous rencontrez l'une des conditions suivantes :  
  
-   Le Conseiller de mise à niveau a détecté un ou plusieurs bloqueurs de mise à niveau. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
-   Vous souhaitez modifier le type de serveur de rapports utilisé dans votre déploiement. Par exemple, vous ne pouvez pas mettre à niveau ou convertir un serveur de rapports en mode natif vers le mode SharePoint. Pour plus d’informations, consultez [Migration du mode natif au mode SharePoint &#40;SSRS&#41;](../../reporting-services/install-windows/native-to-sharepoint-migration-ssrs.md).  
  
-   Vous souhaitez réduire la durée pendant laquelle le serveur de rapports est mis hors connexion lors du processus de mise à niveau. Votre installation actuelle reste en ligne pendant que vous copiez des données de contenu vers une nouvelle instance du serveur de rapports et testez l'installation sans modifier l'état de votre installation existante du serveur de rapports.  
  
-   Vous souhaitez migrer un déploiement SharePoint 2010 de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vers SharePoint 2013. SharePoint 2013 ne prend pas en charge la mise à niveau sur place à partir de SharePoint 2010. Pour plus d’informations, consultez [Migrer une installation Reporting Services &#40;mode SharePoint&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md).  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
##  <a name="bkmk_native_scenarios"></a> Scénarios de mise à niveau et de migration en mode natif  
 **Mise à niveau :** la mise à niveau sur place pour le mode natif est identique pour chacune des versions prises en charge répertoriées plus haut dans cette rubrique. Exécutez l'Assistant Installation de SQL Server ou une installation à partir de la ligne de commande. L'installation suivante dans la base de données du serveur de rapports effectuera automatiquement la mise à niveau vers le nouveau schéma de base de données du serveur de rapports. Pour plus d'informations, consultez la section [In-place upgrade](#bkmk_inplace_upgrade) de cette rubrique.  
  
 Le processus de mise à niveau commence lorsque vous sélectionnez une instance de serveur de rapports existante à mettre à niveau.  
  
1.  Si la base de données de serveur de rapports se trouve sur un ordinateur distant et que vous n'avez pas l'autorisation de mettre à jour cette base de données, le programme d'installation vous invite à fournir les informations d'identification pour mettre à jour la base de données de serveur de rapports distante. Soyez sûr de fournir les informations d'identification qui ont `sysadmin` ou les autorisations de mise à jour de la base de données.  
  
2.  L'installation vérifie les conditions ou paramètres qui empêchent la mise à niveau et lit les paramètres de configuration. Les exemples incluent les extensions personnalisées déployées sur le serveur de rapports. Si la mise à niveau est bloquée, vous devez modifier votre installation afin qu'elle ne le soit plus, ou migrer vers une nouvelle instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Pour plus d'informations, consultez la documentation relative au Conseiller de mise à niveau.  
  
3.  Si la mise à niveau peut se poursuivre, le programme d'installation vous invite à la continuer.  
  
4.  Le programme d'installation crée de nouveaux dossiers pour les fichiers programme de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Les dossiers de programme pour un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation incluent MSRS12.\< *nom de l’instance*>.  
  
5.  L'installation ajoute les fichiers programme du serveur de rapports [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , les outils de configuration et les utilitaires de ligne de commande qui font partie des fonctionnalités du serveur de rapports.  
  
    1.  Les fichiers programme de la version antérieure sont supprimés.  
  
    2.  Les outils de configuration et utilitaires du serveur de rapports mis à niveau vers la nouvelle version incluent l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif, les utilitaires en ligne de commande, tels que RS.exe et le Générateur de rapports.  
  
    3.  Les autres outils clients, tels que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et la documentation en ligne, ne sont pas mis à niveau. Pour obtenir des nouvelles versions des outils, vous pouvez les ajouter lorsque vous exécutez le programme d'installation. Les versions antérieures coexistent avec les versions de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Si vous avez installé les exemples, la version antérieure demeure. L'installation ne prend pas en charge la mise à niveau pour les exemples SQL Server.  
  
    4.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] est disponible en téléchargement séparé. Pour plus d'informations, consultez [Microsoft SQL Server 2014 Data Tools - Business Intelligence pour Microsoft Visual Studio 2012](https://go.microsoft.com/fwlink/?LinkID=325512).  
  
6.  Le programme d'installation réutilise l'entrée de service du gestionnaire de services de contrôle pour le service Report Server de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Cette entrée de service inclut le compte de service Windows Report Server.  
  
7.  L'installation réserve les nouvelles URL en fonction des paramètres de répertoire virtuel existants dans IIS. Comme le programme d'installation ne supprime pas toujours les répertoires virtuels dans IIS, veillez à les supprimer manuellement après la mise à niveau.  
  
8.  L'installation met à niveau les bases de données du serveur de rapports vers le nouveau schéma et modifie le `RSExecRole` en ajoutant les autorisations du propriétaire de la base de données au rôle. Cette étape intervient seulement lorsque vous effectuez une mise à niveau à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] avant le SP1.  
  
9. L'installation fusionne les paramètres dans les fichiers de configuration. En utilisant comme base les fichiers de configuration de l'installation actuelle, les nouvelles entrées sont ajoutées. Les entrées obsolètes ne sont pas supprimées, mais ne seront plus lues après la mise à niveau par le serveur de rapports. La mise à niveau ne supprime pas les anciens fichiers journaux, le fichier RSWebApplication.config obsolète ou les paramètres de répertoire virtuel dans IIS. La mise à niveau ne supprime pas le Concepteur de rapports de SQL Server 2005, Management Studio ou autres outils clients. Si vous n'en avez plus besoin, veillez à supprimer ces fichiers et outils après la mise à niveau.  
  
 **Migration :** la migration d'une version précédente d'une installation en mode natif vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est identique à celle de toutes les versions prises en charge répertoriées plus haut dans cette rubrique. Pour plus d’informations, consultez [Migrer une installation Reporting Services &#40;mode natif&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
##  <a name="bkmk_native_scaleout"></a> Mettre à niveau un déploiement par montée en puissance parallèle en mode natif Reporting Services  
 Voici un récapitulatif de la procédure de mise à niveau d’un déploiement en mode natif [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui fait l’objet d’un scale-out sur plusieurs serveurs de rapports. Ce processus implique des temps morts du déploiement de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
1.  Sauvegardez les bases de données et les clés de chiffrement du serveur de rapports. Pour plus d’informations, consultez [Opérations de sauvegarde et de restauration pour Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md) et [Ajouter et supprimer des clés de chiffrement pour un déploiement évolutif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md).  
  
2.  Utilisez le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour supprimer tous les serveurs de rapports du déploiement avec montée en puissance parallèle. Pour plus d’informations, consultez [Configurer un déploiement par montée en puissance parallèle de serveurs de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
3.  Mettez à niveau un des serveurs de rapports vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
4.  Utilisez le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour rajouter les serveurs de rapports au déploiement avec montée en puissance parallèle. Pour plus d’informations, consultez [Configurer un déploiement par montée en puissance parallèle de serveurs de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
     Pour chaque serveur, répétez les étapes de mise à niveau et montée en puissance parallèle.  
  
##  <a name="bkmk_sharePoint_scenarios"></a> Scénarios de mise à niveau et de migration en mode SharePoint  
 Les sections suivantes décrivent les problèmes et les étapes de base nécessaires pour mettre à niveau ou migrer des versions spécifiques du mode SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vers le mode SharePoint [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Il existe deux composants d'installation pour mettre à niveau un déploiement en mode SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
    > [!TIP]  
    >  Utilisez l'applet de commande SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] `Get-SPRSServiceApplicationServers` pour déterminer quels serveurs de la batterie de serveurs SharePoint exécutent le Service partagé SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et, par conséquent, doivent être mis à niveau.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Complément pour les produits SharePoint. Pour plus d’informations, consultez [installer ou désinstaller le logiciel complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 Pour plus d’informations sur la migration d’une installation en mode SharePoint, consultez [Migrer une installation Reporting Services &#40;mode SharePoint&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md).  
  
> [!IMPORTANT]  
>  Certains des scénarios suivants requièrent l'arrêt de l'environnement SharePoint en raison des différentes technologies devant être mises à niveau. Si votre situation ne permet pas de temps d'arrêt, vous devez effectuer une migration complète au lieu d'une mise à niveau sur place.  
  
### <a name="includesssql11includessssql11-mdmd-to-includesssql14includessssql14-mdmd"></a>[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 **Environnement de départ :** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)], SharePoint 2010.  
  
 **Environnement final :** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SharePoint 2010 ou SharePoint 2013.  
  
-   **SharePoint 2010 :** La mise à niveau sur place de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est prise en charge, mais le scénario de mise à niveau ne nécessite pas de temps mort de l'environnement SharePoint.  
  
     Si vous souhaitez également que l'environnement de fin exécute SharePoint 2013, vous devez effectuer une mise à niveau avec attachement des bases de données de SharePoint 2010 vers SharePoint 2013.  
  
-   **SharePoint 2013 :** SharePoint 2013 ne prend pas en charge la mise à niveau sur place à partir de SharePoint 2010. Cependant, la procédure de **mise à niveau avec liaison des bases de données est prise en charge**  . Le comportement est différent de la mise à niveau vers SharePoint 2010, dans laquelle un client avait le choix entre les deux méthodes de mise à niveau de base : la mise à niveau sur place et la mise à niveau avec liaison des bases de données.  
  
     Si vous avez une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] intégrée à SharePoint 2010, vous ne pouvez pas effectuer une mise à niveau sur place du serveur SharePoint. Toutefois, vous pouvez migrer les bases de données de contenu et les bases de données d'application de service de la batterie de serveurs SharePoint 2010 vers une batterie de serveurs SharePoint 2013.  
  
### <a name="includesskilimanjaroincludessskilimanjaro-mdmd-to-includesssql14includessssql14-mdmd"></a>[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 **Environnement de départ :** SQL Server 2008 R2, SharePoint 2010.  
  
 **Environnement final :** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SharePoint 2010.  
  
-   La mise à niveau sur place est prise en charge et votre environnement SharePoint ne subit aucun arrêt.  
  
-   Installez la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint sur chaque serveur Web frontal dans la batterie de serveurs. Vous pouvez installer le complément à l'aide de l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou en le téléchargeant.  
  
-   Exécutez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation pour mettre à niveau le mode SharePoint pour chaque serveur de rapports. L’Assistant d’installation de SQL Server installera le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service et créer une nouvelle application de Service.  
  
     Si vous souhaitez également que l'environnement de fin exécute SharePoint 2013, vous devez effectuer une mise à niveau avec attachement des bases de données de SharePoint 2010 vers SharePoint 2013.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
### <a name="includesskatmaiincludessskatmai-mdmd-sp2-to-includesssql14includessssql14-mdmd"></a>[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2 vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 **Environnement de départ :** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2, SharePoint 2007.  
  
 **Environnement final :** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SharePoint 2010.  
  
-   Ce scénario de mise à niveau sur place nécessite l'arrêt de l'environnement SharePoint car les technologies SharePoint et SQL Server doivent être mises à niveau toutes les deux. Vous pouvez envisager d'effectuer une migration complète plutôt qu'une mise à niveau sur place.  
  
-   Effectuez tout d'abord une mise à niveau de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] vers le Service Pack 2 (SP2), si cela n'a pas déjà été effectué.  
  
-   Effectuez la mise à niveau de SharePoint vers la version 2010. Lorsque vous exécutez le programme d'installation préalable de SharePoint 2010, il met à niveau le complément Reporting Services pour les produits SharePoint 2010.  
  
-   Installez la version de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint sur tous les serveurs Web frontaux SharePoint. Le programme d'installation préalable de SharePoint a installé la version SQL Server 2008 R2 du complément, mais vous avez besoin de la version de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour utiliser un serveur de rapports de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
-   > [!WARNING]  
    >  Après la mise à niveau de SharePoint, votre environnement Reporting Services ne sera opérationnel qu'une fois SQL Server mis à niveau.  
  
-   Mettre à niveau [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Lorsque vous exécutez l'Assistant Installation de SQL Server, une boîte de dialogue concernant l'«**Authentification de mode SharePoint SQL Server Reporting Services**» s'affiche Le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé et les informations d'identification de la page d'authentification sont utilisées pour créer un nouveau pool d'applications SharePoint.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
### <a name="sql-server-2005-sp2-to-includesssql14includessssql14-mdmd"></a>SQL Server 2005 SP2 vers[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 **Environnement de départ :** SQL Server 2005 SP2, SharePoint 2007.  
  
 **Environnement final :** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SharePoint 2010.  
  
-   Ce scénario de mise à niveau sur place nécessite l'arrêt de l'environnement SharePoint car les technologies SharePoint et SQL Server doivent être mises à niveau toutes les deux. Vous pouvez envisager d'effectuer une migration complète plutôt qu'une mise à niveau sur place.  
  
-   Effectuez tout d'abord une mise à niveau de SQL Server 2005 vers le Service Pack 2 (SP2), si cela n'a pas déjà été effectué.  
  
-   Effectuez la mise à niveau de SharePoint vers SharePoint 2010. Lorsque vous exécutez le programme d'installation préalable de SharePoint 2010, il met à niveau le complément Reporting Services pour les produits SharePoint 2010.  
  
-   > [!WARNING]  
    >  Après la mise à niveau de SharePoint, votre environnement Reporting Services ne sera opérationnel qu'une fois SQL Server mis à niveau.  
  
-   Installez la version de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint sur tous les serveurs Web frontaux SharePoint. Le programme d'installation préalable de SharePoint a installé la version SQL Server 2008 R2 du complément, mais vous avez besoin de la version de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour utiliser un serveur de rapports de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
-   Mettre à niveau [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Lorsque vous exécutez l'Assistant Installation de SQL Server, une boîte de dialogue concernant l'« Authentification de mode SharePoint SQL Server Reporting Services » s'affiche Le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé et les informations d'identification de la page d'authentification sont utilisées pour créer un nouveau pool d'applications SharePoint.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
##  <a name="bkmk_migration_considerations"></a> Considérations relatives à une migration  
 Lorsque vous déplacez des données d'application, tenez compte des problèmes et restrictions suivants :  
  
-   La protection de la clé de chiffrement inclut un hachage qui incorpore l'identité de l'ordinateur.  
  
-   Les noms de bases de données du serveur de rapports sont fixes et ne peuvent pas être renommés sur le nouvel ordinateur.  
  
### <a name="encryption-key-considerations"></a>Considérations sur la clé de chiffrement  
 Effectuez toujours une sauvegarde des clés de chiffrement avant de déplacer une base de données du serveur de rapports vers un nouvel ordinateur.  
  
 Le déplacement d'une installation du serveur de rapports vers un autre ordinateur invalidera le hachage qui protège les clés de chiffrement utilisées pour aider à sécuriser des données sensibles stockées dans la base de données du serveur de rapports. Chaque instance du serveur de rapports qui utilise la base de données a sa copie de la clé de chiffrement, laquelle est chiffrée avec l'identité du compte de service telle qu'elle est définie sur l'ordinateur actuel. Si vous changez d'ordinateurs, le service n'aura plus accès à sa clé, même si vous utilisez le même nom de compte sur le nouvel ordinateur.  
  
 Pour rétablir le chiffrement réversible sur le nouveau serveur de rapports, vous devez restaurer la clé que vous avez précédemment sauvegardée. L'ensemble complet de clés qui est stocké dans la base de données du serveur de rapports est composé d'une valeur de clé symétrique ainsi que des informations d'identité de service utilisées pour restreindre l'accès à la clé afin qu'elle puisse être utilisée uniquement par l'instance du serveur de rapports qui l'a stockée. Pendant la restauration de la clé, le serveur de rapports remplace les copies existantes de la clé par les nouvelles versions. La nouvelle version inclut les valeurs d'identité du service et de l'ordinateur, telles que définies sur l'ordinateur actuel. Pour plus d’informations, consultez les rubriques suivantes :  
  
-   Mode SharePoint : Consultez la section « Gestion des clés » de [gérer une Application de Service Reporting Services SharePoint](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)  
  
-   Mode natif : Consultez [sauvegarder et restaurer les Reporting Services clés de chiffrement](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
### <a name="fixed-database-name"></a>Nom de base de données fixe  
 Vous ne pouvez pas renommer la base de données du serveur de rapports. L'identité de la base de données est enregistrée dans des procédures stockées du serveur de rapports lors de la création de la base de données. Renommer les bases de données primaires ou temporaires du serveur de rapports provoquera des erreurs lors de l'exécution des procédures, invalidant alors votre installation du serveur de rapports.  
  
 Si le nom de la base de données de l'installation existante ne convient pas pour la nouvelle installation, vous devez envisager de créer une base de données portant le nom souhaité, puis de charger les données d'application existantes à l'aide des techniques énumérées ci-dessous :  
  
-   Écrivez un script [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] qui appelle des méthodes SOAP du service Web Report Server pour copier des données entre des bases de données. Vous pouvez utiliser l'utilitaire RS.exe pour exécuter le script. Pour plus d’informations sur cette approche, consultez [Scripts et PowerShell avec Reporting Services](../tools/scripting-and-powershell-with-reporting-services.md).  
  
-   Écrivez du code qui appelle le fournisseur WMI pour copier des données entre des bases de données. Pour plus d’informations sur cette approche, consultez [Accès au fournisseur WMI de Reporting Services](../tools/access-the-reporting-services-wmi-provider.md).  
  
-   Si vous avez seulement quelques éléments, vous pouvez publier de nouveau les rapports, les modèles de rapport et les sources de données partagées du Concepteur de rapports, du Générateur de modèles et du Générateur de rapports sur le nouveau serveur de rapports. Vous devez recréer les attributions de rôles, les abonnements, les planifications partagées, les planifications d'instantanés de rapports, les propriétés personnalisées que vous définissez sur les rapports ou d'autres éléments, la sécurité des éléments de modèle et les propriétés que vous définissez sur le serveur de rapports. L'historique de rapport et les données du journal des exécutions des rapports seront perdus.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
##  <a name="bkmk_additional_resources"></a> Ressources supplémentaires  
  
> [!NOTE]  
>  Pour plus d'informations sur la mise à niveau avec liaison des bases de données SharePoint, consultez les rubriques suivantes :  
  
-   [Vue d’ensemble de la mise à niveau vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688) (https://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Nettoyer les préparations avant une mise à niveau vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689) (https://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Mise à niveau des bases de données à partir de SharePoint 2010 vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans cette rubrique :](#bkmk_top)  
  
## <a name="see-also"></a>Voir aussi  
 [Rapports de mise à niveau](../../reporting-services/install-windows/upgrade-reports.md)   
 [Mise à niveau vers SQL Server 2014 à l’aide de l’Assistant Installation &#40;le programme d’installation&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
