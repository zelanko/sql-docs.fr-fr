---
title: 'Étape 3 : Test du package du didacticiel de la leçon 3 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ffa1849e099e670b5fa13db399af67883e8806c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440466"
---
# <a name="step-3-testing-the-lesson-3-tutorial-package"></a>Étape 3 : Test du package du tutoriel de la leçon 3
  Dans cette tâche, vous allez exécuter le package Lesson 3.dtsx. Lors de l'exécution du package, la fenêtre Journaux d'événements répertorie les entrées inscrites dans le fichier journal. Une fois l'exécution du package terminée, vous allez vérifier le contenu du fichier journal qui a été généré par le fournisseur d'informations.  
  
## <a name="checking-the-package-layout"></a>Vérification de la disposition du package  
 Avant de tester le package, vous devez vérifier que le flux de contrôle et le flux de données dans le package de la leçon 3 contiennent les objets affichés dans les diagrammes suivants. Le flux de contrôle doit être identique au flux de contrôle de la leçon 2. Le flux de données doit être identique au flux de données des leçons 1 et 2.  
  
 **Workflow de contrôle**  
  
 ![Flux de contrôle dans le package](../../2014/tutorials/media/task4lesson2control.gif "Flux de contrôle dans le package")  
  
 **Flux de données**  
  
 ![Flux de données dans le package](../../2014/tutorials/media/task9lesson1data.gif "Flux de données dans le package")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>Pour exécuter le package du didacticiel Lesson 4  
  
1.  Dans le menu SSIS, cliquez sur Journaux d'événements.  
  
2.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
3.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
### <a name="to-examine-the-generated-log-file"></a>Pour examiner le fichier journal généré  
  
-   Utilisez le Bloc-notes ou un autre éditeur de texte et ouvrez le fichier TutorialLog.log.  
  
-   Bien que la sémantique des informations générées pour les `PipelineExecutionPlan` `PipelineExecutionTrees` événements et dépasse le cadre de ce didacticiel, vous pouvez voir que la première ligne répertorie les champs d’information spécifiés dans l’onglet **Détails** de la boîte de dialogue **configurer les journaux SSIS** . De plus, vous pouvez vérifier que les deux événements sélectionnés, PipelineExecutionPlan et PipelineExecutionTrees, ont été enregistrés pour chaque itération de la boucle Foreach.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 4 : Ajout de redirection de flux d’erreurs](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
