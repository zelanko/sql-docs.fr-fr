---
title: 'Tâche 15 : Générer et exécuter le projet SSIS | Documents Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9a63fcf03591626d5b4c1351d5ce868ef7a9fb65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045274"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>Tâche 15 : Générer et exécuter le projet SSIS
  Dans cette tâche, vous allez générer et exécuter le projet SSIS. Si vous avez la version 64 bits d’Excel 2010 est installé sur votre ordinateur, vous devez définir la valeur de **Run64BitRuntime** à **False** pour la source Excel fonctionne.  
  
1.  Dans le **l’Explorateur de solutions** fenêtre, cliquez sur **projet** dans le menu, cliquez sur **propriétés de CleanseAndCurateSuppliers**.  
  
2.  Dans le **propriétés** boîte de dialogue, développez **propriétés de Configuration** sur la gauche, puis cliquez sur **débogage**.  
  
3.  Définissez **Run64BitRuntime** à **False**.  
  
     ![Propriétés du projet CleanseAndCurateSuppliers](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "propriétés du projet CleanseAndCurateSuppliers")  
  
4.  Cliquez sur **OK** pour fermer la **propriétés** boîte de dialogue.  
  
5.  Cliquez sur **générer** sur la barre de menus, cliquez sur **générer CleanseAndCurateSuppliers**. Vérifiez l'absence d'erreurs de génération.  
  
6.  Cliquez sur **déboguer** sur la barre de menus et cliquez sur **démarrer le débogage**.  
  
7.  Passez en revue les messages dans la **progression** fenêtre et vérifiez que le package exécuté et s’est terminée correctement.  
  
     ![Résultant de la fenêtre de progression](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "résultant de la fenêtre en cours")  
  
     ![État final de la fenêtre de progression](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "état Final de la fenêtre en cours")  
  
8.  Cliquez sur **déboguer** sur la barre de menus, cliquez sur **arrêter le débogage** pour arrêter la session de débogage. Si le package échoue, vous devez activer les visionneuses de données pour voir comment les données circulent entre les composants.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 16 : Vérification avec Master Data Manager](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  