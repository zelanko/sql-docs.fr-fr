---
title: Installer Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: bb7aa3e7-8807-42c8-884f-0e41d7a20837
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f0d0487ca83b3168506aec529d7cc6d24f2cea4d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213279"
---
# <a name="install-master-data-services"></a>Installer Master Data Services
  Le flux de travail suivant donne une vue d’ensemble de l’installation et de la configuration de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] L’installation est un processus en trois parties :  
  
-   [Tâches de pré-installation](#preinstall): permettent de vérifier la configuration requise avant d’installer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
-   [Opérations d'installation](#install): installez [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] à l'aide du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'une invite de commandes.  
  
-   [Tâches de post-installation](#postinstall): ouvrez le [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour terminer les opérations consécutives à l’installation. Créez et configurez la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] et les services Web, et déployez un exemple de modèle.  
  
##  <a name="preinstall"></a> Tâches de pré-installation  
  
|Action|Détails|Rubriques connexes|  
|------------|-------------|--------------------|  
|Vérifier la configuration requise pour l'installation|L'ordinateur sur lequel vous exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit avoir la configuration minimale requise pour :<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> L'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] et les services Web.<br /><br /> La base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , si vous hébergez la base de données sur le même ordinateur que l'application Web.<br /><br /> Notez que vous pouvez séparer l’ordinateur serveur web et l’ordinateur du serveur de base de données en exécutant le programme d’installation sur uniquement l’ordinateur de serveur web et en créant le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] base de données sur un ordinateur distant qui exécute une version prise en charge et l’édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)<br /><br /> [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)<br /><br /> [Web Application exigences &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md)<br /><br /> [Exigences de base de données &#40;Master Data Services&#41;](database-requirements-master-data-services.md)|  
|Configurer les rôles, les services de rôle et les fonctionnalités requis|Avant d'exécuter le programme d'installation, configurez l'ordinateur avec les rôles, les services de rôle et les fonctionnalités Windows requis.<br /><br /> Remarque : bien que vous puissiez exécuter ultérieurement cette étape dans le flux de travail, il est utile de procéder à cette configuration avant d’exécuter le programme d’installation, afin de pouvoir effectuer les tâches de configuration web immédiatement après.|[Web Application exigences &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md)|  
|Déterminer le prise en charge linguistique|Déterminez la langue que vous souhaitez installer et exécuter dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Déploiements multilingues et globaux &#40;Master Data Services&#41;](multi-lingual-and-global-deployments-master-data-services.md)|  
  
##  <a name="install"></a> Opérations d'installation  
  
|Action|Détails|Rubriques connexes|  
|------------|-------------|--------------------|  
|Exécuter le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Sur l'ordinateur qui hébergera l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] et les services Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , utilisez le programme d'installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou une invite de commandes pour installer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Lorsque vous utilisez le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] est disponible dans la page **Sélection de fonctionnalités** sous **Fonctionnalités partagées**. Lorsque vous utilisez une invite de commandes, [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] est disponible comme paramètre de fonctionnalité. Notez que le processus d'installation par ligne de commande installe [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], mais ne le configure pas. Vous devez le configurer à l'aide du Gestionnaire de configuration Master Data Services. Processus d'installation :<br /><br /> Installation des dossiers et des fichiers [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] à l'emplacement que vous spécifiez pour les fonctionnalités partagées et affectation des autorisations à ces objets.<br /><br /> Enregistrement des assemblys [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] dans le Global Assembly Cache (GAC).<br /><br /> Installe [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].|[Installer SQL Server 2014 à partir de l’Assistant Installation &#40;le programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)<br /><br /> [Dossier et autorisations de fichier &#40;Master Data Services&#41;](../folder-and-file-permissions-master-data-services.md)|  
  
##  <a name="postinstall"></a> Tâches de post-installation  
  
|Action|Détails|Rubriques connexes|  
|------------|-------------|--------------------|  
|Ouvrir [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour terminer les opérations consécutives à l'installation|Une fois l'installation terminée, ouvrez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] effectue les opérations de post-installation suivantes sur l’ordinateur local :<br /><br /> Création d’un groupe Windows, **MDS_ServiceAccounts**, pour contenir les comptes de service [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] pour les pools d’applications.<br /><br /> Sous le chemin d’installation de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , création du dossier MDSTempDir et affectation des autorisations pour **MDS_ServiceAccounts**. Ce dossier est l’endroit où les fichiers de compilation temporaires sont compilés pour l’application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .<br /><br /> Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] fichier Web.config, configure le `tempDirectory` attribut de la  **\<compilation >** élément avec le chemin d’accès au dossier MDSTempDir.<br /><br /> <br /><br /> Si vous générez un script du processus d'installation, vous pouvez ouvrir [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour enregistrer le composant logiciel enfichable [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], mais vous devez effectuer manuellement les autres étapes pour terminer la configuration. [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] fournit un processus de configuration piloté par l'Assistant. Il n'existe aucun processus de ligne de commande pour configurer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].|[Dossier et autorisations de fichier &#40;Master Data Services&#41;](../folder-and-file-permissions-master-data-services.md)<br /><br /> [Référence de Configuration de Web &#40;Master Data Services&#41;](../web-configuration-reference-master-data-services.md)|  
|Créer une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|Utilisez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour créer une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] pour vos données de référence.|[Créer une base de données Master Data Services](create-a-master-data-services-database.md)|  
|Créer une application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]|Utilisez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour créer et configurer une application Web qui hébergera [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|[Créer une application web Master Data Manager &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)|  
|Associer une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] à une application Web|Utilisez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour associer votre application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] à votre base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Associer une base de données Master Data Services et une application Web](associate-a-master-data-services-database-and-web-application.md)|  
|Configurer la sécurité renforcée d'Internet Explorer|Lorsque vous installez [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] sur un ordinateur Windows Server 2008 ou Windows Server 2008 R2, vous devrez peut-être configurer la sécurité d’amélioré Internet Explorer pour autoriser le script pour le [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] site de l’application. Sinon, la navigation sur le site de l'application [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] sur le serveur échoue.|[Internet Explorer : configuration de sécurité renforcée](http://go.microsoft.com/fwlink/p/?LinkId=223869)|  
|Installer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|Les utilisateurs qui travaillent avec des données de référence peuvent installer [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)].|[http://go.microsoft.com/fwlink/?LinkId=219530](http://go.microsoft.com/fwlink/?LinkId=219530)|  
|Activer l'intégration de Data Quality Services (DQS)|Pour les utilisateurs du [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], activez l’intégration avec la fonction DQS, qui permet de faire correspondre des données similaires.|[Activer l’intégration de Data Quality Services avec Master Data Services](enable-data-quality-services-integration-with-master-data-services.md)|  
|Déployer un exemple de modèle|Les packages d'exemples de modèles sont installés avec Master Data Services et peuvent être déployés à l'aide de l'outil MDSModelDeploy.|[Déploiement des exemples MDS dans SQL Server](http://go.microsoft.com/fwlink/?LinkId=251486&clcid=0x409)|  
  
 Si vous rencontrez des problèmes pendant la procédure d'installation ou la configuration initiale, consultez [Résolution des problèmes d'installation et de configuration](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-installation-and-configuration-issues-master-data-services.aspx) sur TechNet Wiki.  
  
 Si vous n'avez plus besoin de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] sur un ordinateur, vous pouvez désinstaller [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et déterminer s'il faut supprimer les éléments qui ne sont pas supprimés par le processus de désinstallation. Pour plus d’informations, consultez [Désinstaller et supprimer Master Data Services](../../sql-server/install/uninstall-and-remove-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)  
  
  
