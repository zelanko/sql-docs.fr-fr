---
title: Redéploiement de Packages | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f8b5ffb9f238fdc87ecb51765733f3a9cb632946
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038363"
---
# <a name="redeployment-of-packages"></a>Redéploiement de packages
  Après qu'un projet a été déployé, vous pouvez avoir besoin de mettre à jour ou d'étendre les fonctionnalités du package, puis de redéployer le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient les packages mis à jour. Au cours du processus de redéploiement des packages, vous devez vérifier les propriétés de configuration incluses dans l'utilitaire de déploiement. Par exemple, vous pouvez décider de ne pas autoriser les modifications de configuration après le redéploiement du package.  
  
## <a name="process-for-redeployment"></a>Processus de redéploiement  
 Après avoir mis à jour les packages, vous recréez le projet, vous copiez le dossier de déploiement sur l'ordinateur cible et vous réexécutez l'Assistant Installation de package.  
  
 Si vous ne mettez à jour que quelques packages dans le projet, vous ne souhaitez pas forcément redéployer le projet tout entier. Pour ne déployer que quelques packages, vous pouvez créer un nouveau projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , ajouter les packages mis à jour au nouveau projet, puis créer et déployer le projet. Les configurations de package sont automatiquement copiées avec le package lorsque vous l'ajoutez à un autre projet.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Déployer des Packages à l’aide de l’utilitaire de déploiement](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  