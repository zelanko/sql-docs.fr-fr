---
title: "Étape 5 : Test des Packages mis à jour | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 55dae3d13775100b6d443dfc8d97948c3f621c01
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-1-5---testing-the-updated-packages"></a>Leçon 1-5 : test des Packages mis à jour
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
  
  
  

