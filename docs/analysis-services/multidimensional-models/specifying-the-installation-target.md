---
title: "Sp&#233;cification de la cible d&#39;installation | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers d'entrée [Analysis Services]"
  - "cibles d'installation [Analysis Services]"
  - "déploiements Analysis Services, cibles d’installation"
  - "Assistant Déploiement d’Analysis Services, cibles d’installation"
  - "déploiement [Analysis Services], cibles d’installation"
  - "modification de cibles d'installation"
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: 35
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Sp&#233;cification de la cible d&#39;installation
  L’Assistant Déploiement d’[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lit les informations sur la cible d’installation dans le fichier \<*nom_projet*>.deploymenttargets. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée ce fichier lorsque vous générez le projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise la base de données et le serveur spécifiés dans la page **Déploiement** de la boîte de dialogue *<nom_projet>\>* **Pages de propriétés** pour créer le fichier \<*nom_projet*>.targets.  
  
## Modification de la cible d'installation pour le déploiement  
 Dans certaines situations, il peut s'avérer nécessaire de déployer un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vers une base de données ou une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] différente de celle spécifiée sur la page **Déploiement** . Par exemple, vous pouvez choisir de déployer le projet vers un serveur où il sera testé avant son déploiement, puis de le déployer vers un serveur de production une fois les tests terminés. Vous pouvez aussi décider de déployer un projet terminé et testé vers plusieurs serveurs de production dans un cluster d'équilibrage de la charge réseau, ou encore vers un serveur de test et un serveur de production.  
  
 Pour déployer un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vers une base de données ou une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] différente, vous pouvez modifier la cible d'installation dans le fichier d'entrée en employant l'une des méthodes décrites dans la procédure suivante.  
  
#### Pour modifier la cible d'installation après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif. Sur la page **Cible d'installation** , spécifiez une nouvelle destination pour l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et la base de données.  
  
     —ou—  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. Pour plus d'informations sur le mode fichier de réponses, consultez [Running the Analysis Services Deployment Wizard](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     —ou—  
  
-   Modifiez le fichier \<*nom_projet*>.deploymenttargets à l’aide d’un éditeur de texte.  
  
## Voir aussi  
 [Spécification des options de déploiement de partitions et de rôles](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)   
 [Spécification de paramètres de configuration pour le déploiement de solutions](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)   
 [Spécification d'options de traitement](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  