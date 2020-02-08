---
title: 'Étape 3 : Tester le package de la leçon 6 | Microsoft Docs'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0c50372c199d80dc0e6d3d7e3326918011f8a28
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "71283062"
---
# <a name="lesson-6-3-test-the-lesson-6-package"></a>Leçon 6-3 : Tester le package de la leçon 6

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Au moment de l’exécution, votre package obtient la valeur de la propriété **Directory** à partir du paramètre **VarFolderName**.  
  
Pour vérifier si le package met à jour la propriété **Directory**, exécutez le package. Comme vous avez copié trois exemples de fichiers de données dans le nouveau répertoire, le flux de données s’exécute trois fois.
  
## <a name="check-the-package-layout"></a>Vérifier la disposition du package  
Avant de tester le package, vérifiez que les flux de contrôle et de données du package de la leçon 6 ressemblent aux objets présentés dans les diagrammes suivants :   
  
**Flux de contrôle**  
  
![Flux de contrôle](../integration-services/media/task4lesson2control.gif "Flux de contrôle")  
  
**Flux de données**  
  
![Flux de données](../integration-services/media/task5lesson5data.gif "Data Flow")  
  
## <a name="test-the-lesson-6-package"></a>Tester le package de la leçon 6  
  
1.  Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.  
  
2.  Une fois l’exécution du package terminée, dans le menu **Déboguer**, sélectionnez **Arrêter le débogage**.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante
[Étape 4 : Déployer le package de la leçon 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
  
