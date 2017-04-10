---
title: "Sp&#233;cification des options de d&#233;ploiement de partitions et de r&#244;les | Microsoft Docs"
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
  - "partitions [Analysis Services], options de déploiement"
  - "déploiements Analysis Services, rôles"
  - "déploiements Analysis Services, partitions"
  - "Assistant Déploiement d’Analysis Services, rôles"
  - "Assistant Déploiement d’Analysis Services, partitions"
  - "déploiement [Analysis Services], rôles"
  - "rôles [Analysis Services], options de déploiement"
  - "déploiement [Analysis Services], partitions"
  - "modification de déploiements de rôles"
  - "modification de déploiements de partitions"
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Sp&#233;cification des options de d&#233;ploiement de partitions et de r&#244;les
  L’Assistant Déploiement d’[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lit les options de déploiement de rôles et de partitions à partir du fichier \<*nom_projet*>.deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée ce fichier lorsque vous générez le projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise les options de déploiement de rôles et de partitions du projet actuel quand le fichier \<*nom_projet*>.deploymentoptions est créé. Pour plus d'informations sur les paramètres de configuration, consultez [Understanding the Input Files Used to Create the Deployment Script](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md).  
  
## Examen des options de déploiement de partitions et de rôles  
 Les options de déploiement figurant dans le fichier \<*nom_projet*>.deploymentoptions sont les suivantes :  
  
 **Options de déploiement de partitions**  
 Le fichier \<*nom_projet*>.deploymentoptions spécifie si les partitions existantes de la base de données de destination sont conservées ou remplacées (option par défaut). Si les partitions existantes sont conservées, seules les nouvelles partitions sont déployées, et les partitions et les conceptions d'agrégation sur tous les groupes de mesures restent inchangées.  
  
> [!NOTE]  
>  Si le groupe de mesures dans lequel existe la partition est supprimé, la partition est supprimée automatiquement.  
  
 **Options de déploiement de rôles**  
 Le fichier \<*nom_projet*>.deploymentoptions spécifie l’une des options de déploiement de rôles suivantes :  
  
-   Les rôles et les membres de rôle existant dans la base de données de destination sont conservés, et seuls les nouveaux rôles et membres de rôle sont déployés.  
  
-   Tous les rôles et les membres de rôle existant dans la base de données de destination sont remplacés par les rôles et les membres de rôle déployés.  
  
-   Les rôles et les membres de rôle existant dans la base de données de destination sont conservés, et aucun nouveau rôle n'est déployé.  
  
-   **Remarque** Lorsque des membres et des rôles existants sont conservés, les autorisations associées à ces rôles sont réinitialisées à Aucune autorisation. Les autorisations de sécurité sont contenues dans les objets qu'elles sécurisent, et non dans les rôles de sécurité auxquels elles sont associées. Pour plus d'informations sur la manière de gérer ce comportement à l'aide de l'Assistant Déploiement de Analysis Services, consultez l'article relatif à la conservation de rôles et de membres dans la Base de connaissances Microsoft.  
  
## Modification des options de déploiement de partitions et de rôles  
 Vous pouvez être amené à déployer le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en utilisant des options de partitions et de rôles différentes de celles stockées dans le fichier \<*nom_projet*>.deploymentoptions. Par exemple, vous pouvez choisir de conserver des partitions, des rôles et des membres de rôle existants, plutôt que de remplacer la totalité des partitions, rôles et membres de rôle existants comme indiqué dans le fichier \<*nom_projet*>.deploymentoptions.  
  
 Pour modifier le déploiement des partitions et des rôles dans un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous ne pouvez pas changer les paramètres de partitions et de rôles au sein du projet, car la boîte de dialogue **Pages de propriétés** *\<nom_projet>* de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] n’affiche pas ces options. Si vous voulez modifier les options de déploiement pour les rôles et les partitions, vous devez le faire dans le fichier \<*nom_projet*>.deploymentoptions proprement dit. La procédure ci-après décrit comment modifier les options de déploiement des partitions et des rôles dans le fichier \<*nom_projet*>.deploymentoptions.  
  
#### Pour modifier le déploiement de partitions ou de rôles après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif et, sur la page **Spécifiez des options pour les partitions et les rôles** , spécifiez de nouvelles options de déploiement pour les partitions et les rôles.  
  
     —ou—  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. (Pour plus d’informations sur le mode fichier de réponses, consultez [Exécution de l’Assistant Déploiement d’Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).)  
  
     —ou—  
  
-   Ouvrez le fichier \<*nom_projet*>.deploymentoptions dans un éditeur de texte et modifiez les options manuellement.  
  
## Voir aussi  
 [Spécification de la cible d'installation](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)   
 [Spécification de paramètres de configuration pour le déploiement de solutions](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)   
 [Spécification d'options de traitement](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  