---
title: "Outils SQL et des utilitaires pour SQL Server, base de données SQL Azure et SQL Data Warehouse | Documents Microsoft"
ms.custom: 
ms.date: 08/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 0
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: eccbe54c561e009858f6192126abc57e3399082c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="tools-and-utilities-for-azure-sql-database-sql-server-and-sql-data-warehouse"></a>Outils et utilitaires de base de données SQL Azure, SQL Server et SQL Data Warehouse

[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]  

![](../includes/media/sql-database-tools.png)Cet article fournit une liste des outils disponibles pour l’utilisation avec SQL Server, base de données SQL Azure, entrepôt de données SQL et les applications basées sur SQL Server. 

Si vous souhaitez accéder au travail et commencer à créer des tables, les requêtes en cours d’exécution, essentiellement concevoir et gérer votre base de données, puis [ **SQL Server Management Studio (SSMS)** ](../ssms/download-sql-server-management-studio-ssms.md) est très probablement votre outil. SSMS est gratuit et s’exécute sur Windows.

Si vous exécutez Linux ou macOS, essayez [Visual Studio Code](https://code.visualstudio.com/) avec la [ **mssql pour Visual Studio Code** ](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) extension. Ces outils sont pour le développement de Microsoft SQL Server, base de données SQL Azure et SQL Data Warehouse avec un jeu complet de fonctionnalités et sont également disponibles. Consultez [utiliser le Code de Visual Studio pour créer et exécuter des scripts Transact-SQL pour SQL Server](../linux/sql-server-linux-develop-use-vscode.md).


## <a name="sql-tools"></a>Outils SQL 
 
| Outil |  Description |
|:--|:--|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Utilisez SQL Server Management Studio (SSMS) pour les requêtes, concevoir et gérer votre SQL Server, base de données SQL Azure et Azure SQL Data Warehouse. |
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Activez Visual Studio dans un environnement de développement puissant pour SQL Server, base de données SQL Azure et Azure SQL Data Warehouse. |
| [Code Visual Studio](https://code.visualstudio.com/)| Code Visual Studio fonctionne sur Windows, Linux et macOS. Après avoir installé Visual Studio Code, vous devez installer le [mssql extension](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) pour le développement de Microsoft SQL Server, base de données SQL Azure et SQL Data Warehouse. |
| [Gestionnaire de configuration](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Utilisez le Gestionnaire de Configuration SQL Server pour configurer les services SQL Server et de configurer la connectivité réseau.|
| [Assistant de migration SQL Server](../ssma/sql-server-migration-assistant.md) | Utilisez l’Assistant Migration SQL Server pour automatiser la migration de base de données vers SQL Server à partir de Microsoft Access, DB2, MySQL, Oracle et Sybase.|
| [Distributed Replay](../tools/distributed-replay/install-distributed-replay-overview.md) | Utilisez la fonctionnalité de Distributed Replay pour vous aider à évaluer l’impact de futures mises à niveau de SQL Server. Utilisez également Distributed Replay pour aider à évaluer l’impact de matériel et de mises à niveau du système d’exploitation et de réglage de SQL Server. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | L’utilitaire ssbdiagnose signale des problèmes dans les conversations Service Broker ou la configuration des services de Service Broker. |


## <a name="sql-command-prompt-utilities"></a>Utilitaires d’invite de commandes SQL

  Les utilitaires d'invite de commandes vous permettent d'écrire des scripts d'opérations [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Le tableau suivant contient la liste des utilitaires d'invite de commandes fournis avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|**Utility**|**Description**|**Installé dans**|  
|-----------------|---------------------|----------------------|  
|[Utilitaire bcp](../tools/bcp-utility.md)|Utilisé pour copier des données entre une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et un fichier de données dans un format spécifié par l’utilisateur.|\<*lecteur*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Utilitaire dta](../tools/dta/dta-utility.md)|Sert à analyser une charge de travail et à recommander des structures PDS (Physical Design Structures) permettant d'optimiser les performances du serveur pour cette charge de travail.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire dtexec](../integration-services/packages/dtexec-utility.md)|Sert à configurer et à exécuter un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . La version interface utilisateur de cet utilitaire d’invite de commandes se nomme **DTExecUI**et ouvre l’utilitaire d’exécution de package.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Utilitaire dtutil](../integration-services/dtutil-utility.md)|Utilisé pour gérer les packages SSIS.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Déployer des solutions de modèle avec l'utilitaire de déploiement](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|Sert à déployer les projets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans des instances d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[MSSQL-Générateur de script (version préliminaire publique)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/17/try-new-sql-server-command-line-tools-to-generate-t-sql-scripts-and-monitor-dynamic-management-views/)|Utilisé pour générer des scripts de création et de T-SQL INSERT pour les objets de base de données de SQL Server, base de données SQL Azure et Azure SQL Data Warehouse.|Consultez notre [référentiel GitHub](https://github.com/Microsoft/sql-xplat-cli) pour le téléchargement et l’utilisation des informations.| 
|[Utilitaire osql](../tools/osql-utility.md)|Vous permet d'entrer des instructions, des procédures système et des fichiers de script [!INCLUDE[tsql](../includes/tsql-md.md)] à l'invite de commandes.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire profiler](../tools/profiler-utility.md)|Sert à démarrer [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] à partir d'une invite de commandes.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire RS.exe &#40;SSRS&#41;](../reporting-services/tools/rs-exe-utility-ssrs.md)|Sert à exécuter des scripts conçus pour gérer des serveurs de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire rsconfig &#40;SSRS&#41;](../reporting-services/tools/rsconfig-utility-ssrs.md)|Utilisé pour configurer une connexion de serveur de rapports.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire rskeymgmt &#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Sert à gérer des clés de chiffrement sur un serveur de rapports.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Application sqlagent90](../tools/sqlagent90-application.md)|Utilisé pour démarrer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent à partir d'une invite de commandes.|\<lecteur > : \Program Files\Microsoft SQL Server\\<*nom_instance*> \MSSQL\Binn|  
|[Utilitaire sqlcmd](../tools/sqlcmd-utility.md)|Vous permet d'entrer des instructions, des procédures système et des fichiers de script [!INCLUDE[tsql](../includes/tsql-md.md)] à l'invite de commandes.|\<*lecteur*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Utilitaire SQLdiag](../tools/sqldiag-utility.md)|Sert à recueillir des informations de diagnostic pour le service de support technique [!INCLUDE[msCoName](../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Application sqllogship](../tools/sqllogship-application.md)|Permet aux applications d'effectuer des opérations de restauration, de copie et de sauvegarde et les tâches de nettoyage associées pour une configuration de l'envoi de journaux sans effectuer de travaux de restauration, de copie et de sauvegarde.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilitaire SqlLocalDB](../tools/sqllocaldb-utility.md)|Mode d'exécution de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destiné aux développeurs de programme.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[Utilitaire sqlmaint](../tools/sqlmaint-utility.md)|Sert à exécuter des plans de maintenance de bases de données créés dans des versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|\<lecteur > : \Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Binn|  
|[Utilitaire sqlps](../tools/sqlps-utility.md)|Sert à exécuter des commandes et des scripts PowerShell. Charge et inscrit le fournisseur PowerShell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les cmdlets.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Application sqlservr](../tools/sqlservr-application.md)|Sert à démarrer et arrêter une instance de [!INCLUDE[ssDE](../includes/ssde-md.md)] à partir de l'invite de commandes pour le dépannage.|\<lecteur > : \Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Binn|  
|[Utilitaire Ssms](../tools/sql-server-management-studio/ssms-utility.md)|Sert à démarrer [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à partir d'une invite de commandes.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[Utilitaire tablediff](../tools/tablediff-utility.md)|Sert à comparer les données de deux tables pour détecter une non-convergence, ce qui s'avère utile lors du dépannage d'une topologie de réplication.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  

## <a name="sql-command-prompt-utilities-syntax-conventions"></a>Conventions syntaxiques des utilitaires invite de commandes SQL  
  
|**Convention**|**Utilisé pour**|  
|--------------------|------------------|  
|MAJUSCULES|Instructions et termes utilisés au niveau du système d'exploitation.|  
|`monospace`|Exemples de commandes et de code de programmation.|  
|*italique*|Paramètres fournis par l'utilisateur.|  
|**gras**|Commandes, paramètres et autres éléments de la syntaxe qui doivent être tapés exactement de la manière indiquée.|  



