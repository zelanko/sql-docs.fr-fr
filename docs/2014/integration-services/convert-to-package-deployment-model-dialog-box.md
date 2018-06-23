---
title: Convertir en modèle de déploiement Package, boîte de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 69d64b35f39c86b9070df9c9fcfacfcf9a7d68f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052446"
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
 [Déploiement de projets et Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)   
 [Déploiement du package &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)   
 [Assistant Conversion de projet Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  