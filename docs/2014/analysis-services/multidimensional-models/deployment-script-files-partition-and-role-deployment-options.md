---
title: Spécification des options de déploiement de partitions et de rôles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- partitions [Analysis Services], deployment options
- Analysis Services deployments, roles
- Analysis Services deployments, partitions
- Analysis Services Deployment Wizard, roles
- Analysis Services Deployment Wizard, partitions
- deploying [Analysis Services], roles
- roles [Analysis Services], deployment options
- deploying [Analysis Services], partitions
- modifying role deployments
- modifying partition deployments
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
author: minewiskan
ms.author: owend
ms.openlocfilehash: f4f2f5bb2f3f39636541d5aea5b931b1dcc72534
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546861"
---
# <a name="specifying-partition-and-role-deployment-options"></a>Spécification des options de déploiement de partitions et de rôles
  L' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistant Déploiement de lit les options de déploiement de partitions et de rôles à partir du \<*project name*> fichier. deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]crée ce fichier lorsque vous générez le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]utilise les options de déploiement de partitions et de rôles du projet actif lors de la \<*project name*> création du fichier. deploymentoptions. Pour plus d'informations sur les paramètres de configuration, consultez [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Examen des options de déploiement de partitions et de rôles  
 Les options de déploiement dans le \<*project name*> fichier. deploymentoptions sont les suivantes :  
  
 **Options de déploiement de partitions**  
 Le \<*project name*> fichier. deploymentoptions spécifie si les partitions existantes dans la base de données de destination sont conservées ou remplacées (par défaut). Si les partitions existantes sont conservées, seules les nouvelles partitions sont déployées, et les partitions et les conceptions d'agrégation sur tous les groupes de mesures restent inchangées.  
  
> [!NOTE]  
>  Si le groupe de mesures dans lequel existe la partition est supprimé, la partition est supprimée automatiquement.  
  
 **Options de déploiement de rôles**  
 Le \<*project name*> fichier. deploymentoptions spécifie l’une des options de déploiement de rôle suivantes :  
  
-   Les rôles et les membres de rôle existant dans la base de données de destination sont conservés, et seuls les nouveaux rôles et membres de rôle sont déployés.  
  
-   Tous les rôles et les membres de rôle existant dans la base de données de destination sont remplacés par les rôles et les membres de rôle déployés.  
  
-   Les rôles et les membres de rôle existant dans la base de données de destination sont conservés, et aucun nouveau rôle n'est déployé.  
  
-   **Remarque** Lorsque des membres et des rôles existants sont conservés, les autorisations associées à ces rôles sont réinitialisées à Aucune autorisation. Les autorisations de sécurité sont contenues dans les objets qu'elles sécurisent, et non dans les rôles de sécurité auxquels elles sont associées. Pour plus d’informations sur l’utilisation de ce comportement à l’aide de l’Assistant Déploiement d’Analysis Services, consultez la rubrique relative à la conservation des rôles et des membres dans la base de connaissances Microsoft.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Modification des options de déploiement de partitions et de rôles  
 Vous devrez peut-être déployer le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet en utilisant des options de partitions et de rôles différentes de celles stockées dans le \<*project name*> fichier. deploymentoptions. Par exemple, vous souhaiterez peut-être conserver les partitions, rôles et membres de rôle existants, au lieu de remplacer toutes les partitions, rôles et membres existants comme indiqué dans le \<*project name*> fichier. deploymentoptions.  
  
 Pour modifier le déploiement des partitions et des rôles dans un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet, vous ne pouvez pas modifier les paramètres de partitions et de rôles dans le projet, car la *\<project name>* boîte de dialogue **pages de propriétés** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] n’affiche pas ces options. Si vous souhaitez modifier les options de déploiement pour les rôles et les partitions, vous devez modifier ces informations dans le \<*project name*> fichier. deploymentoptions lui-même. La procédure suivante décrit comment modifier les options de déploiement de partitions et de rôles dans le \<*project name*> fichier. deploymentoptions.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>Pour modifier le déploiement de partitions ou de rôles après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif et, sur la page **Spécifiez des options pour les partitions et les rôles** , spécifiez de nouvelles options de déploiement pour les partitions et les rôles.  
  
     -ou-  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. (Pour plus d’informations sur le mode fichier de réponses, consultez [exécution de l’Assistant Déploiement de Analysis Services](running-the-analysis-services-deployment-wizard.md).)  
  
     -ou-  
  
-   Ouvrez le \<*project name*> . deploymentoptions dans n’importe quel éditeur de texte et modifiez manuellement les options.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification de la cible d’installation](deployment-script-files-specifying-the-installation-target.md)   
 [Spécification des paramètres de configuration pour le déploiement de solutions](deployment-script-files-solution-deployment-config-settings.md)   
 [Spécification d'options de traitement](deployment-script-files-specifying-processing-options.md)  
  
  
