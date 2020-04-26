---
title: Déploiement de packages (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c912d4417842bc332262549cc604b97eaa50a44d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62767088"
---
# <a name="package-deployment-ssis"></a>Déploiement de packages (SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] comprend des outils et des assistants qui facilitent le déploiement de packages de l’ordinateur de développement au serveur de production ou à d’autres ordinateurs.  
  
 Ce processus de déploiement de package se déroule en quatre étapes :  
  
1.  La première étape est facultative et implique la création de configurations de package qui mettent à jour les propriétés des éléments de package au moment de l'exécution. Les configurations sont automatiquement incluses lorsque vous déployez les packages.  
  
2.  La deuxième étape consiste à générer le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] afin de créer un utilitaire de déploiement de package. L'utilitaire de déploiement du projet contient les packages à déployer.  
  
3.  La troisième étape consiste à copier, sur l'ordinateur cible, le dossier de déploiement créé lors de la génération du projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
4.  La quatrième étape consiste à exécuter l’Assistant Installation de package sur l’ordinateur cible pour installer les packages sur le système de fichiers ou une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la création d’un utilitaire de déploiement, consultez [Créer un utilitaire de déploiement](../create-a-deployment-utility.md).  
  
 Pour plus d’informations sur le déploiement de packages à l’aide de l’utilitaire de déploiement, consultez [Déployer des packages à l’aide de l’utilitaire de déploiement](../deploy-packages-by-using-the-deployment-utility.md).  
  
 Pour plus d’informations sur la création de configurations de package, consultez [Créer des configurations de package](../create-package-configurations.md).  
  
  
