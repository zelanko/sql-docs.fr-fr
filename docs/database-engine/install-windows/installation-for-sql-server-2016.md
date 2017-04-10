---
title: "Installation de SQL Server&#160;2016 | Microsoft Docs"
ms.custom: ""
ms.date: "04/13/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.portal.Installation.f1"
helpviewer_keywords: 
  - "SQL Server (installation), installation initiale"
  - "installation [SQL Server]"
  - "installation initiale [SQL Server]"
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
caps.latest.revision: 34
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 34
---
# Installation de SQL Server&#160;2016
  L'Assistant Installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit une arborescence de fonctionnalités unique pour installer tous les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   Composants de connectivité  
  
 À compter de SQL Server 2016, les outils d’administration SQL Server ne sont plus installés à partir de l’arborescence de fonctionnalités principales ; pour plus d’informations, consultez [Installer les outils d’administration SQL Server avec SSMS](Install%20SQL%20Server%20Management%20Tools%20\(SSMS\).md).  
  
 Vous pouvez installer chaque composant individuellement ou sélectionner une combinaison de composants ci-dessus. Pour choisir au mieux les éditions et les composants disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Éditions et composants de SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md) et [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
## Dans cette section  
 Que vous utilisiez l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l'invite de commandes pour installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le processus d'installation implique les étapes suivantes :  
  
 [Planification d'une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)  
 Décrit comment préparer l'ordinateur pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Configuration matérielle et logicielle requise.  
  
-   Vérifier les spécifications de l'Outil d'analyse de configuration système et les problèmes bloquants.  
  
-   Considérations sur la sécurité.  
  
 [Installer SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016.md)  
 Décrit les options d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Guide de référence de l'interface utilisateur du programme d'installation de SQL Server](../Topic/SQL%20Server%20Setup%20User%20Interface%20Reference.md)  
 Décrit les options d’installation proposées par l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Mettre à niveau vers SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
 Décrit les options pour effectuer une mise à niveau vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Désinstaller SQL Server 2016](../../sql-server/install/uninstall-sql-server-2016.md)  
 Décrit les procédures pour désinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
 [Installation d'un cluster de basculement SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 Cette section de la documentation d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] décrit comment installer et configurer un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Installer les fonctionnalités Business Intelligence de SQL Server 2016](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les fonctions qui font partie de la plateforme BI de Microsoft sont notamment [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], ainsi que plusieurs applications clientes servant à créer ou utiliser des données analytiques. Cette section de la documentation de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] explique comment installer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## Plus d’informations  
 [Installer des fonctionnalités SQL Server BI avec SharePoint &#40;PowerPivot et Reporting Services&#41;](../Topic/Install%20SQL%20Server%20BI%20Features%20with%20SharePoint%20\(Power%20Pivot%20and%20Reporting%20Services\).md)  
 Cette section explique comment installer les fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un environnement SharePoint. Elle identifie les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibles en fonction d'une version et d'une édition spécifiques de SharePoint. Elle inclut aussi des procédures d’installation de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint et Reporting Services en mode SharePoint.  
  
 ![ssrs_fyi_note](../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png) Installez la nouvelle base de données exemple, [Wide World Importers](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx). 
  
 [Exemples SQL Server et exemples de bases de données supplémentaires](http://sqlserversamples.codeplex.com/)  
 Explique comment installer et configurer les exemples et les exemples de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Consultez le [Centre de mise à jour SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) pour obtenir des liens et des informations concernant toutes les versions de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] prises en charge.  
  
## Voir aussi  
 [Nouveautés liées à l'installation de SQL Server](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)  
  
  