---
title: Comprendre les fichiers d’entrée utilisés pour créer le script de déploiement | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2eb377b29ef798b4cbdd02666b866c52eb8f8599
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546871"
---
# <a name="understanding-the-input-files-used-to-create-the-deployment-script"></a>Précisions sur les fichiers d'entrée utilisés pour créer le script de déploiement
  Lorsque vous générez un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] génère des fichiers XML pour le projet. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] place ces fichiers XML dans le dossier de sortie du projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Par défaut, les sorties sont envoyées au dossier \Bin. Le tableau suivant répertorie les fichiers XML que crée [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
|Fichier XMLA|Description|  
|---------------|-----------------|  
|\<*project name*>. asdatabase|Contient les définitions déclaratives de tous les objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] du projet.|  
|\<*project name*>. deploymenttargets|Contient le nom de l'instance et de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans lesquelles les objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] seront créés.|  
|\<*project name*>. configsettings|Contient des paramètres spécifiques à l'environnement, par exemple des informations sur la connexion à une source de données et les emplacements de stockage des objets. Les paramètres de ce fichier remplacent les paramètres dans le \<*project name*> fichier. asdatabase.|  
|\<*project name*>. deploymentoptions|Contient des options de déploiement qui déterminent, par exemple, si le déploiement est transactionnel et si les objets déployés doivent être traités après le déploiement.|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ne stocke jamais les mots de passe dans ses fichiers de projet.  
  
## <a name="modifying-the-input-files"></a>Modification des fichiers d'entrée  
 La modification des valeurs dans les fichiers d’entrée, ou les valeurs récupérées à partir des fichiers d’entrée, permet de modifier la destination du déploiement, les paramètres de configuration et les options de déploiement sans modifier la totalité du \<*project name*> fichier. asdatabase (ou un fichier de script XMLA entier si vous générez un script à partir d’une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données existante). La possibilité de modifier des fichiers individuels vous permet de créer facilement des scripts de déploiement différents selon les buts poursuivis.  
  
 Les rubriques suivantes expliquent comment modifier des valeurs dans les divers fichiers d'entrée :  
  
-   [Spécification de la cible d'installation](deployment-script-files-specifying-the-installation-target.md)  
  
-   [Spécification des options de déploiement de partitions et de rôles](deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [Spécification de paramètres de configuration pour le déploiement de solutions](deployment-script-files-solution-deployment-config-settings.md)  
  
-   [Spécification d'options de traitement](deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de l’Assistant Déploiement de Analysis Services](running-the-analysis-services-deployment-wizard.md)   
 [Description du script de déploiement Analysis Services](understanding-the-analysis-services-deployment-script.md)  
  
  
