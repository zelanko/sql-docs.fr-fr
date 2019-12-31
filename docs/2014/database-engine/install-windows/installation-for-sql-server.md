---
title: Installation pour SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql12.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 96afef098b711c65e1bcb46d5f687c95061f2c94
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228410"
---
# <a name="installation-for-sql-server-2014"></a>Installation de SQL Server 2014
 ## <a name="download-sql-server-2014-expresshttpwwwhanselmancomblogdownloadsqlserverexpressaspx"></a>[Télécharger SQL Server Express 2014](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  **Nous vous remercions de [Scott Hanselman](http://www.hanselman.com/) pour la collecte de tous les liens du package d’installation en un seul endroit.**
  
  L'Assistant Installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit une arborescence de fonctionnalités unique pour installer tous les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   Outils de gestion  
  
-   Composants de connectivité  
  
 Vous pouvez installer chaque composant individuellement ou sélectionner une combinaison de composants ci-dessus. Pour faire le meilleur choix parmi les éditions et les composants disponibles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans, consultez [éditions et composants de SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) et [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). 
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est disponible en éditions 32 bits et 64 bits.
 
 **Lancez-vous :**  
  
-   Vous avez un compte Azure ?  Cliquez **[ici](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** pour lancer une machine virtuelle avec SQL Server 2014 Service Pack 1 (SP1) déjà installé. Pour plus d’informations sur SQL Server 2014 (SP1), consultez les [informations de version de SQL Server 2014 Service Pack 1](https://support.microsoft.com/kb/3058865).  
  
## <a name="in-this-section"></a>Dans cette section  
 Que vous utilisiez l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l'invite de commandes pour installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le processus d'installation implique les étapes suivantes :  
  
 [Planification d’une installation de SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)  
 Décrit comment préparer l'ordinateur pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Configuration matérielle et logicielle requise.  
  
-   Vérifier les spécifications de l'Outil d'analyse de configuration système et les problèmes bloquants.  
  
-   Considérations sur la sécurité.  
  
 [Installer SQL Server 2014](install-sql-server.md)  
 Décrit les options d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Mise à niveau vers SQL Server 2014](upgrade-sql-server.md)  
 Décrit les options pour effectuer une mise à niveau vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Désinstaller SQL Server 2014](../../sql-server/install/uninstall-sql-server.md)  
 Décrit les procédures pour désinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
 [SQL Server l’installation du cluster de basculement](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 Cette section de la documentation d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] décrit comment installer et configurer un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 [Installer les fonctionnalités BI de SQL Server 2014](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les fonctions qui font partie de la plateforme BI de Microsoft sont notamment [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], ainsi que plusieurs applications clientes servant à créer ou utiliser des données analytiques. Cette section de la documentation de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] explique comment installer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="related-sections"></a>Sections connexes  
 [Rubriques de procédures relatives à l’installation](../../sql-server/install/installation-how-to-topics.md)  
 Fournit des liens vers des rubriques de procédure pour installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à partir de l'Assistant Installation, à partir de l'invite de commandes, à l'aide des fichiers de configuration, puis à l'aide de SysPrep.  
  
 [Installer SQL Server fonctionnalités BI avec SharePoint &#40;PowerPivot et Reporting Services&#41;](../../sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
 Cette section explique comment installer les fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un environnement SharePoint. Elle identifie les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibles en fonction d'une version et d'une édition spécifiques de SharePoint. Elle inclut également des procédures d'installation de PowerPivot pour SharePoint et Reporting Services en mode SharePoint.  
  
 [Installation d'exemples et d'exemples de bases de données SQL Server](https://sqlserversamples.codeplex.com/)  
 Explique comment installer et configurer les exemples et les exemples de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’installation de SQL Server](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
