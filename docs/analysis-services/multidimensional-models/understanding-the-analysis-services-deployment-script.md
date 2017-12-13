---
title: "Présentation de l’analyse du Script de déploiement des Services | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], scripts
- Analysis Services deployments, scripts
- scripts [Analysis Services], deployment
ms.assetid: a63ebee9-9848-48f1-82ad-64ecf2e47019
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9b5850dafa57e967da3c79146424023b25f9fd33
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="understanding-the-analysis-services-deployment-script"></a>Description du script de déploiement Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Le script de déploiement XMLA généré par le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistant de déploiement se compose de deux sections :  
  
-   La première partie du script de déploiement contient les commandes nécessaires à la création, la modification ou la suppression des objets [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appropriés dans la base de données de destination. Par défaut, les fichiers d'entrée générés par le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont basés sur un déploiement incrémentiel. Par conséquent, le script de déploiement XMLA n'affecte que les objets qui ont été modifiés ou supprimés.  
  
-   La seconde partie du script de déploiement contient les commandes requises pour traiter uniquement les objets créés ou modifiés sur le serveur de destination (option Traiter par défaut) ou pour traiter intégralement la base de données de destination. Vous pouvez également décider que le script de déploiement ne contiendra aucune commande de traitement.  
  
 L'ensemble du script de déploiement peut être exécuté dans une seule transaction ou dans plusieurs transactions. Si le script est exécuté dans plusieurs transactions, la première partie du script est exécutée sous la forme d'une seule transaction, et chaque objet est traité dans sa propre transaction.  
  
> [!IMPORTANT]  
>  L’Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déploie les objets uniquement dans une seule base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Il ne déploie pas des objets, ni des données au niveau du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de l'Assistant Déploiement d'Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Précisions sur les fichiers d'entrée utilisés pour créer le script de déploiement](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)  
  
  
