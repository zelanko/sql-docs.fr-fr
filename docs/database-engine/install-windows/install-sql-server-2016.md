---
title: "Installer SQL Server&#160;2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "AdventureWorks, exemple de base de données"
  - "installation de SQL Server, préparation à l’installation"
  - "installation [SQL Server]"
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
caps.latest.revision: 59
ms.author: "mikeray"
manager: "jhubbard"
---
# Installer SQL Server&#160;2016
  SQL Server 2016 est une application 64 bits. Voici des informations importantes sur la façon d’obtenir SQL Server et de l’installer.

## <a name="installation-details"></a>Détails de l’installation
  
*  **Options** : effectuez l’installation par le biais de l’Assistant Installation, de l’outil sysprep ou d’une invite de commandes
 
*  **Configuration requise** : avant de procéder à l’installation, prenez connaissance de la configuration requise, des vérifications de configuration du système et des considérations sur la sécurité décrites dans [Planification d’une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md) 

* **Processus** : consultez [Installation de SQL Server](../../database-engine/install-windows/installation-for-sql-server-2016.md) pour obtenir des instructions complètes sur le processus d’installation

* **Exemples de bases de données et exemples de code** : 
    * Par défaut, ils ne sont pas installés dans le cadre de l’installation de SQL Server 
    * Pour les installer avec les éditions non-Express de SQL Server, consultez le [site web CodePlex](http://go.microsoft.com/fwlink/?LinkId=87843)
    * Pour obtenir de l’aide sur les exemples de bases de données SQL Server et les exemples de code pour SQL Server Express, consultez [Databases and Samples Overview](http://go.microsoft.com/fwlink/?LinkId=110391).
    

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

L’emplacement de téléchargement pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dépend de l’édition :

- Les **éditions de SQL Server Enterprise, Standard et Express** sont concédées sous licence pour une utilisation en production. Pour les éditions Enterprise et Standard, contactez votre revendeur de logiciels pour obtenir le support d’installation. Vous trouverez des informations sur l’achat et un annuaire de partenaires de Microsoft sur le [site web d’achat de Microsoft](https://www.microsoft.com/en-us/server-cloud/products/sql-server/overview.aspx). 

- Les **éditions gratuites** sont disponibles via ces liens :

| Édition | Description
|---------|--------
|[Developer Edition](http://myprodscussu1.app.vssubscriptions.visualstudio.com/Downloads?q=SQL%20Server%20Developer) | Jeu gratuit et complet du logiciel SQL Server 2016 Enterprise Edition qui permet aux développeurs de générer, tester et démontrer des applications dans un environnement hors production. 
|[Express Edition](http://www.microsoft.com/download/details.aspx?id=52679)|  Base de données gratuite d’entrée de gamme idéale pour déployer de petites bases de données dans des environnements de production. Créez des applications de bureau et de petits serveurs pilotées par les données jusqu’à 10 Go de taille sur disque. 
| [Evaluation Edition](http://technet.microsoft.com/evalcenter/mt130694) | Jeu complet du logiciel SQL Server Enterprise Edition avec une période d’évaluation de 180 jours.
   
 
  

## <a name="how-to-install-sql-server"></a>Comment installer SQL Server
 
|Titre|Description|  
|-----------|-----------------|  
|[Installer SQL Server 2016 sur Server Core](../../database-engine/install-windows/install-sql-server-2016-on-server-core.md)|Prenez connaissance de cette rubrique pour installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur Windows Server Core.|  
|[Paramètres de l’outil d’analyse de configuration système](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)|Décrit les fonctions de l'Outil d'analyse de configuration système (SCC).|  
|[Installer SQL Server 2016 avec l’Assistant Installation &#40;programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)|Rubrique de procédure pour une installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] typique à l'aide de l'Assistant Installation.|  
|[Installer SQL Server 2016 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)|Rubrique de procédure qui fournit un exemple de syntaxe et de paramètres d'installation pour exécuter une installation sans assistance.|  
|[Installer SQL Server 2016 à l’aide d’un fichier de configuration](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)|Rubrique de procédure qui fournit un exemple de syntaxe et de paramètres d'installation pour exécuter une installation à l'aide d'un fichier de configuration.|  
|[Installer SQL Server 2016 à l’aide de SysPrep](../../database-engine/install-windows/install-sql-server-2016-using-sysprep.md)|Rubrique de procédure qui fournit un exemple de syntaxe et de paramètres d’installation pour exécuter une installation à l’aide de SysPrep.|  
|[Ajouter des fonctionnalités à une instance de SQL Server 2016 &#40;programme d’installation&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)|Rubrique de procédure pour mettre à jour les composants d'une instance existante de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|[Réparer une installation défectueuse de SQL Server 2016](../../database-engine/install-windows/repair-a-failed-sql-server-2016-installation.md)|Rubrique de procédure pour réparer une installation endommagée de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|[Renommer un ordinateur qui héberge une instance autonome de SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)|Rubrique de procédure pour mettre à jour les métadonnées système stockées dans sys.servers.|  
|[Installer des mises à jour de maintenance de SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016-servicing-updates.md)|Rubrique de procédure portant sur l’installation des mises à jour de SQL Server 2016.|  
|[Afficher et lire les fichiers journaux d’installation de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)|Rubrique de procédure pour rechercher des erreurs dans les fichiers journaux d'installation.|  
|[Valider une installation SQL Server](../../database-engine/install-windows/validate-a-sql-server-installation.md)|Vérifiez l'utilisation du rapport de découverte SQL pour vérifier la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur.|  
  
  
## <a name="how-to-install-individual-components"></a>Comment installer des composants individuels  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Installer le moteur de base de données SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)|Explique comment installer et configurer le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Installer la réplication SQL Server](../../database-engine/install-windows/install-sql-server-replication.md)|Explique comment installer et configurer la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Install Distributed Replay - Présentation](../../tools/distributed-replay/install-distributed-replay-overview.md)|Répertorie les rubriques pour installer la fonctionnalité Distributed Replay.|  
|[Installer les Outils d’administration SQL Server avec SSMS](Install%20SQL%20Server%20Management%20Tools%20\(SSMS\).md)|Décrit comment installer et configurer les outils d'administration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Installer SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)|Décrit les considérations relatives à l'installation des composants PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  

## <a name="how-to-configure-sql-server"></a>Pour configurer SQL Server  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|Cette rubrique fournit une vue d'ensemble de la configuration du pare-feu et décrit comment configurer le Pare-feu Windows.|  
|[Configurer un ordinateur multirésident pour l’accès à SQL Server](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|Cette rubrique explique comment configurer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le Pare-feu Windows avec fonctions avancées de sécurité pour fournir des connexions réseau à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un environnement multirésident.|  
|[Configurer le Pare-feu Windows pour autoriser l’accès à Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|Vous pouvez suivre les étapes fournies dans cette rubrique pour configurer les paramètres de port et de pare-feu afin d’autoriser l’accès à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint.|  
  
## <a name="related-sections"></a>Sections connexes  
[Fonctionnalités prises en charge par l’édition de SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
[Installer les fonctionnalités Business Intelligence de SQL Server 2016](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)  
  [Installation d’un cluster de basculement SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 
  
## <a name="see-also"></a>Voir aussi  

[Planification d’une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Mettre à niveau vers SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)   
 [Désinstaller SQL Server 2016](../../sql-server/install/uninstall-sql-server-2016.md)   
 [Solutions haute disponibilité &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  