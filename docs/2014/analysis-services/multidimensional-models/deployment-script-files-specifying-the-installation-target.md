---
title: En spécifiant la cible d’Installation | Microsoft Docs
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
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a779e6ecbc32316d6d22ef8f270d9d0d2af6738e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254951"
---
# <a name="specifying-the-installation-target"></a>Spécification de la cible d'installation
  Le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistant Déploiement de lit les informations de cible d’installation à partir de la \< *nom_projet*> .deploymenttargets fichier. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée ce fichier lorsque vous générez le projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise la base de données et le serveur spécifié sur le **déploiement** page de la * \<nom_projet >* **Pages de propriétés** boîte de dialogue pour créer le \< *nom_projet*> fichier .targets.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>Modification de la cible d'installation pour le déploiement  
 Dans certaines situations, il peut s'avérer nécessaire de déployer un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vers une base de données ou une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] différente de celle spécifiée sur la page **Déploiement** . Par exemple, vous pouvez choisir de déployer le projet vers un serveur où il sera testé avant son déploiement, puis de le déployer vers un serveur de production une fois les tests terminés. Vous pouvez aussi décider de déployer un projet terminé et testé vers plusieurs serveurs de production dans un cluster d'équilibrage de la charge réseau, ou encore vers un serveur de test et un serveur de production.  
  
 Pour déployer un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vers une base de données ou une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] différente, vous pouvez modifier la cible d'installation dans le fichier d'entrée en employant l'une des méthodes décrites dans la procédure suivante.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>Pour modifier la cible d'installation après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif. Sur la page **Cible d'installation** , spécifiez une nouvelle destination pour l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et la base de données.  
  
     —ou—  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. Pour plus d'informations sur le mode fichier de réponses, consultez [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).  
  
     —ou—  
  
-   Modifier le \< *nom_projet*> fichier .deploymenttargets à l’aide de n’importe quel éditeur de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification des partitions et des Options de déploiement de rôle](deployment-script-files-partition-and-role-deployment-options.md)   
 [Spécification des paramètres de Configuration pour le déploiement de la Solution](deployment-script-files-solution-deployment-config-settings.md)   
 [Spécification d’options de traitement](deployment-script-files-specifying-processing-options.md)  
  
  
