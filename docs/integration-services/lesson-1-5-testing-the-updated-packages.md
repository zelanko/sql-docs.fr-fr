---
title: "Étape 5 : Test des packages mis à jour | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c56a94dbe6235c7448b91e7f29037430ec4e8828
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="lesson-1-5---testing-the-updated-packages"></a>Leçon 1-5 : Test des packages mis à jour
Avant d'aborder la leçon suivante où vous allez créer l'application de déploiement qui sert à installer les packages sur l'ordinateur de destination, vous devez tester les packages. A cours de cette tâche, vous allez exécuter les packages DataTransfer.dtsx et LoadXMLData que vous avez ajoutés au projet Didacticiel de déploiement puis étendus avec des configurations.  
  
Lors de l'exécution des packages, chaque exécutable du package prend la couleur vert au terme de son exécution correcte. Lorsque tous les exécutables sont vert, le package s'est achevé correctement. Vous pouvez aussi consulter la progression de l'exécution du package sous l'onglet **Progression** .  
  
Si les packages ne s'exécutent pas correctement, vous devez les corriger avant d'aborder la leçon suivante.  
  
### <a name="to-run-the-datatransfer-package"></a>Pour exécuter le package DataTransfer  
  
1.  Dans l'Explorateur de solutions, cliquez sur DataTransfer.dtsx.  
  
2.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
3.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
### <a name="to-run-the-loadxmldata-package"></a>Pour exécuter le package LoadXMLData  
  
1.  Dans l'Explorateur de solutions, cliquez sur LoadXMLData.dtsx.  
  
2.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
3.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 2 : Créer l’application de déploiement dans SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
  
  
