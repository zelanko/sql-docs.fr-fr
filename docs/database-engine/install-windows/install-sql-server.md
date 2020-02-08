---
title: Guide d’installation de SQL Server
ms.description: 'An index of content that helps you install SQL Server and associated components through various options such as the installation wizard, command prompt, or sysprep. '
ms.custom: ''
ms.date: 11/14/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- AdventureWorks sample database
- installing SQL Server, preparing to install
- installation [SQL Server]
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 30155a37f57391edeee916cd2b6629d63a1dcaaa
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "75688242"
---
# <a name="sql-server-installation-guide"></a>Guide d’installation de SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article offre un index de contenu permettant de trouver des conseils pour l’installation de SQL Server sur Windows.

Pour d’autres scénarios de déploiement, consultez :

- [Linux](../../linux/sql-server-linux-setup.md)
- [Conteneurs Docker](../../linux/sql-server-linux-configure-docker.md)
- [Kubernetes - Clusters Big Data](../../big-data-cluster/deploy-get-started.md)

À partir de [!INCLUDE[sssql15](../../includes/sssql15-md.md)], [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] est disponible uniquement en tant qu’application 64 bits. Voici des informations importantes sur la façon d’obtenir SQL Server et de l’installer.

## <a name="getting-started"></a>Prise en main
  
* **Éditions et fonctionnalités** : passez en revue les fonctionnalités prises en charge par les différentes éditions et versions de SQL Server pour déterminer celles qui correspondent le mieux à vos besoins métier. 
    - [[!INCLUDE[ss2019](../../includes/sssqlv15-md.md)]](~/sql-server/editions-and-components-of-sql-server-version-15.md).  
    - [[!INCLUDE[ss2017](../../includes/sssqlv14-md.md)]](~/sql-server/editions-and-components-of-sql-server-2017.md).  
    - [[!INCLUDE[ss2016](../../includes/sssql15-md.md)]](~/sql-server/editions-and-components-of-sql-server-2016.md).  
    - [[!INCLUDE[ss2014](../../includes/sssql14-md.md)]](https://technet.microsoft.com/library/cc645993(v=sql.120).aspx)

*  **Exigences** : prenez connaissance des conditions requises pour l’installation, des contrôles de configuration du système et des considérations sur la sécurité pour [planifier une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md). 
  
* **Exemples de bases de données et exemples de code**: 
    * Ils ne sont pas installés dans le cadre de l’installation de SQL Server par défaut, mais sont disponibles. 
    * Pour les installer avec les éditions non-Express de SQL Server, consultez l’article sur l’[emplacement des exemples](../../samples/sql-samples-where-are.md)
    

## <a name="installation-media"></a>Support d’installation

L’emplacement de téléchargement pour [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] dépend de l’édition :

* Les **éditions de SQL Server Entreprise, Standard et Express** sont concédées sous licence pour une utilisation en production. Pour les éditions Enterprise et Standard, contactez votre revendeur de logiciels pour obtenir le support d’installation. Vous trouverez des informations sur l’achat et un annuaire de partenaires de Microsoft sur la [page Microsoft dédiée aux licences](https://www.microsoft.com/licensing/product-licensing/sql-server).
* [Version gratuite - dernière version](https://www.microsoft.com/sql-server/sql-server-downloads)
* [Version gratuite - autres versions](https://www.microsoft.com/evalcenter/evaluate-sql-server)


Les liens suivants vous permettront de trouver d’autres composants SQL Server : 

* [Ensemble des mises à jour cumulatives](https://sqlserverbuilds.blogspot.com/)
* [SQL Server Reporting Services](https://www.microsoft.com/download/details.aspx?id=100122). 
* [SQL Server Management Studio](https://aka.ms/ssmsfullsetup)
* [Azure Data Studio](https://go.microsoft.com/fwlink/?linkid=2109256)


## <a name="sql-server-installation"></a>Installation de SQL Server
 
|Article|Description|  
|-----------|-----------------|  
|[Assistant Installation](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)|Installation de SQL Server à l’aide de l’interface graphique utilisateur de l’Assistant Installation lancée à partir du fichier d’installation setup.exe. |  
|[Invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)|Exemple de syntaxe et de paramètres d’installation pour l’exécution d’une installation de SQL Server à partir de l’invite de commandes. | 
|[Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md)|Installation de [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] sur Windows Server Core.|  
|[Paramètres de l’outil d’analyse de configuration système](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)|Décrit les fonctions de l'Outil d'analyse de configuration système (SCC).|   
|[Fichier de configuration](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)|Exemple de syntaxe et de paramètres d’installation pour exécuter une installation à l’aide d’un fichier de configuration.|  
|[SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md)|Exemple de syntaxe et de paramètres d’installation pour exécuter une installation à l’aide de SysPrep.|
|[Ajouter des fonctionnalités à une instance](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)|Mise à jour des composants d’une instance existante de [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Installation d'un cluster de basculement SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)| Installation d’une instance de cluster de basculement SQL Server.  | 
|[Réparer une installation défectueuse de [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)|Réparation d’une installation endommagée de [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Renommer un ordinateur avec SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)|Mise à jour des métadonnées système stockées dans sys.servers après avoir renommé le nom d’hôte d’un ordinateur qui héberge une instance autonome de SQL Server. |  
|[Installer les mises à jour de maintenance de [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/install-sql-server-servicing-updates.md)|Installation des mises à jour pour [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Fichiers journaux d’installation](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)| Visualisation des erreurs dans les fichiers journaux d’installation de SQL Server. |  
|[Valider une installation](../../database-engine/install-windows/validate-a-sql-server-installation.md)|Vérifiez l'utilisation du rapport de découverte SQL pour vérifier la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur.|  
  
  
## <a name="individual-component-installation"></a>Installation individuelle des composants 
  
|Article|Description|  
|-----------|-----------------|  
|[Moteur de base de données SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)|Installation et configuration de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Réplication SQL Server](../../database-engine/install-windows/install-sql-server-replication.md)|Installation et configuration de la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Distributed Replay](../../tools/distributed-replay/install-distributed-replay-overview.md)|Liste des articles portant sur l’installation de la fonctionnalité Distributed Replay.|  
|[Outils d’administration SQL Server avec SSMS](https://msdn.microsoft.com/library/af68d59a-a04d-4f23-9967-ad4ee2e63381)|Installation et configuration des outils d’administration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)|Considérations relatives à l’installation des composants PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  

## <a name="sql-server-configuration"></a>Configuration de SQL Server 
  
|Article|Description|  
|-----------|-----------------|  
|[Configurer le Pare-feu Windows (SQL Server)](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|Vue d’ensemble de la configuration du pare-feu et de la façon de configurer le Pare-feu Windows pour autoriser l’accès à SQL Server.|  
|[Configurer le Pare-feu Windows (SSAS)](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|Configuration des paramètres de port et de pare-feu pour autoriser l’accès à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint.|  
|[Configurer un ordinateur multirésident](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|Configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et du Pare-feu Windows avec des fonctions avancées de sécurité pour fournir des connexions réseau à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un environnement multirésident.|  

 
## <a name="see-also"></a>Voir aussi  

[Mettre à niveau [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/upgrade-sql-server.md)   
[Désinstaller [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../sql-server/install/uninstall-sql-server.md)   
[Installer SQL Server Reporting Services (SSRS)](../../reporting-services/install-windows/install-reporting-services.md)
[Installer SQL Server Analysis Services (SSAS)](/analysis-services/instances/install-windows/install-analysis-services)
[Installer les fonctionnalités Business Intelligence de [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../sql-server/install/install-sql-server-business-intelligence-features.md)   
[Solutions haute disponibilité &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
