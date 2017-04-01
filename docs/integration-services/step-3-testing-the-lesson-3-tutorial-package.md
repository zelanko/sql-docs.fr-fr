---
title: "&#201;tape 3 : Test de la le&#231;on 3 du package du didacticiel | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# &#201;tape 3 : Test de la le&#231;on 3 du package du didacticiel
Dans cette tâche, vous allez exécuter le package Lesson 3.dtsx. Lors de l'exécution du package, la fenêtre Journaux d'événements répertorie les entrées inscrites dans le fichier journal. Une fois l'exécution du package terminée, vous allez vérifier le contenu du fichier journal qui a été généré par le fournisseur d'informations.  
  
## Vérification de la disposition du package  
Avant de tester le package, vous devez vérifier que le flux de contrôle et le flux de données dans le package de la leçon 3 contiennent les objets affichés dans les diagrammes suivants. Le flux de contrôle doit être identique au flux de contrôle de la leçon 2. Le flux de données doit être identique au flux de données des leçons 1 et 2.  
  
**Flux de contrôle**  
  
![Control flow in package](../integration-services/media/task4lesson2control.gif "Control flow in package")  
  
**Flux de données**  
  
![Data flow in package](../integration-services/media/task9lesson1data.gif "Data flow in package")  
  
### Pour exécuter le package du didacticiel Lesson 4  
  
1.  Dans le menu SSIS, cliquez sur Journaux d'événements.  
  
2.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
3.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
### Pour examiner le fichier journal généré  
  
-   Utilisez le Bloc-notes ou un autre éditeur de texte et ouvrez le fichier TutorialLog.log.  
  
-   Bien que la signification des informations générées pour les événements **PipelineExecutionPlan** et **PipelineExecutionTrees** ne soit pas abordée dans le cadre de ce didacticiel, vous pouvez voir que la première ligne mentionne les champs d'informations spécifiés sous l'onglet **Détails** de la boîte de dialogue **Configurer les journaux SSIS** . De plus, vous pouvez vérifier que les deux événements sélectionnés, PipelineExecutionPlan et PipelineExecutionTrees, ont été enregistrés pour chaque itération de la boucle Foreach.  
  
## Leçon suivante  
[Leçon 4 : Ajouter une redirection de flux d’erreurs avec SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  
