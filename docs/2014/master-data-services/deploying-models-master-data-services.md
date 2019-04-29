---
title: Déploiement de modèles (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 58f946f89691a6e26ba4402166b8ad725e7a977c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925053"
---
# <a name="deploying-models-master-data-services"></a>Déploiement de modèles (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], un package est un fichier XML qui contient une structure de modèle déployable et, éventuellement, les données du modèle. Utilisez les packages de modèle pour déplacer des copies de modèles d'un environnement MDS vers un autre, ou pour créer de nouveaux modèles dans votre environnement MDS existant.  
  
> [!IMPORTANT]  
>  Les packages peuvent être déployés uniquement dans l'édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans laquelle ils ont été créés. Cela signifie que les packages créés dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ne peuvent pas être déployés sur [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ou les versions ultérieures.  
  
## <a name="tools-for-deploying-models"></a>Outils pour déployer des modèles  
 Pour utiliser les packages de modèles, vous pouvez opter pour l'un des trois outils, selon vos besoins.  
  
-   **Outil MDSModelDeploy** : pour créer et déployer des objets de modèle et des données, utilisez l’outil MDSModelDeploy.exe. Si vous avez sélectionné le chemin d’accès par défaut lors de l’installation de MDS, cet outil se trouve sur *lecteur*: \Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
-   **Assistant Déploiement de modèle** : pour créer et déployer des packages de la structure de modèle uniquement, utilisez l’Assistant dans l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Vous ne pouvez pas utiliser cet Assistant pour déployer des données.  
  
-   **Éditeur de package de modèle** : pour modifier un package de modèle, utilisez l’outil ModelPackageEditor.exe qui lance l’Assistant Éditeur de package de modèle. Vous utilisez cet Assistant pour modifier un package créé par l'outil MDSModelDeploy ou l'Assistant Déploiement de modèle. Si vous avez sélectionné le chemin d’accès par défaut lors de l’installation de MDS, cet outil se trouve sur *lecteur*: \Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
> [!IMPORTANT]  
>  Vous pouvez utiliser MDSDeployModel pour créer un modèle, créer un clone d'un modèle ou mettre à jour un modèle existant et ses données. Si vous utilisez l'outil MDSModelDeploy pour mettre à jour un modèle existant et ses données et que le package ne contient pas une entité, un attribut ou un membre existant dans le modèle de destination, MDSModelDeploy ne supprime pas cette entité, cet attribut ou ce membre du modèle.  
  
## <a name="what-packages-contain"></a>Contenu des packages  
 Un package de modèle est un fichier XML enregistré avec l'extension .pkg. Lorsque vous créez un package de déploiement, vous pouvez décider s'il convient d'inclure ou non des données. Si vous décidez d'inclure des données, vous devez sélectionner une version des données à inclure.  
  
 Tous les objets de modèle sont inclus dans un package. Ces objets sont :  
  
-   Entités  
  
-   Attributs  
  
-   Groupes d'attributs  
  
-   Hierarchies  
  
-   Collections  
  
-   Règles d'entreprise  
  
-   Indicateurs de version  
  
-   Vues d'abonnement  
  
 Les métadonnées définies par l'utilisateur, les attributs de fichier et les autorisations d'accès ne sont pas incluses. Après avoir déployé un modèle, vous devez les mettre à jour manuellement.  
  
## <a name="sample-packages"></a>Exemples de packages  
 Des fichiers d'exemple de package sont inclus lorsque vous installez [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Ils se trouvent dans le répertoire Master Data Services\Samples\Packages où vous avez installé [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Lorsque vous déployez ces exemples de packages à l'aide de l'outil MDSModelDeploy, les exemples de modèles sont créés et remplis avec les données.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créez un nouveau package de déploiement d'objets de modèle et/ou de données à l'aide de l'outil MDSModelDeploy.|[Créer un package de déploiement de modèle à l'aide de MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Créez un nouveau package de déploiement d'objets de modèle uniquement à l'aide de l'Assistant.|[Créer un package de déploiement de modèle à l’aide de l’Assistant](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|Déployez un package d'objets de modèle et des données à l'aide de l'outil MDSModelDeploy.|[Déployer un package de déploiement de modèle à l’aide de MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Déployez un package d'objets de modèle uniquement à l'aide de l'Assistant.|[Déployer un package de déploiement de modèle à l'aide de l'Assistant](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|Modifiez un package de déploiement de modèle pour déployer les parties sélectionnées d'un modèle, plutôt que le modèle entier.|[Modifier un package de déploiement de modèle](../../2014/master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Options de déploiement de modèle &#40;Master Data Services&#41;](model-deployment-options-master-data-services.md)  
  
  
