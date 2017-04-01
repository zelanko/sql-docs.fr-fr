---
title: "Pr&#233;cisions sur les fichiers d&#39;entr&#233;e utilis&#233;s pour cr&#233;er le script de d&#233;ploiement | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers d'entrée [Analysis Services]"
  - "Assistant Déploiement d’Analysis Services, scripts"
  - "déploiement [Analysis Services], fichiers d’entrée"
  - "Assistant Déploiement d’Analysis Services, fichiers d’entrée"
  - "scripts [Analysis Services], déploiement"
  - "déploiements Analysis Services, fichiers d’entrée"
  - "modification de fichiers d'entrée"
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Pr&#233;cisions sur les fichiers d&#39;entr&#233;e utilis&#233;s pour cr&#233;er le script de d&#233;ploiement
  Lorsque vous générez un projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] génère les fichiers XML du projet. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] place ces fichiers XML dans le dossier de sortie du projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Par défaut, les sorties sont envoyées au dossier \\Bin. Le tableau suivant répertorie les fichiers XML que crée [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
|Fichier XMLA|Description|  
|---------------|-----------------|  
|\<*nom du projet*\>.asdatabase|Contient les définitions déclaratives de tous les objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] du projet.|  
|\<*nom du projet*\>.deploymenttargets|Contient le nom de l'instance et de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans lesquelles les objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] seront créés.|  
|\<*nom du projet*\>.configsettings|Contient des paramètres spécifiques à l'environnement, par exemple des informations sur la connexion à une source de données et les emplacements de stockage des objets. Les paramètres de ce fichier remplacent ceux définis dans le fichier \<*nom du projet*\>.asdatabase.|  
|\<*nom du projet*\>.deploymentoptions|Contient des options de déploiement qui déterminent, par exemple, si le déploiement est transactionnel et si les objets déployés doivent être traités après le déploiement.|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ne stocke jamais les mots de passe dans ses fichiers de projet.  
  
## Modification des fichiers d'entrée  
 La modification des valeurs dans les fichiers d’entrée ou des valeurs récupérées des fichiers d’entrée permet de changer la destination du déploiement, les paramètres de configuration et les options de déploiement sans modifier la totalité du fichier \<*nom du projet*\>.asdatabase \(ou l’intégralité d’un fichier de script XMLA si vous générez un script à partir d’une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] existante\). La possibilité de modifier des fichiers individuels vous permet de créer facilement des scripts de déploiement différents selon les buts poursuivis.  
  
 Les rubriques suivantes expliquent comment modifier des valeurs dans les divers fichiers d'entrée :  
  
-   [Spécification de la cible d'installation](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)  
  
-   [Spécification des options de déploiement de partitions et de rôles](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)  
  
-   [Spécification de paramètres de configuration pour le déploiement de solutions](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)  
  
-   [Spécification d'options de traitement](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
## Voir aussi  
 [Exécution de l'Assistant Déploiement d'Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Description du script de déploiement Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)  
  
  