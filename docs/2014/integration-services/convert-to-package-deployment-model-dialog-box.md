---
title: Convertir en modèle de déploiement de package, boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 73f1242b9756828b330d0386d93e3c8e8e4f2220
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84917609"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a>Convertir en modèle de déploiement de package, boîte de dialogue
  La commande **Convertir en modèle de déploiement de package** vous permet de convertir un package en modèle de déploiement de package après avoir vérifié la compatibilité du projet et de chaque package du projet avec ce modèle. Si un package utilise des fonctionnalités propres au modèle de déploiement de projet, par exemple des paramètres spécifiques, le package ne peut pas être converti.  
  
## <a name="task-list"></a>Liste des tâches  
 La conversion d'un package en modèle de déploiement de package requiert deux étapes.  
  
1.  Quand vous sélectionnez la commande **Convertir en modèle de déploiement de package** dans le menu **Projet** , le projet et les packages individuels sont examinés dans le but de garantir leur compatibilité avec ce modèle. Les résultats s’affichent dans le tableau **Résultats** .  
  
     Si le projet ou un package ne réussit pas le test de compatibilité, cliquez sur **Échec** dans la colonne **Résultat** pour obtenir des informations supplémentaires. Cliquez sur **Enregistrer le rapport** pour enregistrer une copie de ces informations dans un fichier texte.  
  
2.  Si le projet et tous les packages réussissent le test de compatibilité, cliquez sur **OK** pour convertir le package.  
  
> [!NOTE]  
>  Pour convertir un projet en modèle de déploiement de projet, utilisez **l’Assistant Conversion de projet Integration Services**. Pour plus d’informations, consultez [Assistant Conversion de projet Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de projets et de packages](packages/deploy-integration-services-ssis-projects-and-packages.md)   
 [Déploiement de packages &#40;&#41;SSIS](packages/legacy-package-deployment-ssis.md)   
 [Assistant Conversion de projet Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
