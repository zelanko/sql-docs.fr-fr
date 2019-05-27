---
title: Créer un utilitaire de déploiement | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deploying packages [Integration Services], deployment utility
- deployment utility [Integration Services]
ms.assetid: 354322a4-ae8c-4d92-8e71-42d29dbd0614
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e5f7959496cfa2b473fbf5c500f424647df0a1c7
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66060229"
---
# <a name="create-a-deployment-utility"></a>Créer un utilitaire de déploiement
  La première étape de déploiement des packages consiste à créer un utilitaire de déploiement pour un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. L'utilitaire de déploiement est un dossier qui contient les fichiers dont vous avez besoin pour déployer les packages dans un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un serveur différent. L'utilitaire de déploiement est créé sur l'ordinateur sur lequel le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est stocké.  
  
 Vous créez un utilitaire de déploiement de packages pour un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en configurant d'abord le processus de création pour créer un utilitaire de déploiement de packages, puis en créant le projet. Lorsque vous créez le projet, tous les packages et configurations de package dans le projet sont automatiquement inclus. Pour déployer des fichiers supplémentaires tels que le fichier Lisez-moi avec le projet, placez les fichiers dans le dossier **Divers** du projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Lorsque le projet est généré, ces fichiers sont automatiquement inclus.  
  
 Vous pouvez configurer chaque déploiement de projet différemment. Avant de générer le projet et de créer l'utilitaire de déploiement de packages, vous pouvez définir les propriétés sur l'utilitaire de déploiement pour personnaliser la façon dont les packages du projet seront déployés. Par exemple, vous pouvez spécifier si les configurations de package peuvent être mises à jour lorsque le projet est déployé. Pour accéder aux propriétés d’un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.  
  
 Le tableau suivant récapitule les propriétés de l'utilitaire de déploiement.  
  
|Propriété|Description|  
|--------------|-----------------|  
|AllowConfigurationChange|Une valeur qui spécifie si les configurations peuvent être mises à jour lors du déploiement.|  
|CreateDeploymentUtility|Une valeur qui spécifie si un utilitaire de déploiement de packages est créé lorsque le projet est généré. Cette propriété doit être définie à `True` pour créer un utilitaire de déploiement.|  
|DeploymentOutputPath|L'emplacement, relatif au projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , de l'utilitaire de déploiement.|  
  
 Quand vous générez un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], un fichier manifeste, \<nom_projet>.SSISDeploymentManifest.xml et des copies des packages du projet et des dépendances de package sont créés et ajoutés dans le dossier bin\Deployment au sein du projet ou à l’emplacement spécifié dans la propriété DeploymentOutputPath. Le fichier manifeste répertorie les packages, les configurations de package et tous les divers autres fichiers du projet.  
  
 Le contenu du dossier de déploiement est actualisé chaque fois que vous générez le projet. Cela signifie que tout fichier enregistré dans ce dossier et qui n'est pas copié de nouveau dans le dossier par le processus de construction sera supprimé. Par exemple, les fichiers de configuration de package enregistrés dans les dossiers de déploiement seront supprimés.  
  
### <a name="to-create-a-package-deployment-utility"></a>Pour créer un utilitaire de déploiement de package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez la solution qui contient le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour lequel vous voulez créer un utilitaire de déploiement de package.  
  
2.  Cliquez avec le bouton droit sur le projet et cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **\<Pages de propriétés de <nom_projet**, cliquez sur **Utilitaire de déploiement**.  
  
4.  Pour mettre à jour les configurations de package lors du déploiement de packages, définir **AllowConfigurationChanges** à `True`.  
  
5.  Définissez `CreateDeploymentUtility` sur `True`.  
  
6.  Vous pouvez au besoin mettre à jour l'emplacement de l'utilitaire de déploiement en modifiant la propriété `DeploymentOutputPath`.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis cliquez sur **Générer**.  
  
9. Affichez la progression de la build et les erreurs de build dans la fenêtre **Sortie** .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurations du package](../../2014/integration-services/package-configurations.md)   
 [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md)   
 [Déployer des packages à l'aide de l'utilitaire de déploiement](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)   
 [Déploiement du package &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)  
  
  
