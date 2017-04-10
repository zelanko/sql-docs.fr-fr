---
title: "Ex&#233;cuter des packages Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "packages Integration Services, exécution"
  - "packages SSIS, exécution"
  - "packages [Integration Services], exécution"
  - "packages SQL Server Integration Services, exécution"
  - "exécution de packages [Integration Services]"
  - "exécution de packages [Integration Services]"
  - "Integration Services, (voir aussi Packages Integration Services)"
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
caps.latest.revision: 65
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 61
---
# Ex&#233;cuter des packages Integration Services (SSIS)
  Pour exécuter un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous pouvez utiliser un outil parmi plusieurs, en fonction de l’endroit où ces packages sont stockés. Ces outils sont répertoriées dans le tableau ci-dessous.  
  
 Pour stocker un package sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous utilisez le modèle de déploiement de projet pour déployer le projet sur le serveur. Pour plus d’informations, consultez [Déployer des projets sur le serveur Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
 Pour stocker un package dans le magasin de packages SSIS, la base de données msdb ou dans le système de fichiers, vous utilisez le modèle de déploiement de package. Pour plus d’informations, consultez [Déploiement de packages hérités &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md).  
  
|Outil|Packages stockés sur le serveur Integration Services|Packages stockés dans le magasin de packages SSIS ou dans la base de données msdb|Packages stockés dans le système de fichiers, hors de l'emplacement qui fait partie du magasin de packages SSIS|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**Outils de données SQL Server**|Non|Non<br /><br /> Vous pouvez cependant ajouter un package existant à un projet du magasin de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] , qui inclut la base de données msdb. L'ajout d'un package existant au projet de cette manière effectue une copie locale du package dans le système de fichiers.|Oui|  
|**SQL Server Management Studio, quand vous êtes connecté à une instance du moteur de base de données qui héberge le serveur Integration Services**<br /><br /> Pour plus d’informations, consultez [Boîte de dialogue d’exécution de package](../../integration-services/packages/execute-package-dialog-box.md)|Oui|Non<br /><br /> Vous pouvez toutefois importer un package vers le serveur à partir de ces emplacements.|Non<br /><br /> Vous pouvez toutefois importer un package vers le serveur à partir du système de fichiers.|
|**SQL Server Management Studio, quand vous êtes connecté à une instance du moteur de base de données qui héberge le serveur Integration Services**<br /><br /> Pour plus d’informations, consultez [Exécuter des packages dans Scale Out](../../integration-services/run-packages-in-integration-services-ssis-scale-out.md)|Oui|Non|Non|
|**SQL Server Management Studio, quand il est connecté au service Integration Services qui gère le magasin de packages SSIS**|Non|Oui|Non<br /><br /> Vous pouvez cependant importer un package dans le magasin de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] à partir du système de fichiers.|  
|**dtexec**<br /><br /> Pour plus d’informations, voir [dtexec Utility](../../integration-services/packages/dtexec-utility.md).|Oui|Oui|Oui|  
|**dtexecui**<br /><br /> Pour plus d’informations, consultez [Référence de l’interface utilisateur de l’utilitaire d’exécution de package &#40;DtExecUI&#41;](../../integration-services/packages/execute-package-utility-dtexecui-ui-reference.md)|Non|Oui|Oui|  
|**SQL Server Agent**<br /><br /> Vous pouvez utiliser un travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour planifier un package.<br /><br /> Pour plus d’informations, consultez [Travaux de l’Agent SQL Server pour les packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md).|Oui|Oui|Oui|  
|**Procédure stockée intégrée**<br /><br /> Pour plus d’informations, consultez [catalog.start_execution &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)|Oui|Non|Non|  
|**API managée, en utilisant des types et des membres de l’espace de noms **<xref:Microsoft.SqlServer.Management.IntegrationServices>|Oui|Non|Non|  
|**API managée, en utilisant des types et des membres de l’espace de noms **<xref:Microsoft.SqlServer.Dts.Runtime>|Actuellement impossible|Oui|Oui|  
  
## <a name="execution-and-logging"></a>Exécution et journalisation  
 Les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] peuvent être activés pour la journalisation et vous pouvez capturer des informations sur l'exécution dans des fichiers journaux. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md).  
  
 Vous pouvez surveiller des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] déployés et exécutés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à l’aide des rapports de fonctionnement. Les rapports sont disponibles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d'informations, consultez [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Planifier un package à l’aide de SQL Server Agent](../../integration-services/packages/schedule-a-package-by-using-sql-server-agent.md)  
  
-   [Exécuter un package dans les outils de données SQL Server](../../integration-services/packages/run-a-package-in-sql-server-data-tools.md)  
  
-   [Exécuter un package sur le serveur SSIS à l’aide de SQL Server Management Studio](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire dtexec](../../integration-services/packages/dtexec-utility.md)   
[Démarrer l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)
  
  