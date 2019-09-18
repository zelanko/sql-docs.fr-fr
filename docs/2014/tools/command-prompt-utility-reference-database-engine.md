---
title: Informations de référence sur l’utilitaire d’invite de commandes (Moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server]
- command prompt utilities [SQL Server], about command prompt utilities
- command prompt [SQL Server]
- utilities [SQL Server], command prompt
- command prompt [SQL Server], utilities
ms.assetid: 48364bd9-6ea7-45e9-a332-acf3d81bbfae
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dfb77db3676c8df124b65199fb0b806755e550a1
ms.sourcegitcommit: b4962530f90234017073b3fdd2248936b2de4e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71077510"
---
# <a name="command-prompt-utility-reference-database-engine"></a>Référence de l'utilitaire d'invite de commandes (moteur de base de données)
  Les utilitaires d'invite de commandes vous permettent d'écrire des scripts d'opérations [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Le tableau suivant contient la liste des utilitaires d'invite de commandes fournis avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|**Utility**|**Description**|**Installé dans**|  
|-----------------|---------------------|----------------------|  
|[Utilitaire bcp](bcp-utility.md)|Utilisé pour copier des données entre une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et un fichier de données dans un format spécifié par l’utilisateur.|\<*lecteur*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Utilitaire dta](dta/dta-utility.md)|Sert à analyser une charge de travail et à recommander des structures PDS (Physical Design Structures) permettant d'optimiser les performances du serveur pour cette charge de travail.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire dtexec](../integration-services/packages/dtexec-utility.md)|Sert à configurer et à exécuter un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . La version interface utilisateur de cet utilitaire d’invite de commandes se nomme **DTExecUI**et ouvre l’utilitaire d’exécution de package.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Utilitaire dtutil](../integration-services/dtutil-utility.md)|Utilisé pour gérer les packages SSIS.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Déployer des solutions de modèle avec l'utilitaire de déploiement](https://docs.microsoft.com/analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility)|Sert à déployer les projets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans des instances d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[Utilitaire osql](osql-utility.md)|Vous permet d'entrer des instructions, des procédures système et des fichiers de script [!INCLUDE[tsql](../includes/tsql-md.md)] à l'invite de commandes.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire profiler](profiler-utility.md)|Sert à démarrer [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] à partir d'une invite de commandes.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire RS.exe &#40;SSRS&#41;](../reporting-services/tools/rs-exe-utility-ssrs.md)|Sert à exécuter des scripts conçus pour gérer des serveurs de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire rsconfig &#40;SSRS&#41;](../reporting-services/tools/rsconfig-utility-ssrs.md)|Utilisé pour configurer une connexion de serveur de rapports.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire rskeymgmt &#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Sert à gérer des clés de chiffrement sur un serveur de rapports.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Application sqlagent90](sqlagent90-application.md)|Utilisé pour démarrer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent à partir d'une invite de commandes.|\<lecteur>:\Program Files\Microsoft SQL Server\\<*instance_name*>\MSSQL\Binn|  
|[sqlcmd Utility](sqlcmd-utility.md)|Vous permet d'entrer des instructions, des procédures système et des fichiers de script [!INCLUDE[tsql](../includes/tsql-md.md)] à l'invite de commandes.|\<*lecteur*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Utilitaire SQLdiag](sqldiag-utility.md)|Sert à recueillir des informations de diagnostic pour le service de support technique [!INCLUDE[msCoName](../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Application sqllogship](sqllogship-application.md)|Permet aux applications d'effectuer des opérations de restauration, de copie et de sauvegarde et les tâches de nettoyage associées pour une configuration de l'envoi de journaux sans effectuer de travaux de restauration, de copie et de sauvegarde.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire SqlLocalDB](sqllocaldb-utility.md)|Mode d'exécution de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destiné aux développeurs de programme.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire sqlmaint](sqlmaint-utility.md)|Sert à exécuter des plans de maintenance de bases de données créés dans des versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|\<> de lecteur : \Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\Binn|  
|[Utilitaire sqlps](sqlps-utility.md)|Sert à exécuter des commandes et des scripts PowerShell. Charge et inscrit le fournisseur PowerShell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les cmdlets.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Application sqlservr](sqlservr-application.md)|Sert à démarrer et arrêter une instance de [!INCLUDE[ssDE](../includes/ssde-md.md)] à partir de l'invite de commandes pour le dépannage.|\<> de lecteur : \Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\Binn|  
|[Utilitaire Ssms](../ssms/ssms-utility.md)|Sert à démarrer [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à partir d'une invite de commandes.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[Utilitaire tablediff](tablediff-utility.md)|Sert à comparer les données de deux tables pour détecter une non-convergence, ce qui s'avère utile lors du dépannage d'une topologie de réplication.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  
  
 **Pour accéder au Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[win8](../includes/win8-md.md)]**  
  
 Étant donné que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est un composant logiciel enfichable pour le programme [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console, et non un programme autonome, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] n'apparaît pas en tant qu'application lorsque vous exécutez [!INCLUDE[win8](../includes/win8-md.md)]. Pour ouvrir le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , dans l’icône **Rechercher** , sous **Applications**, tapez **SQLServerManager12.msc** (pour [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]) ou **SQLServerManager11.msc** pour ([!INCLUDE[ssSQL11](../includes/sssql11-md.md)]) et appuyez sur **Entrée**.  
  
## <a name="command-prompt-utilities-syntax-conventions"></a>Conventions régissant la syntaxe des utilitaires de ligne de commande  
  
|**Convention**|**Utilisé pour**|  
|--------------------|------------------|  
|MAJUSCULES|Instructions et termes utilisés au niveau du système d'exploitation.|  
|`monospace`|Exemples de commandes et de code de programmation.|  
|*italique*|Paramètres fournis par l'utilisateur.|  
|**gras**|Commandes, paramètres et autres éléments de la syntaxe qui doivent être tapés exactement de la manière indiquée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Agent de distribution de réplication](../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agent de lecture du journal de réplication](../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agent de fusion de réplication](../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agent de lecture de la file d’attente de réplication](../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Agent d'instantané de réplication](../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
