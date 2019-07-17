---
title: Spécification des partitions et des Options de déploiement de rôles | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8bd62cc5fef3ef13dede85c06b28b0501a83de2f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178453"
---
# <a name="deployment-script-files---partition-and-role-deployment-options"></a>Fichiers de script de déploiement - Options de déploiement de partitions et de rôles
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistant Déploiement de lit les options de déploiement de rôles et de partitions à partir de la \< *nom_projet*> .deploymentoptions fichier. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée ce fichier lorsque vous générez le projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise les options de déploiement de partitions et de rôles du courant de projet lorsque le \< *nom_projet*> .deploymentoptions fichier est créé. Pour plus d'informations sur les paramètres de configuration, consultez [Précisions sur les fichiers d'entrée utilisés pour créer le script de déploiement](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md).  
  
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
  
-   **Remarque** Lorsque des membres et des rôles existants sont conservés, les autorisations associées à ces rôles sont réinitialisées à Aucune autorisation. Les autorisations de sécurité sont contenues dans les objets qu'elles sécurisent, et non dans les rôles de sécurité auxquels elles sont associées. Pour plus d’informations sur la façon de travailler avec ce comportement à l’aide de l’Assistant Déploiement d’Analysis Service, consultez « Conservation de rôles et membres » dans la Base de connaissances Microsoft.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Modification des options de déploiement de partitions et de rôles  
 Vous devrez peut-être déployer la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet à l’aide des options de partitions et de rôles différentes de celles stockées dans le \< *nom_projet*> .deploymentoptions fichier. Par exemple, vous pouvez choisir de conserver des partitions existantes, les rôles et les membres du rôle, au lieu de remplacer toutes les partitions existantes, les rôles et les membres comme indiqué dans le \< *nom_projet*> .deploymentoptions fichier.  
  
 Pour modifier le déploiement de partitions et des rôles dans un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet, vous ne pouvez pas modifier les paramètres de partitions et de rôles au sein du projet, car le  *\<nom_projet >* **Pages de propriétés**  boîte de dialogue dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] n’affiche pas ces options. Si vous souhaitez modifier les options de déploiement pour les rôles et les partitions, vous devez modifier ces informations dans le \< *nom_projet*> fichier .deploymentoptions lui-même. La procédure suivante décrit comment modifier les options de déploiement de partitions et de rôles au sein de la \< *nom_projet*> .deploymentoptions fichier.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>Pour modifier le déploiement de partitions ou de rôles après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif et, sur la page **Spécifiez des options pour les partitions et les rôles** , spécifiez de nouvelles options de déploiement pour les partitions et les rôles.  
  
     ou  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. (Pour plus d’informations sur le mode fichier de réponses, consultez [Exécution de l’Assistant Déploiement d’Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).)  
  
     ou  
  
-   Ouvrez le \< *nom_projet*> .deploymentoptions dans un éditeur de texte et manuellement modifier les options. Les options de PartitionDeployment sont DeployPartitions, RetainPartitions. Les options de RoleDeployment sont DeployRolesAndMembers, DeployRolesRetainMembers, RetainRoles.
  
## <a name="see-also"></a>Voir aussi  
 [Spécification de la cible d'installation](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [Spécification de paramètres de configuration pour le déploiement de solutions](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)   
 [Spécification d'options de traitement](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  
