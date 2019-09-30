---
title: 'Étape 4 : Tester le package de la leçon 5 | Microsoft Docs'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 342845789df01a7803196076ea20c03a80dac9f9
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71283078"
---
# <a name="lesson-5-4-test-the-lesson-5-package"></a>Leçon 5-4 : Tester le package de la leçon 5

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Au moment de l’exécution, votre package récupère la valeur de la propriété **Directory** à partir d’une variable de configuration plutôt que du nom du répertoire spécifié lors de la création du package. La valeur de cette variable provient du fichier XML **SSISTutorial.dtsConfig**.  
  
Pour vérifier si le package met à jour la propriété **Directory** avec la nouvelle valeur lors de l’exécution, exécutez le package. Étant donné que seuls les trois exemples de fichiers de données se trouvent dans le nouveau répertoire, le flux de données s’exécute seulement trois fois.  
  
## <a name="checking-the-package-layout"></a>Vérification de la disposition du package  
Avant de tester le package, vérifiez que les flux de contrôle et de données du package de la leçon 5 ressemblent aux objets présentés dans les diagrammes suivants :  
  
**Flux de contrôle**  
  
![Flux de contrôle dans le package](../integration-services/media/task4lesson2control.gif "Flux de contrôle dans le package")  
  
**Flux de données**  
  
![Flux de données dans le package](../integration-services/media/task9lesson1data.gif "Flux de données dans le package")  
  
## <a name="test-the-lesson-5-package"></a>Tester le package de la leçon 5  
  
1.  Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.  
  
2.  Une fois l’exécution du package terminée, dans le menu **Déboguer**, sélectionnez **Arrêter le débogage**.  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 6 : Utiliser des paramètres avec le modèle de déploiement de projet dans SSIS](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
  
