---
title: Installer SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, preparing to install
- installation [SQL Server]
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7b9fb6be3970ea12ce3252e70f7773f1687dbe83
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62775352"
---
# <a name="install-sql-server-2014"></a>Installer SQL Server 2014
## <a name="download-sql-server-2014-expresshttpwwwhanselmancomblogdownloadsqlserverexpressaspx"></a>[Télécharger SQL Server 2014 Express](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  **Nous vous remercions d’avoir à [Scott Hanselman](http://www.hanselman.com/) pour la collecte de tous les liens de package de programme d’installation au même endroit !**
  
 Cette rubrique fournit une vue d'ensemble des différentes options d'installation disponibles pour installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations sur les différents [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composants qui peuvent être installés et le processus d’installation, consultez [Installation pour SQL Server 2014](installation-for-sql-server.md).  
> **Remarque :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est disponible dans les éditions 32 bits et 64 bits. Les éditions 64 bits et 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont installées via l'Assistant Installation ou à l'invite de commandes. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composants, consultez [éditions et composants de SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) et [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Par défaut, les exemples de bases de données et les exemples de code ne sont pas installés dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour installer des exemples de bases de données et de code pour les éditions non-Express de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez le [site Web CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843). Pour plus d'informations sur la prise en charge des exemples de base de données et de code [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], consultez [Vue d'ensemble des bases de données et des exemples](https://go.microsoft.com/fwlink/?LinkId=110391).  
  
 Avant d'installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], prenez connaissance des conditions requises pour l'installation, des contrôles de configuration du système et des considérations sur la sécurité. Pour en savoir plus, voir [Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md). Examinez les rubriques de la section suivante pour plus d'informations sur différents scénarios d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
  
## <a name="install-includesscurrentincludessscurrent-mdmd-components"></a>Installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] composants  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[À propos du moteur de base de données SQL Server](../sql-server-database-engine-overview.md)|Explique comment installer et configurer le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Installer la réplication SQL Server](install-sql-server-replication.md)|Explique comment installer et configurer la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Installer Distributed Replay](../../tools/distributed-replay/install-distributed-replay-overview.md)|Répertorie les rubriques pour installer la fonctionnalité Distributed Replay.|  
|[Installer les outils d’administration SQL Server](../../sql-server/install/install-sql-server-management-tools.md)|Décrit comment installer et configurer les outils d'administration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Installer SQL Server PowerShell](install-sql-server-powershell.md)|Décrit les considérations relatives à l'installation des composants PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
## <a name="how-to-install-includesscurrentincludessscurrent-mdmd"></a>Comment installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
|Titre|Description|  
|-----------|-----------------|  
|[Rubriques de procédures relatives à l’installation](../../sql-server/install/installation-how-to-topics.md)|Fournit des liens vers des rubriques de procédure pour installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à partir de l'Assistant Installation, à partir de l'invite de commandes, à l'aide des fichiers de configuration, puis à l'aide de SysPrep.|  
|[Installer SQL Server 2014 sur Server Core](install-sql-server-on-server-core.md)|Prenez connaissance de cette rubrique pour installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur Windows Server Core.|  
|[Valider une installation SQL Server](validate-a-sql-server-installation.md)|Vérifiez l'utilisation du rapport de découverte SQL pour vérifier la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur.|  
|[Paramètres de l’outil d’analyse de configuration système](check-parameters-for-the-system-configuration-checker.md)|Décrit les fonctions de l'Outil d'analyse de configuration système (SCC).|  
  
## <a name="configuration"></a>Configuration  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|Cette rubrique fournit une vue d'ensemble de la configuration du pare-feu et décrit comment configurer le Pare-feu Windows.|  
|[Configurer un ordinateur multirésident pour l’accès à SQL Server](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|Cette rubrique explique comment configurer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le Pare-feu Windows avec fonctions avancées de sécurité pour fournir des connexions réseau à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un environnement multirésident.|  
|[Configurer le Pare-feu Windows pour autoriser l’accès à Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|Vous pouvez suivre les étapes fournies dans cette rubrique pour configurer les paramètres de port et de pare-feu afin d'autoriser l'accès à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à PowerPivot pour SharePoint.|  
  
## <a name="related-sections"></a>Sections connexes  
 [Installer les fonctionnalités BI de SQL Server 2014](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 Les fonctions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui font partie de la plateforme BI de [!INCLUDE[msCoName](../../includes/msconame-md.md)] sont notamment [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)], ainsi que plusieurs applications clientes servant à créer ou utiliser des données analytiques. Cette section de la documentation de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] explique comment installer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)], et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Installation d'un cluster de basculement SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 Cette section de la documentation d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] décrit comment installer et configurer un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Planification d'une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Mise à niveau vers SQL Server 2014](upgrade-sql-server.md)   
 [Désinstaller SQL Server 2014](../../sql-server/install/uninstall-sql-server.md)   
 [Solutions haute disponibilité &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  
