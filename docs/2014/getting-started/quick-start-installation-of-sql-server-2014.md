---
title: Installation de démarrage rapide de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- quick start installation [SQL Server]
- installation [SQL Server]
- installing SQL Server, quick start installations
ms.assetid: 672afac9-364d-4946-ad5d-8a2d89cf8d81
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4b9007ce0c5f0c05638f88fcb1ac27658b9f91c7
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706885"
---
# <a name="quick-start-installation-of-sql-server-2014"></a>Installation de démarrage rapide de SQL Server 2014
    
## <a name="introduction"></a>Introduction  
 L'Assistant Installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est basé sur Windows Installer. Il fournit une arborescence de fonctionnalités unique pour l'installation des composants [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] suivants :  
  
-   [!INCLUDE[ssDE](../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]  
  
-   Outils d'administration  
  
-   Composants de connectivité  
  
 Vous pouvez installer chaque composant individuellement ou sélectionner une combinaison de composants ci-dessus. Pour obtenir le meilleur choix parmi les éditions et les composants disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] , consultez [éditions et composants de SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md).  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est disponible en éditions 32 bits et 64 bits. Le programme d'installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prend en charge les options d'installation suivantes :  
  
-   **Assistant Installation**  
  
     Pour obtenir des informations procédurales sur l’installation à l’aide de l’Assistant Installation, consultez [installer SQL Server 2014 à partir de l’Assistant installation &#40;&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   **Invite de commandes**  
  
     Consultez [installer SQL Server 2014 à partir de l’invite de commandes](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) pour obtenir un exemple de syntaxe et de paramètres d’installation pour l’exécution de l’installation sans assistance.  
  
-   **Fichier de configuration**  
  
     Consultez [installer SQL Server 2014 à l’aide d’un fichier de configuration](../database-engine/install-windows/install-sql-server-using-a-configuration-file.md) pour obtenir un exemple de syntaxe et de paramètres d’installation pour exécuter le programme d’installation via un fichier de configuration.  
  
-   **SysPrep**  
  
     Pour obtenir des informations procédurales sur l’installation de à l’aide de SysPrep, consultez [installer SQL Server 2014 à l’aide de Sysprep](../database-engine/install-windows/install-sql-server-using-sysprep.md) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   **Installation Server Core**  
  
     Pour obtenir des informations procédurales sur l’installation de sur Windows Server Core, consultez [installer SQL Server 2014 sur Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]Installation des fonctionnalités  BI**  
  
     Pour plus d’informations sur l’installation des fonctionnalités qui font partie de la plateforme bi de Microsoft, consultez [installation de SQL Server fonctionnalités bi de 2014](../sql-server/install/install-sql-server-business-intelligence-features.md) , notamment [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ,, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , et plusieurs applications clientes utilisées pour créer ou utiliser des données analytiques.  
  
-   **Installation d’un cluster de basculement**  
  
     Pour [SQL Server Failover Cluster Installation](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md) obtenir des informations procédurales sur l’installation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de sur un cluster de basculement, consultez SQL Server installation d’un cluster de basculement [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Par défaut, les exemples de bases de données et les exemples de code ne sont pas installés dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour installer des exemples de bases de données et de code pour les éditions non-Express de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez le [site Web CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843). Pour plus d'informations sur la prise en charge des exemples de base de données et de code [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], consultez [Vue d'ensemble des bases de données et des exemples](https://go.microsoft.com/fwlink/?LinkId=110391).  
  
## <a name="ssnoversion-installation"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Programme  
 Que vous utilisiez l'Assistant Installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou l'invite de commandes pour installer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le processus d'installation implique une ou plusieurs des étapes suivantes :  
  
-   Prenez connaissance des conditions requises pour l'installation, des options d'installation, des contrôles de configuration du système et des considérations sur la sécurité pour une installation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  Pour en savoir plus, voir [Planning a SQL Server Installation](quick-start-installation-of-sql-server-2014.md#BKMK_BeforeYouInstall).  
  
-   Exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour mettre à niveau une version existante de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [mise à niveau vers SQL Server 2014](#BKMK_Upgrading).  
  
-   Exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour installer une nouvelle instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [installation de SQL Server 2014](#BKMK_Install).  
  
-   Une fois l'installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] terminée, l'étape principale suivante consiste à configurer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et ses composants. Configurez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l'aide des utilitaires [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [configuration de SQL Server 2014](#BKMK_Configure).  
  
 Vous pouvez rechercher des explications détaillées de ces tâches dans la section suivante.  
  
## <a name="related-tasks"></a>Tâches associées  
  
###  <a name="planning-a-ssnoversion-installation"></a><a name="BKMK_BeforeYouInstall"></a>Planification d’une [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installation  
 Avant d'installer [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], vous devez vérifier les configurations matérielle et logicielle requises, les considérations relatives au réseau et à Internet, ainsi que les considérations relatives à la sécurité pour l'installation et l'exécution de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [planification d’une installation de SQL Server](../../2014/sql-server/install/planning-a-sql-server-installation.md) et également les rubriques suivantes :  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Passez en revue les configurations matérielle et logicielle requises, la prise en charge du système d'exploitation, les considérations relatives au réseau et à Internet, et l'espace disque nécessaire.|[Configuration requise pour l'installation](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)|  
|Vérifier les remarques de sécurité à prendre en compte pour une installation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Security Considerations](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)|  
|Passez en revue les détails des fonctionnalités prises en charge par les différentes éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Fonctionnalités et éditions](features-supported-by-the-editions-of-sql-server-2014.md)|  
|Déterminez au mieux les éditions et les composants disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Éditions et composants de SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md)|  
|Examinez la configuration matérielle et apprenez à préparer l'installation de cluster de basculement [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Avant l'installation du clustering de basculement](../sql-server/failover-clusters/install/before-installing-failover-clustering.md)|  
  
###  <a name="upgrading-to-sscurrent"></a><a name="BKMK_Upgrading"></a>Mise à niveau vers[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Vous pouvez mettre à niveau les instances existantes de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], ou [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] vers [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [mettre à niveau vers SQL Server 2014](../database-engine/install-windows/upgrade-sql-server.md). Avant d'exécuter le programme d'installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour procéder à la mise à niveau vers [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], examinez les rubriques suivantes à propos de la mise à niveau :  
  
|Description|Rubrique|  
|-----------------|-----------|  
|Documente les chemins d'accès de mise à niveau vers [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] pris en charge.|[Mises à niveau prises en charge](../database-engine/install-windows/supported-version-and-edition-upgrades.md)|  
|Décrit le Conseiller de mise à niveau, outil qui analyse les instances de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] et [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] pour identifier les problèmes de mise à niveau connus.|[Utiliser le Conseiller de mise à niveau pour la préparation des mises à niveau](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)|  
|Décrit Distributed Replay Utility, un outil qui peut utiliser plusieurs ordinateurs pour relire les données de trace de plusieurs ordinateurs, en simulant mieux les charges de travail sensibles. En effectuant une nouvelle lecture sur un serveur de test avant et après une mise à niveau de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous pouvez mesurer les différences de performance et rechercher toute incompatibilité entre votre application et la mise à niveau.|[Utiliser Distributed Replay Utility pour préparer des mises à niveau](../../2014/sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)|  
|Répertorie les modifications importantes susceptibles d'affecter vos applications après votre mise à niveau vers [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Compatibilité descendante](backward-compatibility.md)|  
|Rubrique procédurale pour mettre à niveau une instance autonome de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Effectuez une mise à niveau vers SQL Server 2014 à l’aide de l’Assistant Installation &#40;le programme d’installation&#41;](../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)|  
|Rubrique procédurale pour mettre à niveau une édition de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] vers une autre édition. Pour plus d’informations sur les chemins de mise à niveau d’édition pris en charge, consultez [Mises à niveau de version et d’édition prises en charge](../database-engine/install-windows/supported-version-and-edition-upgrades.md).|[Effectuer une mise à niveau vers une autre édition de SQL Server 2014 &#40;de l’installation&#41;](../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-setup.md)|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prend en charge la mise à niveau du [!INCLUDE[ssDE](../includes/ssde-md.md)] et d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à partir des clusters de basculement [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] vers [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] séparément sur tous les nœuds de cluster de basculement. Pour plus d'informations, consultez cette rubrique.|[Mettre à niveau un cluster de basculement SQL Server](../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)|  
  
###  <a name="installing-sscurrent"></a><a name="BKMK_Install"></a>L’installation[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Consultez les rubriques suivantes pour plus d'informations sur les différents scénarios d'installation de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
|Description|Rubrique|  
|-----------------|-----------|  
|Fournit des liens vers des rubriques pour installer plusieurs composants de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et des rubriques de procédures pour installer [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Installer SQL Server 2014](../database-engine/install-windows/install-sql-server.md)|  
|Prenez connaissance de cette rubrique pour installer [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] sur Windows Server Core.|[Installer SQL Server 2014 sur Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md)|  
|Prenez connaissance de cette rubrique pour ajouter des fonctionnalités à une instance existante de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|[Ajouter des fonctionnalités à une instance de SQL Server 2014 &#40;de l’installation&#41;](../database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup.md)|  
|Consultez cette rubrique pour créer une nouvelle instance de cluster de basculement [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Créer un cluster de basculement SQL Server &#40;programme d’installation&#41;](../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)|  
|Utilisez cette rubrique pour gérer les nœuds d'une instance de cluster de basculement [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] existante.|[Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)|  
|Utilisez cette rubrique pour installer les outils clients de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un cluster de basculement.|[Installer les outils clients sur un cluster de basculement SQL Server](../sql-server/failover-clusters/install/install-client-tools-on-a-sql-server-failover-cluster.md)|  
|Vérifiez l'utilisation du rapport de découverte SQL pour vérifier la version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les fonctionnalités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installées sur l'ordinateur.|[Valider une installation de SQL Server](../database-engine/install-windows/validate-a-sql-server-installation.md)|  
|Fournit des liens vers des rubriques de procédure pour installer [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] à partir de l'Assistant Installation, à partir de l'invite de commandes, à l'aide des fichiers de configuration, puis à l'aide de SysPrep.|[Rubriques de procédures relatives à l'installation](../../2014/sql-server/install/installation-how-to-topics.md)|  
  
## <a name="related-content"></a>Contenu associé  
 Cette section fournit des informations sur la configuration et la désinstallation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
###  <a name="configuring-sscurrent"></a><a name="BKMK_Configure"></a>Configuration[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Une fois [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installé, vous pouvez optimiser la configuration de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l'aide d'utilitaires graphiques et de l'invite de commandes. Consultez les rubriques suivantes pour configurer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour la première fois :  
  
|Description|Rubrique|  
|-----------------|-----------|  
|Utilisez les informations de cette rubrique pour déterminer si vous devez débloquer des ports dans un pare-feu pour permettre l'accès à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou PowerPivot pour SharePoint. Vous pouvez suivre les étapes fournies dans cette rubrique pour configurer les paramètres des ports et du pare-feu.|[Configurer le Pare-feu Windows pour autoriser l’accès à Analysis Services](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|  
|Cette rubrique fournit une vue d'ensemble de la configuration du pare-feu et résume les informations présentant un intérêt pour un administrateur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|[Configurer le pare-feu Windows pour autoriser l’accès SQL Server](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|  
|Cette rubrique explique comment configurer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et le Pare-feu Windows avec fonctions avancées de sécurité pour fournir des connexions réseau à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans un environnement multirésident.|[Configurer un ordinateur multirésident pour l'accès à SQL Server](../../2014/sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|  
  
###  <a name="uninstalling-sscurrent"></a><a name="BKMK_Uninstalling"></a>Désinstallation[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 Les rubriques suivantes expliquent comment désinstaller manuellement une instance autonome et une instance de cluster de basculement de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :  
  
|Description|Rubrique|  
|-----------------|-----------|  
|Cet rubrique explique comment désinstaller manuellement une instance autonome de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Désinstaller SQL Server 2014](../sql-server/install/uninstall-sql-server.md)|  
|Cette rubrique explique comment désinstaller une instance de cluster de basculement de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Supprimer une instance de cluster de basculement SQL Server &#40;programme d’installation&#41;](../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)|  
|Cette rubrique fournit des informations sur la suppression manuelle des objets [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) après la désinstallation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou juste du serveur DQS.|[Supprimer les objets serveur DQS](../../2014/sql-server/install/remove-data-quality-server-objects.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications de produit pour SQL Server 2014](sql-server-2014-product-specifications.md)   
 [Prise en main de la documentation produit pour la](../2014-toc/index.yml) [compatibilité descendante](backward-compatibility.md) SQL Server  
  
  
