---
title: Spécification des partitions et des Options de déploiement de rôles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
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
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 28be72efd82f72662bada57062d2e69e558793e3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253101"
---
# <a name="specifying-partition-and-role-deployment-options"></a>Spécification des options de déploiement de partitions et de rôles
  Le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistant Déploiement de lit les options de déploiement de rôles et de partitions à partir de la \< *nom_projet*> .deploymentoptions fichier. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée ce fichier lorsque vous générez le projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise les options de déploiement de partitions et de rôles du courant de projet lorsque le \< *nom_projet*> .deploymentoptions fichier est créé. Pour plus d'informations sur les paramètres de configuration, consultez [Précisions sur les fichiers d'entrée utilisés pour créer le script de déploiement](deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Examen des options de déploiement de partitions et de rôles  
 Les options de déploiement dans le \< *nom_projet*> .deploymentoptions fichier incluent les éléments suivants :  
  
 **Options de déploiement de partitions**  
 Le \< *nom_projet*> fichier de .deploymentoptions Spécifie si les partitions existantes de la base de données de destination sont conservées ou remplacée (option par défaut). Si les partitions existantes sont conservées, seules les nouvelles partitions sont déployées, et les partitions et les conceptions d'agrégation sur tous les groupes de mesures restent inchangées.  
  
> [!NOTE]  
>  Si le groupe de mesures dans lequel existe la partition est supprimé, la partition est supprimée automatiquement.  
  
 **Options de déploiement de rôles**  
 Le \< *nom_projet*> .deploymentoptions fichier spécifie une des options de déploiement de rôles suivantes :  
  
-   Les rôles et les membres de rôle existant dans la base de données de destination sont conservés, et seuls les nouveaux rôles et membres de rôle sont déployés.  
  
-   Tous les rôles et les membres de rôle existant dans la base de données de destination sont remplacés par les rôles et les membres de rôle déployés.  
  
-   Les rôles et les membres de rôle existant dans la base de données de destination sont conservés, et aucun nouveau rôle n'est déployé.  
  
-   **Remarque** Lorsque des membres et des rôles existants sont conservés, les autorisations associées à ces rôles sont réinitialisées à Aucune autorisation. Les autorisations de sécurité sont contenues dans les objets qu'elles sécurisent, et non dans les rôles de sécurité auxquels elles sont associées. Pour plus d'informations sur la manière de gérer ce comportement à l'aide de l'Assistant Déploiement de Analysis Services, consultez l'article relatif à la conservation de rôles et de membres dans la Base de connaissances Microsoft.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Modification des options de déploiement de partitions et de rôles  
 Vous devrez peut-être déployer la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet à l’aide des options de partitions et de rôles différentes de celles stockées dans le \< *nom_projet*> .deploymentoptions fichier. Par exemple, vous pouvez choisir de conserver des partitions existantes, les rôles et les membres du rôle, au lieu de remplacer toutes les partitions existantes, les rôles et les membres comme indiqué dans le \< *nom_projet*> .deploymentoptions fichier.  
  
 Pour modifier le déploiement de partitions et des rôles dans un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet, vous ne pouvez pas modifier les paramètres de partitions et de rôles au sein du projet, car le  *\<nom_projet >* **Pages de propriétés**  boîte de dialogue dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] n’affiche pas ces options. Si vous souhaitez modifier les options de déploiement pour les rôles et les partitions, vous devez modifier ces informations dans le \< *nom_projet*> fichier .deploymentoptions lui-même. La procédure suivante décrit comment modifier les options de déploiement de partitions et de rôles au sein de la \< *nom_projet*> .deploymentoptions fichier.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>Pour modifier le déploiement de partitions ou de rôles après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif et, sur la page **Spécifiez des options pour les partitions et les rôles** , spécifiez de nouvelles options de déploiement pour les partitions et les rôles.  
  
     —ou—  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. (Pour plus d’informations sur le mode fichier de réponses, consultez [Exécution de l’Assistant Déploiement d’Analysis Services](running-the-analysis-services-deployment-wizard.md).)  
  
     —ou—  
  
-   Ouvrez le \< *nom_projet*> .deploymentoptions dans un éditeur de texte et manuellement modifier les options.  
  
## <a name="see-also"></a>Voir aussi  
 [En spécifiant la cible d’Installation](deployment-script-files-specifying-the-installation-target.md)   
 [Spécification des paramètres de Configuration pour le déploiement de la Solution](deployment-script-files-solution-deployment-config-settings.md)   
 [Spécification d’options de traitement](deployment-script-files-specifying-processing-options.md)  
  
  
